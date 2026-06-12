---
title: "Lxterminal question"
date: 2014-03-02
forum: Desktop Environments
---

### Post by marc11 on 2014-03-02
[INDENT]                     First off I am new to Linux, so please forgive me if this should be obvious. I've searched all over here and the web in general and I have not found any definitive answers. I am writing some scripts  for launching a program called HDSentinel. I am having to create  different scripts for different DE's/emulators as there is no set  standard. My problem is that I can find no way to hold lxterminal open  after the command has executed. Gnome-terminal lets me create a profile  that holds the emulator window open. Xterm lets me use -hold to keep the  terminal window open. But lxterminal does not seem to have any  mechanism for doing this. Is there something I am missing? Or is there  some work around for this, other than just using xterm?                 
[/INDENT]

---

### Post by vasa1 on 2014-03-03
Does your lxterminal close after running this script?

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

T='gYw'   # The test text

echo -e "\n                 40m     41m     42m     43m\
     44m     45m     46m     47m";

for FGs in '    m' '   1m' '  30m' '1;30m' '  31m' '1;31m' '  32m' \
           '1;32m' '  33m' '1;33m' '  34m' '1;34m' '  35m' '1;35m' \
           '  36m' '1;36m' '  37m' '1;37m';
  do FG=${FGs// /}
  echo -en " $FGs \033[$FG  $T  "
  for BG in 40m 41m 42m 43m 44m 45m 46m 47m;
    do echo -en "$EINS \033[$FG\033[$BG  $T  \033[0m";
  done
  echo;
done
echo
```

Mine remains open.

---

### Post by marc11 on 2014-03-03
Maybe I'm missing something, lord knows this is a learning experience  for me, but from what I can see, your script doesn't call its own  terminal window. What I want is to     call a terminal window from within the script, execute a command in     that terminal window, and have the window stay open after that     command exits. And that's where the problem comes up. 
    
    With xterm and konsole for example I can call the terminal with the     -hold option,  like this: 
    xterm -hold -e "sudo  ./xyz " 
or
konsole -hold -e sudo ./xyz
and the termnal window will remain open after the command xyz exits.     
    Xfce4-terminal has the equivalent -H option. But lxterminal has no     equivalent option. 
    
    Gnome-terminal and mate-terminal let me create a profile that will hold the terminal     open after the command exits, and call that profile, like this: 
    gnome-terminal --window-with-profile=HoldOpen -e " ./xyz " 
or
mate-terminal --window-with-profile=HoldOpen -e " ./xyz " 
    Lxterminal does not give me that feature either, as far as I can     tell.

---

### Post by vasa1 on 2014-03-03
> **marc11 said:**
> Maybe I'm missing something, lord knows this is a learning experience  for me, but from what I can see, your script doesn't call its own  terminal window. ...
Lxterminal does not give me that feature either, as far as I can tell.
Your requirement of opening a terminal from within the script wasn't clear to me. Sorry for the confusion.

Functions available elsewhere may not be included in lxterminal because the particular usage may not have occurred to the dev. Also, lxterminal is supposed to be "lightweight" and so one may expect to see fewer features in it (and in most other LXDE software).

---

### Post by marc11 on 2014-03-03
No need to apologize, I obviously wasn't clear on that. 

I had sort of come to that same conclusion, that it just isn't an option with lxterminal. Would be a nice feature. Anyway, most distros do come with xterm and I do have scripts for it, so folks can use them. Or they can install some other emulator that I have created scripts for. And of course folks can always "roll their own" scripts, which is what's so interesting about Linux (says the 20+ year Windows user/soon to be ex-user I think).

Anyway, thanks for the quick responses.

---

