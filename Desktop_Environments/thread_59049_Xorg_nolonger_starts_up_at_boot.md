---
title: "Xorg nolonger starts up at boot"
date: 2005-08-22
forum: Desktop Environments
---

### Post by shooterae5 on 2005-08-22
After my last system up Xorg will no longer start at boot. I have to login at a text screen and then manually start X (startx). this puts me in to the default Gnome desktop. I can work from here just fine, but when I'm at work I like to use blackbox, I use Gmone for personal things at home. 

My question is how can I get the graphic login back, so I can switch back and forth more easily?

Thanks 

Dale

---

### Post by KingBahamut on 2005-08-22
What did you change to cause this to happen? 

Could always try dpkg-reconfigure xserver-xorg , and reset your xorg configuration and see if that will work.

---

### Post by shooterae5 on 2005-08-22
[QUOTE=KingBahamut]What did you change to cause this to happen? 

Could always try dpkg-reconfigure xserver-xorg , and reset your xorg configuration and see if that will work.[/QUOTE]



I have tried that (sudo dpkg-reconfigure xserver-xorg) and it did not fix the autostart of an x session. I think that something in the boot script got changed when I did a system update over the weekend. I'm not sure where to look for the boot script or what to look for once I find it. X runs fine after manauly starting it. So the x config file shouldn't be the problem. 

Thanks for the quick responce...

Dale

---

### Post by KingBahamut on 2005-08-22
Could try to uninstall and reinstall gdm. 

apt-get remove gdm , apt-get install gdm.

---

### Post by shooterae5 on 2005-08-22
That fixed it... \\:D/ 
Now that I know what controls the graphic loging   (GDM) I'll read the man page to learn the rest of what I'd like to know. (and hopefully a more)
thanks for the quick help. I love the way you Linux guys step up and help...
As I learn more I'll be sure to help out other newbies. :razz: 

Dale

---

