---
title: "How do I set this up?"
date: 2006-02-08
forum: Desktop Environments
---

### Post by ardchoille on 2006-02-08
I am running an experiment to see just how much I can do on a computer without running X. I have been able to do the following:

1. IRC with irssi
2. surf the internet with elinks
3. send/receive email (gmail) with elinks
4. file browsing and manipulation with bash and Midnight Commander

I run all of these apps in screen. Someone told me that framebuffer in a tty will enable me to watch DVD's with MPlayer/Xine, which makes me wonder why I even need X.

My question is: How do I install and set up framebuffer? I have seen that "links2 -g" can enable the user to view .png/.gif/.jpeg/.xpm files with framebuffer in a tty - I saw this while booted into the [System Rescue CD]("http://www.sysresccd.org/").

Anyone have any ideas on how to install and set up framebuffer?

---

### Post by dcstar on 2006-02-09
[QUOTE=ardchoille]
.......
My question is: How do I install and set up framebuffer? I have seen that "links2 -g" can enable the user to view .png/.gif/.jpeg/.xpm files with framebuffer in a tty - I saw this while booted into the [System Rescue CD]("http://www.sysresccd.org/").

Anyone have any ideas on how to install and set up framebuffer?[/QUOTE]
Using framebuffer starts with a "vga=xxx" kernel boot parameter, and fbset is in the repositories.

---

