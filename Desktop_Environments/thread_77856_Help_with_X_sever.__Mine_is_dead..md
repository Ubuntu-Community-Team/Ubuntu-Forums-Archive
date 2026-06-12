---
title: "Help with X sever.  Mine is dead."
date: 2005-10-17
forum: Desktop Environments
---

### Post by joplass on 2005-10-17
Guys,
I updated with apt-get update and apt-get dist-upgrade.  I lost the X server in the process.  When the box starts it goes through all the check up but instead of it going to X server it gives me the option to “login” for a brief moment then I get a blue screen.  The blue screen gives the option to setup the X server with “yes” highlighted.  But when I press “Enter” on the keyboard nothing happens.  The machine seems frozen at this stage because I can not even move to highlight “no” and like I mentioned above, pressing “Enter” on the keyboard doesn’t do anything.

I will appreciate some help.

Thank you,

---

### Post by KingBahamut on 2005-10-17
Hardware configuration? Video hardware? 

Most likely what you could do is change the xorg driver in xorg.conf to "vesa" and actually get X running, and then go from there, but it sounds like a video card issue, right off.

---

### Post by joplass on 2005-10-17
[QUOTE=KingBahamut]Hardware configuration? Video hardware? 

Most likely what you could do is change the xorg driver in xorg.conf /QUOTE]

Could you tell me how to do this?

---

### Post by KingBahamut on 2005-10-17
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nano /etc/X11/xorg.conf 

find the video driver , change it from whatever it is to "vesa" , 

Ctrl X , Save as xorg.conf , then attempt to restart x via startx

---

### Post by Miguel on 2005-10-17
Don't forget that you can always fire a terminal (if the keyboard responds, that is) by pressing Ctrl+Alt+F1

If not, don't despair. You can either use the installation disc in rescue mode (a bit difficult) or you can also use a Live CD  (this way you also check if your hardware is still OK). Note that with the ubuntu Live-CD you will need to mount manually your HD.

Hope is the last thing to lose

---

### Post by zenodaddy on 2005-10-17
Honestly I would do the following. I had the same problem when I upgraded to the SR - 1 before the final release.

Log In --  (Of Course :))

Sudo apt-get update
Sudo apt-get upgrade

then this will tell you which packages has dependency problems. From there just write them down and sudo apt-get whatever. You may also have to fix the package by using sudo apt-get -f install (I think that is right), once you do these steps a few times it should resolve the issue. I don't think it is a video card issue but just an install problem. I ran into all kinds of problems doing the dis-upgrade. I recommend burning the ISO to a CD and doing a clean install.

---

### Post by joplass on 2005-10-18
I went with a clean install.  So, upgrading the system still does not work.

---

