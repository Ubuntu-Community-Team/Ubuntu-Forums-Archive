---
title: "coming from ubuntu"
date: 2005-04-12
forum: Desktop Environments
---

### Post by gix on 2005-04-12
I've recently "updated" my ubuntu to kubuntu
Often, when I'm hurry, I have to shutdown quickly the system...
It would be nice if I could find a "shutdown" and "reboot" options from the kde logout dialog...
any hints?
thanks
GiGi

---

### Post by Skaman on 2005-04-12
[QUOTE=gix]I've recently "updated" my ubuntu to kubuntu
Often, when I'm hurry, I have to shutdown quickly the system...
It would be nice if I could find a "shutdown" and "reboot" options from the kde logout dialog...
any hints?
thanks
GiGi[/QUOTE]
 u  can even add the shutdown button in your toolbar ^^

---

### Post by jobezone on 2005-04-12
[QUOTE=Skaman]u  can even add the shutdown button in your toolbar ^^[/QUOTE]
 If you use KDM instead of GDM, you will have a direct option in KDE to shutdown, reboot, and even start a new session as another user, as far as I remember using kdm in Debian unstable.

---

### Post by gix on 2005-04-12
[QUOTE=Skaman]u  can even add the shutdown button in your toolbar ^^[/QUOTE]
 good idea! 
simple and fast :)

---

### Post by kal_zakath on 2005-04-12
[QUOTE=Skaman]u  can even add the shutdown button in your toolbar ^^[/QUOTE]
 To have these options enabled ine the log off menu, it seems you have to use kdm instead of gdm. At least, it's how I got it to work.

To reconfigure this, simply do
```
sudo dpkg-reconfigure kdm
```

and choose kdm as you default display manager.

Then go to KDE Control center -> KDE Components -> Session Manager and make sure the first to checkboxes are checked (don't know exact name, I use french language pack, it's something like : "Confirm log off" and "Default shutdown option"

Hope this helps

---

### Post by Skaman on 2005-04-12
[QUOTE=jobezone]If you use KDM instead of GDM, you will have a direct option in KDE to shutdown, reboot, and even start a new session as another user, as far as I remember using kdm in Debian unstable.[/QUOTE]
 guys he wrote he's running KUBUNTU :P
so i guess he's using kdm

---

### Post by Skaman on 2005-04-12
guys he said he's usung KUBUNTU...so i guess he's using kdm....:P

---

### Post by wbeck85 on 2005-04-12
[QUOTE=Skaman]guys he wrote he's running KUBUNTU :P
so i guess he's using kdm[/QUOTE]
 not necessarily, skaman. You can use either.

---

### Post by kal_zakath on 2005-04-12
[QUOTE=Skaman]guys he wrote he's running KUBUNTU :P
so i guess he's using kdm[/QUOTE]
 nope he said he "updated" from ubuntu to kubuntu, so I gess he did an apt-get install kubuntu-desktop wich install kdm, but ask wether you want to continue to use gdm or switch to kdm. In his case, I'm quite sure he kept gdm, and that's why he can't directly shutdown or reboot from KDE

---

### Post by jobezone on 2005-04-12
[QUOTE=Skaman]u  can even add the shutdown button in your toolbar ^^[/QUOTE]
 If you use KDM instead of GDM, you will have a direct option in KDE to shutdown, reboot, and even start a new session as another user, as far as I remember using kdm in Debian unstable.

---

### Post by gix on 2005-04-13
[QUOTE=jobezone]If you use KDM instead of GDM, you will have a direct option in KDE to shutdown, reboot, and even start a new session as another user, as far as I remember using kdm in Debian unstable.[/QUOTE]
 yeah men!
you're right!
I was using gdm
Now that I've switched to kdm ... POFF! here are the new buttons!
thanks!!!!!!!!

keep on kubunting!  ;-) 
bye

---

### Post by gix on 2005-04-13
[QUOTE=kal_zakath]nope he said he "updated" from ubuntu to kubuntu, so I gess he did an apt-get install kubuntu-desktop wich install kdm, but ask wether you want to continue to use gdm or switch to kdm. In his case, I'm quite sure he kept gdm, and that's why he can't directly shutdown or reboot from KDE[/QUOTE]

rigth!
I did an apt-get install kubuntu-desktop and I kept gdm ... 
just because I prefer the gdm default background ... O_o
(yes, I know, I could have change the background from the control panel but.... I'm so lazy .... :p)

thanks again guys... and sorry for the late reply ... yesterday I went bed early :)

---

### Post by Beestar on 2005-05-10
[QUOTE=gix]yeah men!
you're right!
I was using gdm
Now that I've switched to kdm ... POFF! here are the new buttons!
thanks!!!!!!!!

keep on kubunting!  ;-) 
bye[/QUOTE]
 Hello everyone,

how do I change from GDM to KDM? 

I tried "sudo dpkg-reconfigure kdm", and that only said  
* Reloading K Display Manager configuration...                          [ ok ]
and I could not set anything...

Now, when I press the Administrator button in KControl, KControl freezes and doesn't present the password pop-up anymore... :-(

Thanks in advance for any help!


Bee

UPDATE:
It seems that I don't have GDM installed:
$ sudo dpkg-reconfigure gdm
Package `gdm' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: gdm is not installed
$
LOL.  I must see KDM then at start-up I guess...  :smile: 

I still can't use Administrator mode in KControl however... ;-(

---

### Post by bored2k on 2005-05-10
> **Beestar]Hello everyone,

how do I change from GDM to KDM? 

I tried "sudo dpkg-reconfigure kdm", and that only said  
* Reloading K Display Manager configuration...                          [ ok ]
and I could not set anything...

Now, when I press the Administrator button in KControl, KControl freezes and doesn't present the password pop-up anymore... :-(

Thanks in advance for any help!


Bee

UPDATE:
It seems that I don't have GDM installed:
$ sudo dpkg-reconfigure gdm
Package `gdm' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: gdm is not installed
$
LOL.  I must see KDM then at start-up I guess...  :smile: 

I still can't use Administrator mode in KControl however...  said:**
> 
 ```
sudo kwrite /etc/init.d/kdm
```
Where it says
> # To start kdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager

Change HEED_DEFAULT to false:
[QUOTE]# To start kdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=false
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager


Regarding you trashing your kcontrol.. that's weird. Perhaps try removing kdm and its configuration files and reinstalling from scratch. Reinstalling kcontrol if necessary. :/

**Edit !** - About that frozen kcontrol. I was able to reproduce the bug after I changed kdm to use a 1280*1024 wallpaper. After I changed to a normal 1024* one, it got fixed.

---

### Post by Kurse on 2005-05-11
[QUOTE=bored2k]```
sudo kwrite /etc/init.d/kdm
```
Where it says

Change HEED_DEFAULT to false:


Regarding you trashing your kcontrol.. that's weird. Perhaps try removing kdm and its configuration files and reinstalling from scratch. Reinstalling kcontrol if necessary. :/

**Edit !** - About that frozen kcontrol. I was able to reproduce the bug after I changed kdm to use a 1280*1024 wallpaper. After I changed to a normal 1024* one, it got fixed.[/QUOTE]

If you read that last section you quoted from the /etc/init.d/kde file, it shows you that the file that sets the default desktop manager is "/etc/X11/default-display-manager". All you have to do is edit this file and chage gdm to kdm.

---

