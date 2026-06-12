---
title: "howto get Whiskermenu after upgrade 13.10 to 14.04"
date: 2014-05-15
forum: Desktop Environments
---

### Post by frank-wagner-p on 2014-05-15
Hi,  
started with ubuntu, then migrate to xubuntu Latest release 13.10, today i migrate to 14.04 
seems all okay, but I still have old menu (with a lot of missing icons :() 
I noticed that while migration ppa for xfce was disabled ([http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu](http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu)) 
I reenabled it, but still old start menu  

how can I get Whiskermenu running?  

found anywhere this command: apt-cache policy xfdesktop4
xfdesktop4:
  Installiert:           4.11.6-1ubuntu1
  Installationskandidat: 4.11.6-1ubuntu1
  Versionstabelle:
 *** 4.11.6-1ubuntu1 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
        100 /var/lib/dpkg/status

apt-cache policy xfce4
xfce4:
  Installiert:           4.10.1
  Installationskandidat: 4.10.1
  Versionstabelle:
 *** 4.10.1 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
        100 /var/lib/dpkg/status



maybe it's wrong to use ppa? or this one? what have I to change to get the latest xfce-desktop?

thanks in advance for any hint and tips 

       Frank

---

### Post by Toz on 2014-05-15
Hello and welcome to the forums.

To use the whiskermenu, make sure that xfce4-whiskermenu-plugin is installed and then add it to your panel via the Panel's "Add Items" procedure.

The PPA is not required for 14.04 as the latest version of Xfce is included in 14.04. Besides, the PPA won't work in 14.04.

---

### Post by frank-wagner-p on 2014-05-15
Hi,

thanks for your tip :)
so easy :KS:KS

still a small problem
a lot of icons are missing, is there an easy way to restore all icons ?

---

### Post by Toz on 2014-05-15
> still a small problem
a lot of icons are missing, is there an easy way to restore all icons ? 
Which icon theme are you using? 
Have you tried changing the theme (Settings Manager >> Appearance >> Icons)?
Any chance you can post a screenshot?

---

### Post by frank-wagner-p on 2014-05-15
Hey man,

you are great =d>=d>
this was the trick, migrations seems to lost theme and icons settings.
After choosing a new one all icons are back again :D

thank you very much :popcorn:

---

