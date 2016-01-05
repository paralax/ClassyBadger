# ClassyBadger
simple "oops" util to fix the previous shell command

# what

years ago i saw my dad working in a terminal and i could have sworn i typed "oops <something>" when he made a typo and it worked: the command was fixed and rerun, he didn't need to retype the whole thing. i always wanted the oops command.

however, it didn't exist, or at least as i knew it. so i wrote a portable version of it (it seems it exists in zsh, a shell i just don't use). the python part of it is really simple, just a Levenshtein distance calculator and a replacement engine. 

# usage

you need to create a command alias for it however:

ksh, sh, bash:

    $ alias oops='history>/tmp/oops_history && ~/bin/oops.py'

csh and derivatives:

    % alias oops 'history > /tmp/oops_history && ~/bin/oops.py'

here's a brief example of it in action:

    $ emacss ~/bin/oops.py
    ksh: emacss: not found
    $ oops emacs
    [ emacs opens and voila, working ... ]

i make a lot of typos and rather than cutting, pasting, fixing the line this makes it easier. some bugs and limitations:

- i need to make it use the damerau distance, which is better for spelling errors)
- not extensively field tested at all
- it doesn't leave a corrected mark in your history file
- it doesn't work for shell built-ins (e.g. cd)

