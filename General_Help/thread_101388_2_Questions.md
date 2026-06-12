---
title: "2 Questions"
date: 2005-12-09
forum: General Help
---

### Post by TudorB on 2005-12-09
Hi, I`m new to linux but very fond of the Ubuntu Distro. 
I`ve installed Kubuntu Breezy and I have 2 questions about it:
1. how to I upgrade to the latest version of the Firefox browser
2. can anyone recommend a good (and easy to install) ftp client?

Thank you

---

### Post by korkow on 2005-12-09
As for firefox, I reccomend the easiest way to do this is by "sudo adept" on the command line. Adept is basically a nice graphical version of apt-get. Then either update all your packages by clicking "Full upgrade at the top" (I recommend this), or putting "firefox" into the search thing to just update that.

---

### Post by Adrian on 2005-12-09
[QUOTE=TudorB]
2. can anyone recommend a good (and easy to install) ftp client?
[/QUOTE]

Well, actually Konqueror is a capable FTP client.

If you don't mind installing a GTK program, gFTP is very popular and it's easy to use. I haven't tried kBear myself, but it seems to be nice too.

---

### Post by GoldBuggie on 2005-12-09
>  1. how to I upgrade to the latest version of the Firefox browser

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by veloct on 2005-12-10
I've been using kbear without a problem. gftp is great also

---

### Post by TudorB on 2005-12-10
I`ve installed Firefox and the FireFTP plugin, and it works great! So everything is fixed. But there are 3 more questions (no need for extra topic, I guess)

1. how do I play mp3 files and other media. Amarok keeps telling me that it can`t play mp3`s. Juk doesn`t work either. Are there any libraries I should install? 

2. how do I customize the bootloader (GRUB) to display a cooler meniu (with graphics, etc.)

3. how do I change the display resolution for the Kubuntu Login screen? I`ve changed it in KDE and the KDE setting do not apply to the login screen. With kind of makes sense, because the login screen displays before KDE loads.

Thank you

---

### Post by veloct on 2005-12-10
[QUOTE=TudorB]I`ve installed Firefox and the FireFTP plugin, and it works great! So everything is fixed. But there are 3 more questions (no need for extra topic, I guess)

1. how do I play mp3 files and other media. Amarok keeps telling me that it can`t play mp3`s. Juk doesn`t work either. Are there any libraries I should install? 

2. how do I customize the bootloader (GRUB) to display a cooler meniu (with graphics, etc.)

3. how do I change the display resolution for the Kubuntu Login screen? I`ve changed it in KDE and the KDE setting do not apply to the login screen. With kind of makes sense, because the login screen displays before KDE loads.

Thank you[/QUOTE]

1. you'll need to load an engine for amarok to play mp3's. 
*sudo apt-get install amarok-gstreamer*
Then open amarok, go to settings -> configure amarok -> engine and select gstreamer engine. apply

2. GRUB has splashimages that you can use.  Kde-look.org has more you can download.  To apply them you have to use your favorite editor to edit /boot/grub/menu.lst (must edit as root) and then add a line like this before the entries for the different kernel entries:
*splashimage=(hd0,1)/boot/grub/splashimages/<filename>.xpm.gz*
*(hd0,1) is where my linux partition is so make sure that you enter the right info here. 

3. not sure. 

you can read the GRUB man pages to get more clarification if you need it.  I believe there is a grubconf program but I'm not sure if it's apt-getable, grubconf is a gui way to edit grub

---

### Post by TudorB on 2005-12-10
It still doesn`t work. I get the following error message on amaroK
> 
The gst-engine claims it cannot play MP3 files.
You may want to choose a different engine from the Configure Dialog, or examine the installation of the multimedia-framework that the current engine uses.


---

### Post by TudorB on 2005-12-10
XMMS on the other hand works, but it has some "blackout`s"

---

### Post by Knomefan on 2005-12-10
1. Enable the multiverse repositoris:
Open a terminal and edit your /etc/apt/sources.list:
sudo nano -w /etc/apt/sources.list
now remove the leadin # from the lines for the universe and multiverse repositories. They now should look something like this:
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe multiverse
Now save the changes (Ctrl+O) and exit the editor (Ctrl+X)

2. Install gstreamer-plugins-multiverse:
Refresh you package database: sudo apt-get update
Then install gstreamer-plugins-multiverse:
sudo apt-get install gstreamer0.8-plugins-multiverse

3. Have fun!

---

### Post by TudorB on 2005-12-11
It works now...thanks!!!

---

