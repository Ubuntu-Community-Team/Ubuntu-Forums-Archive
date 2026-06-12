---
title: "Global Menu Applet problems"
date: 2009-01-15
forum: General Help
---

### Post by danelectro15 on 2009-01-15
Hello,

I'm relatively new to linux and ubuntu so forgive me if I use the wrong terms. I was trying to theme my ubuntu to look like a mac and I downloaded an applet called the "Global Menu Applet". I used these commands to do so.

cd Mac_files
wget [http://gnome2-globalmenu.googlecode....-svn964.tar.gz](http://gnome2-globalmenu.googlecode....-svn964.tar.gz)
tar zxvf gnome-globalmenu-0.4-svn964.tar.gz
cd globalmenu
sudo dpkg -i *.deb

Ever since then I received the message "The panel encountered a problem while loading "OAFIID: GNOME_MixerApplet" when trying to add applets to my panel.

And now when I try to restart my computer the Ubuntu loads but it never gets to the login screen I just get a swirling loading mouse icon. I have let it try to load over night and It was still in the same spot in the morning


Thanks for any and all help!

---

### Post by cariboo on 2009-01-15
I looks like your problem has nothing to do with the files you downloaded, it looks more like a problem with your video adapter. Restart in recovery mode and select xfix to restore your /etc/X11/xorg.conf to the default setting, then select resume. THis should get your desktop back to where you can diagnose your other problems.

Jim

---

### Post by danelectro15 on 2009-01-15
Thanks for the reply,

I tried xfix but I got this message 

Xserver-xorg postinst warning:overwriting possibly-customized configuration file; in /etc/x11/xorg.conf20090115171000

Then it quickly brings me back to the recovery mode screen

do I have to restore the file manually?

I tried deleting the file as I was informed that it would regenerate itself with default settings using the command-

sudo rm /etc/X11/xorg.conf

But it says no such file or directory

---

### Post by danelectro15 on 2009-01-15
Anyone?

---

### Post by theApokalypsis on 2009-01-17
> **danelectro15 said:**
> Thanks for the reply,

I tried xfix but I got this message 

Xserver-xorg postinst warning:overwriting possibly-customized configuration file; in /etc/x11/xorg.conf20090115171000





Dont delete the file. just run xfix like you did, then continue your boot and x should be up and running.

---

