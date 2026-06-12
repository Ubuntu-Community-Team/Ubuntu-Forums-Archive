---
title: "colors in xterm and virtual term"
date: 2008-01-03
forum: Desktop Effects &amp; Customization
---

### Post by naugiedoggie on 2008-01-03
Hello,

I use mutt for my mail client.  I find that the color "yellow" is either not defined or it is misdefined in some way on ubuntu.  It appears as black in a virtual terminal window but as normal yellow in an xterm.

Is there a way for me to fix this?

I normally use screen, but that is not the problem, as the color issue appears in both screen and a plain terminal.

Bad color definition:

powem@ellen:~$ env | grep TERM
TERM=screen
TERMCAP=SC|screen|VT 100/ANSI X3.64 virtual terminal:\

or

powem@ellen:~$ env | grep TERM
TERM=linux

Good color definition:

(Linux 2.6.22-14-generic~ellen) [powem] [  ~] 
 503 $ --> env | grep TERM
TERM=xterm
COLORTERM=gnome-terminal

Thanks for any help.

mp

---

