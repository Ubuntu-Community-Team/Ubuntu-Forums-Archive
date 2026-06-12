---
title: "Ubuntu 13.10 Black Screen"
date: 2015-08-08
forum: Desktop Environments
---

### Post by xRt/7&amp;?bYe on 2015-08-08
I'm a intermediate Linux user.

Long story short, Haven't touched my Linux install in awhile. Had a backup of it with clonezilla, restored that to a VM (Hyper-V), everything boots fine, login, black screen (can still see the cursor).

Thought ok it doesn't like a VM. Restored to bare metal (same computer, but different video card; Radeon 7950 -> GTX980), get login screen, login, black screen (can still see the cursor). On baremetal I got some error screens asking me to view logs and reset to default desktop but nothing seemed to respond from that. I also get a there are updates window pop up (which fails cause my release is EOL).

I just don't get why I get the login screen but then after that goes black. I assume this has to do with the graphics drivers, but I have no idea how to go about fixing this. Getting it to work under a VM would be best, I just want to get in there remember what was all on there, backup bookmarks etc. then do a fresh install.

---

### Post by Bashing-om on 2015-08-08
Hello;

A number of things we can do to get at your files:
> 
I just want to get in there remember what was all on there, backup bookmarks etc. 


Be aware I have no experience with a VM.. but perhaps this procedure is the same in the virtual world as in the bare metal.
Try:
boot the machine to the grub boot menu, with the ubuntu kernel selected press the 'e' key for edit mode -> boot parameters screen;
In the parameters screen arrow down to the line similar : "inux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " replace the present parameters -  quiet splash $vt_handoff - with the term 'text' - without the quotes. Key combo ctl+x to continue the boot process to TTY1 with boot messages visible. 
In this boot mode, the GUI driver will not be activated.

Can you log in here with your credentials ? From this terminal one can look around and copy off the desired files.

As to the difficulties booting to a GUI, Yeah I highly suspect it is a graphics driver issue. The install configured for a particular set of hardwares, I bet the graphics driver from that old install was not removed prior to bringing the system up on different graphics sets. We will not beat on a dead horse in an attempt to install software;  The 13.10 software repository no longer exists.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-08-08
Welcome. 13.10 is no longer supported and reached EOL in July. Please upgrade to a supported release. By the sounds, 14.04 LTS would be the one as it is supported for five years, until 2019. 15.04 til next January. If you need to retrieve files, please create install media (USB or DVD), boot from it, 'Try Ubuntu' and when you are in a 'live' session at a desktop you can retrieve files to external storage.

Here's some links that might help:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

[http://xubuntu.org/](http://xubuntu.org/)

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Install Ubuntu:
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Make DVD:
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

USB:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Mate in 14.04:
```
sudo apt-get install ubuntu-mate-core ubuntu-mate-desktop
```

There are other spins. Depends on the specs of your machine, but if you are running a VM, any would probably be fine. 

:)

PS: 13.10 was an interim release. The interims are now supported for nine months, LTS for five years.

---

### Post by ajgreeny on 2015-08-08
I suspect that your problem is now the AMD graphics that you need but will be very difficult to achieve as 13.10 no longer can be updated easily as the repos of all packages have been moved.

If you can still boot to the "bare metal" install that you restored, when you get to the login screen use Ctrl+Alt+F1 to get to a command line and login there.

You will now at the very least be able to backup all your personal files to a USB drive or similar and can then think about the upgrading needed to 14.04.  In fact I would recommend a clean install as I don't think it is worth the palaver of upgrading 13.10, that may itself not be fully up to date, to 14.04.

---

### Post by xRt/7&amp;?bYe on 2015-08-09
it gets to the graphical login. First boot after restore it gives a low graphic mode error, gives an option to restore to default but then just goes into a endless loop. After entering my password I get a black screen. I can still open terminal and from there even open chrome and other apps, but window elements are missing (border, close/minimize, etc).

I sed the sources.list to change the archive.ubuntu.com to old-releases.ubuntu.com. So I able to update things and install new packages. I tried apt-get install nvidia-current and then reinstalling and reconfiguring xserver-xorg. Same thing.

Tried unity-tweak-tool --reset-unity but just got a bunch of dconf-WARNING **: failed to commit changes to dconf: errors. Tried mounting my NAS (which is still in fstab and used to work) and get bad FS type errors.

I don't work well in command line for going through my files, plus I can't get a connection to my nas now.

[ATTACH=CONFIG]263744[/ATTACH]

And after I enter my password...

[ATTACH=CONFIG]263743[/ATTACH]


And I know 13.10 is EOL. I just want to get this back up and running so I can check over everything and grab what I need. Then I will reinstall fresh a LTS version.

---

### Post by Bucky Ball on 2015-08-09
You can restore files from a live boot. Please attach large pictures but 'Go Advanced' and using the paperclip icon, thanks, rather than inserting them into the body of your posts. :)

---

