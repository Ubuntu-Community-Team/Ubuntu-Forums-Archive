---
title: "Linux newb having driver issues"
date: 2009-01-19
forum: General Help
---

### Post by Vtuser on 2009-01-19
Hello,
  I'm new to linux and am enjoying it except I can't seem to get my video drivers to work.  I have two xfx 7600gt cards in sli.  I currently have 8.10 installed.  When I try and install the drivers and reboot the gui will not start.  I have tried x config and others commands I have seen posted and the computer has spit out some useful info I'm sure. How do I copy it so other may be able to assist me??? Any help would be greatly appreciated.

---

### Post by Vtuser on 2009-01-19
I have gotten it to spit out errno 111, errno 3, fatal error no screens found.  Trys to start gui in two resolutions. Startx won't start gui.

---

### Post by Vtuser on 2009-01-19
it seems like gnome is running because when I ctrl alt delete it says stopping display manager

---

### Post by theWrkncacnter on 2009-01-19
Seems like a tricky problem. One way you can post output from the terminal if you're connected to thie internet is by using the pastebinit command (sudo apt-get install pastebinit). Alternatively you can save the output of any command by adding " > filename.txt" to the end of the line, such as "glxinfo > ~/glxinfo.txt"

---

### Post by Vtuser on 2009-01-19
at this point I'd just like to get back into the gui so I could trouble shoot this with the help of you guys.  I'm using my other computer right now

---

### Post by Vtuser on 2009-01-19
I tried recovery mode but end up back at the console.  I don't need to have the internet cable plugged in for resetting the xserver do I?

---

### Post by Vtuser on 2009-01-19
gedit say 6176 GTK-warning **: cannot open display

---

### Post by Vtuser on 2009-01-19
tried sudo update-initramfs -uk all no luck

---

### Post by theWrkncacnter on 2009-01-19
When I was running into display problems with my nvidia card, I got the gui back mostly by luck, but there are things that make it easier.

First, could you post the contents of /var/log/Xorg.0.log ? This will give us a better idea of what Xorg is trying to do when it starts up.

Do you have a Ubuntu Live CD? It'll be the most surefire way to boot into a GUI.

---

