---
title: "name@box in a different color in the terminal?"
date: 2007-05-01
forum: Desktop Environments
---

### Post by winter_mute on 2007-05-01
On various other linux distributions I've had the name in the terminal being green or some other color - by name I mean login@box ~ - and I can't seem to get that working in Ubuntu.  Is there some way to get that set up?  It's a nice feature to have when going through huge outputs in the terminal, and I'd like to have that back.

---

### Post by amohanty on 2007-05-01
An example:
Put in your ~/.bashrc file

```

no_color='\[\033[0m\]'       
black='\[\033[0;30m\]'
blue='\[\033[0;34m\]'
red='\[\033[0;31m\]'

PROMPT="${blue}\u@\h ${red}\w ${no_color} $"

```
will give you a blue username@host followed by a red current dir and a defautl color '$'

To get those number I copied a script of tldp:

```

#!/bin/bash
#
#   This file echoes a bunch of color codes to the 
#   terminal to demonstrate what's available.  Each 
#   line is the color code of one forground color,
#   out of 17 (default + 16 escapes), followed by a 
#   test use of that color on all nine background 
#   colors (default + 8 escapes).
#
# src: http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html

T='gYw'   # The test text

echo -e "\n 40m     41m     42m     43m     44m     45m     46m     47m";

for FGs in '    m' '   1m' '  30m' '1;30m' '  31m' '1;31m' \
           '  32m' '1;32m' '  33m' '1;33m' '  34m' '1;34m' \
           '  35m' '1;35m' '  36m' '1;36m' '  37m' '1;37m'; 
  do FG=${FGs// /}
  echo -en " $FGs \033[$FG  $T  "
  for BG in 40m 41m 42m 43m 44m 45m 46m 47m; do 
    echo -en "$EINS \033[$FG\033[$BG  $T  \033[0m";
  done
  echo
done
echo

```

This is a good guide:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

HTH
AM

---

### Post by winter_mute on 2007-05-01
Thank you!

---

### Post by x1a4 on 2007-05-01
Hi,

Here's how I have it set-up: 

TCSH
set prompt='%{**^[**[01;33m%}[tcsh]%{**^[**[01;34m%}%c02/%{**^[**[01;33m%}%%%{**^[**[00m%} '

ZSH
PROMPT='%{**^[**[01;33m%}[zsh]%{**^[**[01;34m%}%2~/%{**^[**[01;33m%}%%%{**^[**[00m%} '

BASH
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;33m\][bash]\[\033[00m\]\[\033[01;34m\]\w/\[\033[00m\]\[\033[01;33m\]%\[\033[00m\] '

All of these will print the shell name between brackets in bold yellow, then the current path in bold blue, then % in bold yellow.  

**^[** is generated using Ctrl+V then Esc

The various colour values are: 

restore    = 00       eg:  %{**^[**[00m%}
black       = 00;30  eg:  %{**^[**[00;30m%}
firebrick  = 00;31  eg:  %{**^[**[00;31m%
red          = 01;31  eg:  %{**^[**[01;31m%}
forest      = 00;32  eg:  %{**^[**[00;32m%}
green       = 01;32  eg: %{**^[**[01;32m%}
brown      = 00;33  eg:  %{**^[**[00;33m%}
yellow      = 01;33  eg: %{**^[**[01;33m%}
navy        = 00;34  eg  %{**^[**[00;34m%}
blue         = 01;34  eg:  %{**^[**[01;34m%}
purple      = 00;35  eg:  %{**^[**[00;35m%}
magenta   = 01;35  eg:  %{**^[**[01;35m%}
cadet       = 00;36  eg:  %{**^[**[00;36m%}
cyan        = 01;36  eg:  %{**^[**[01;36m%}
gray         = 01;36  eg:  %{**^[**[00;37m%}
white       = 01;37  eg:  %{**^[**[01;37m%}

---

