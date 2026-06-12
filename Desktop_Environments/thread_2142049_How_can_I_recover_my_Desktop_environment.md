---
title: "How can I recover my Desktop environment?"
date: 2013-05-04
forum: Desktop Environments
---

### Post by insignia92 on 2013-05-04
Good evening Everyone, I am having problems recovering my desktop.


Before it came to this desktop without the taskbar at the top, and the sidebar. Also the title bar for applications are gone.


What happened is I tried to installed my NVIDIA driver without using the AdditionalDrivers application, but using the terminal.


1. I downloaded the installer for my NVIDIA driver
2. Followed the instructions, which was first to disable the X server, I did it by changing the run-level.
```
vim /etc/init/rc-sysinit.conf
changed the value of "env DEFAULT_RUNLEVEL = 2" to 3
```
3. Next was I disable the Nouveau Driver by adding this lines.
```
 blacklist nouveau
options nouveau modeset=0
 to the following file:
 /etc/modprobe.d/blacklist.conf using vim
```


After that everything went wrong, my desktop did not went the way  things I thought it would be so, I decided to uninstall the driver and undo the changes I did.. and this happened..


The reason why I tried to install the driver: because my systems keeps on saying my graphics driver is not well configured that I had to run on low graphics mode for one session even if it won't be just once. and also it keeps giving errors that my graphics is not well installed. hmp..


Before everything else, my desktop was fine. I was looking for some ways to reset the default desktop unity which was
```
unity reset 
```


but it gives out an error that the reset command was already deprecated and so I came to my last resort on posting a question in this forum so I can find a solution on how to fix my desktop environment.


I'm using the Ubuntu 12.10 Desktop version btw.


I can't run the `unity` command in the terminal. It gives out errors that the process is not found and all the things that it is loading goes for an error and nothing.


If definitely by chance I get things done and found the solution, I'll post it.


[IMG]http://i.stack.imgur.com/tS0IO.png[/IMG]

---

### Post by bogan on 2013-05-04
Hi!, **insignia92**,

Can you get to a Terminal or TTY, 'Crtl+Alt+F1'?

Please Post: ```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Have you tried  logging in to the Guest Account, or creating a second Administration account and seeing if it is the same.

In 12.10 the most common cause of similar problems is that the correct linux-headers have not been loaded.```
Sudo apt-get install linux-headers-generic linux-headers-(uname -r) # insert output of uname -r, no brackets
```

If they are installed, not reported as already the correct version, then remove --purge any installed driver by name  and reinstall the one you want.

Chao!, **bogan.**

---

