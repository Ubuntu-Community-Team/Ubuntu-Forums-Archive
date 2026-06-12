---
title: "I don't know how to fix this problem..."
date: 2009-01-25
forum: General Help
---

### Post by faust7 on 2009-01-25
Hi guys!

I changed the resolution of my Ubuntu 8.10 to an unsupported resolution by my graphics card and now there is no way for me to change it back. I rebooted and logged in recovery mode without success. As soon as I get in Ubuntu, the resolution changes to the unsupported one and I lose the image. The gdm menu works fine though, it's passed it that the resolution changes.

Is there a way for me to change the resolution manually somewhere ?

If that can help I am in dual boot with Windows Vista and the partition for Ubuntu is ext3.

Any help would be more than appreciated !!!!!!! Don't tell me I have to reinstall everything after wasting so much bandwith to download all the upgrades!!!!

---

### Post by faust7 on 2009-01-25
Ok, actually I found out that through the recovery mode I can drop to root shell prompt... which is where I am now... so I guess I will try to find on the net how to change the resolution from the root menu.

(I am definitely not an expert with the terminal as it's my first week on Linux)

---

### Post by faust7 on 2009-01-25
Deleted by the author

---

### Post by faust7 on 2009-01-25
The latest attempt was editing /etc/X11/xorg.conf and I added in the Screen section 

```
SubSection "Display"
    Depth 16
    Modes "1024x768_75.00"
End SubSection
```

I logged in fine from GDM and then I lose the image again. It looks like my attempt was unsuccessful.

Help?

---

### Post by mb_webguy on 2009-01-25
[This thread]("http://ubuntuforums.org/showthread.php?t=83973") should be useful.  If that doesn't help, post back and I'm sure someone will help you figure it out.

---

### Post by faust7 on 2009-01-25
Thanks mb_webguy... This is the thread I have been reading in my attempt at fixing this problem...

I'm surprised because the default xserver settings should work just fine as it did when I first installed Ubuntu. I feel like there is something which I am not doing correctly. 

First I performed these in the following order


```
sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start
```

Then I rebooted and it didn't work (losing the image after gdm).

Then I tried :

```
sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm start
```

Same result.

Then I tried:

```
sudo /etc/init.d/gdm stop

sudo nano /etc/X11/xorg.conf 
```

and Added 

```
SubSection "Display"
Depth   16
Modes "1024x768_75.00"
EndSubSection 
``` restarted gdm and realized that it didn't change anything either.  

I am wondering how I can reset the Xserver or possibly the Gnome options in general... or simply fix that problem...

---

### Post by fooman on 2009-01-25
have you tried the "xfix" option in recovery mode?

---

### Post by faust7 on 2009-01-25
Yes I tried XFIX, then I resumed. I got to the logon menu which was working fine, then as soon as it starts loading, the image goes away. I can tell though that I am logged on because from time to time, the screen shows 1-1.5 second of the desktop but I don't have enough time to successfully go in the screen resolution menu to change things.....

---

### Post by faust7 on 2009-01-25
That's it for tonight...... Unfortunately, I am thinking that I might have to reinstall Ubuntu from scratch..... :(

---

### Post by mb_webguy on 2009-01-25
If you're getting that far, the problem is most likely somewhere in your user configuration files.  Boot into recovery mode, then drop into a command prompt.  Navigate to your home directory, back up everything (e.g. "mkdir backup; cp -r ./* backup/"), and then delete any configuration files that pertain to Gnome or Compiz (such as the .gconf/ and .config/compiz/ directories).  Then reboot and try logging in to your regular account.

---

### Post by irfan9727 on 2009-01-25
Maybe compiz problem? [http://ubuntuforums.org/showthread.php?t=990711](http://ubuntuforums.org/showthread.php?t=990711)
Try this: > I think there is an easier way to fix this...

ctrl+alt+f1

Code:

killall compiz.real

Code:

exit

navigate to your compiz settings as usual and turn off bicubic filtering...

reload compiz(you can just go to preferences>appearance and check "normal" on the visual effects tab)

viola!

---

### Post by faust7 on 2009-01-25
Finally resigned myself...... and formatted!

This time, I decided to delete Vista as well and keep only U with one gigantic partition

---

### Post by mb_webguy on 2009-01-26
> **faust7 said:**
> Finally resigned myself...... and formatted!

This time, I decided to delete Vista as well and keep only U with one gigantic partition

Actually, if you haven't done it already, you might want to consider putting your root directory and home directory on separate partitions.  This will make upgrading (or reinstalling) much more painless later on, since you don't have to worry about losing your data or settings. Ubuntu can live comfortably on an 8GB partition, and you can devote the rest of the drive to your home directory.  If you want to have the option to put your system into hibernation mode, you'll need swap space about equal to your system memory.  While you can use a swap file, it's really simple to set up a swap partition during installation.

---

