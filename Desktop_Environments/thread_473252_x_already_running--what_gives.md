---
title: "x already running--what gives?"
date: 2007-06-13
forum: Desktop Environments
---

### Post by dominator22 on 2007-06-13
i tried to launch an x session (using srartx) on tty6 when I got a can't start x message because it's already running on :0 --what is this BS?

i want multiple instances of x

---

### Post by trippinnik on 2007-06-14
I did a quick google search and found the answer to your problem:
Hello,
I have tried to run multiple X servers with only one card and one monitor. Is this possible, or is it normal that the second X server does not run? I used startx display :0 the first time, and :1 the second. I have a 1024K video board (#9GXE64 PCI, S3 864), and normal config is 8 bpp, 1024*768 virtual desktop, running on a remix of RedHat 4.0, 4.1 and 4.2, with XFree86 as server. Maybe I did not understand the man page (English is not my first languaje). Any suggestion?

The normal way this is done is using the form:

	startx -- :0 &
		startx -- :1 &

... The -- is used by startx and xinit to separate an optional set of client parameters from the set of display/server options and parameters.

If you ran the command:

	startx xterm -e myprog -- :1 &

... it would start X Windows with a copy of xterm which would be running 'myprog' (whatever that might be). The remainder of the line informs the X server to use display number one (which would be VC -- virtual console -- number eight on most Linux systems).

(On my systems it would start on VC#14 -- accessed with the {Right Alt}+{F2} key combination. I routinely configure mine with 24 VC's -- the first twelve of which have "getty's" (login prompts) and the next eleven of which are available for X (xdm's or otherwise), using 'open' commands, or for dumping status output from a process (like 'make' or 'tail -f').

Read the man pages for startx and xinit one more time. I'm pretty sure that the man pages have all been translated into Spanish -- so you might want to hunt those down.

Thanks!!!

Read the man pages for startx and xinit one more time.

---

