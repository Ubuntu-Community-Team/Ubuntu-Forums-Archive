---
title: "Desktop freezes and tty login password incorrect"
date: 2013-03-30
forum: Desktop Environments
---

### Post by patriq on 2013-03-30
Good day, 
I have a recurring issue with my system I hope you can assist me with

To  begin, I have Ubuntu 12.04lts (64bit) loaded on a HP compaq-6715s laptop  and all too often the desktop freezes. I can move the mouse, but nothing  responds on the screen or the keyboard. If I have a movie or music  running, it'll continue, but the desktop remains frozen. Sometimes it  freezes when I have nothing but a folder window open and sometimes I can  have several programs running at once and yet, eventually, it'll  freeze. In the end all I can do is force shut down and reboot 

I have consulted various forums to troubleshoot this, yet nothing works to date
Accessing the terminal doesn't not work
I can not switch desktops to force quit a program

I  can go to the tty environment using ctrl/alt/+an f-key, but no matter  what I type, the system will ask me for my password, which is always refused
I have only one  login password and there are no special characters, numbers or capitols, its  just a simple 8 letter word in lower case and every time I type my  password the system always responds with 'incorrect login'

I have  tried typing my password in the command line to ensure the keyboard is  correct and it is

To recap I have 2 issues;
1. My computer freezes too often and I must force quit
2. The tty environment does not recognize my password and I must force quit

I  am new to ubuntu so I hope my description was adequate to help you  recognize the issue, however please feel welcome to request any other  details if required. 

Thank you for your assistance,
patriq

---

### Post by r.stiltskin on 2013-03-31
Sorry if this is a dumb question, but are you sure that you're entering the username correctly?  To be certain, open a terminal window (xterm, gnome terminal, etc.) and type
```
whoami
```Make sure you're entering your username exactly as it appears there.

If that doesn't solve the login problem, you can (at the tty **login** prompt) type your **password** (instead of username) to see how the characters show up there (in case there's a problem with the keymap configuration).

Regarding the desktop freezing, that sounds like a driver issue.  Not sure I can help much with that.  Maybe you can find something helpful on this wiki page: [https://wiki.ubuntu.com/LaptopTestingTeam/Old/HPCompaq6715s]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/HPCompaq6715s").  I'm not familiar with that laptop but if it's a "not very powerful" machine, maybe you'll have better results with Xubuntu.  (I prefer it even on fast hardware.)

Also, you might want to try installing the i386 (32 bit) version instead of the 64 bit.

---

