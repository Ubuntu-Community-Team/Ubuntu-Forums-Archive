---
title: "How to change root's prompt colors"
date: 2005-12-27
forum: General Help
---

### Post by ShirishAg75 on 2005-12-27
Hi all,
 I've been playing around with the .bashrc which is there both as normal user (/home/username/.bashrc) as well as root (/root/.bashrc). This is the way the default entry is in .bashrc which I'm using :-

     
     
```
[LEFT]PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac[/LEFT]
    
```  While looking for where the color schemes code are listed came to /usr/lib/X11/rgb.txt which lists the all the colors to the corresponding code while this in a different format. My main motive is to change 
     
```
[LEFT]PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"' [/LEFT]
    
``` the prompt colors. How can I do this? Thanx in advance

---

### Post by jliedeka on 2005-12-27
You can get the color codes from running "dircolors -p".  The escape codes are about 1/3 down into the output.

---

