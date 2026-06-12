---
title: "help my video card driver is messed up"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by bribaetz on 2007-10-26
okay so i install all the stuff for the advanced settings but i messed up my card driver when i messed with it to see if any of them would work because i hadn't read all the threads so my comp is fine at this piont its a little crapy with the video. my card environment thingy will have a blank at the top of the window bar where you move it or close it. so i just disable it and i messed with my driver some more and i also mess with my screen settings size etc. now every time i try to log in it takes me back to the log in screen unless i use the failsafe_gnome thing with out using any extra scripts which would be okay if my mouses left click and right click weren't backwards. by the way my video card is "ATI rage 128" how might i fix this problem.

---

### Post by bribaetz on 2007-10-26
any ideas

---

### Post by bribaetz on 2007-10-26
please

---

### Post by MaximusTG on 2007-10-26
Well you could try to login failsafe, or at least get to a terminal,

then type:

sudo dpkg-reconfigure xserver-xorg

That should reconfigure your xserver to default settings. Now next you want to play with you setting s, backup your old config, just in case

type:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

and to reverse

sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

---

### Post by bribaetz on 2007-10-26
i figure i will start from square one and  just reinstall  gusty all over

---

### Post by MaximusTG on 2007-10-26
You could do that, but why not give my suggestion a try? It's not very hard.. You could also boot the livecd, and copy the xorg.conf of the livecd to your current installation

---

### Post by bribaetz on 2007-10-26
okay and just for future reference i don't need to change my driver to get the xgl to work or visual effects to work.

---

### Post by bribaetz on 2007-10-26
where can i find a tutorial on the terminal

---

### Post by MaximusTG on 2007-10-26
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

That's a basic introduction to the terminal,

however, I don't think you actually can get compiz to run on your videocard..

---

### Post by bribaetz on 2007-10-26
is it not powerful enough?

---

### Post by MaximusTG on 2007-10-26
Well I just did a quick search, but it has something to do with square textures not being supported..
Your better off buying a budget nvidia card if you really want desktop effects.

---

