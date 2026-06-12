---
title: "Screen help and DVD help."
date: 2006-07-13
forum: Desktop Environments
---

### Post by Iorchova on 2006-07-13
I recently got Ubuntu Linux and got all the necessary updates, and I have a few question.

First, my screen is positioned a bit right, and some buttons get cut off.

Second. Is there a program that can play DVDs? I've wanted to watch movies for awhile but I can't find a proper program.

---

### Post by ScottMorris on 2006-07-13
What kind of monitor are you using?

As for DVDs install VideoLAN Client (VLC) [[http://www.videolan.org/vlc/]("http://www.videolan.org/vlc/")]  It can play DVDs right off the bat and works really well. :)

---

### Post by gratefultux on 2006-07-13
Ok, for the screen there should be some buttons on your monitor to fix the positioning.
For the dvd try totem-xine.  You will also need dvdlibcss2 in order to play protected dvd's.The Unofficial Ubuntu [Guide]("http://ubuntuguide.org/wiki/Dapper") has information on how to set this up.

---

### Post by ScottMorris on 2006-07-13
VLC requires no special decrypting libs as it uses its own built in ones.

---

### Post by Iorchova on 2006-07-13
I don't know much about my monitor but I'm using an LCD monitor with a max resolution of 1080.

---

### Post by gratefultux on 2006-07-13
I don't think the resolution is really the problem if only a little bit of the picture is cut off.  Look at the frame of your monitor, there should be buttons or wheels or something like that on it.  I know that for me i have 4 buttons.  Menu, +, -, and Exit.  I can hit the Menu button and a little menu pops up on the screen.  In this menu there's an icon that describes moving the screen.  I can go to that icon with the + button, hit menu again and then use the + and - button to move my screen left and right (or up and down whatever the case may be).

---

### Post by Iorchova on 2006-07-13
Okay, now I did what it told me to to install VLC, and it says my System Architecture is wrong when I try to check the box.

---

### Post by Iorchova on 2006-07-13
Okay, I fixed the screen, but I think I messed up the Ubuntu Linux Repositories.

---

### Post by Iorchova on 2006-07-13
"Cannot install 'wxvlc'

This application conflicts with other installed software. To install 'wxvlc' the conflicting software must be removed before.

Switch to advanced mode to resolve this conflict.

---

### Post by Iorchova on 2006-07-14
Will I have to reinstall ubuntu to solve t his error?

---

### Post by ScottMorris on 2006-07-16
Advanced mode is the Synaptic Package Manager, just open that and search for the program you are trying to install and it should tell you the conflicting program.  Then try removing it and reinstalling what your trying to install.

---

