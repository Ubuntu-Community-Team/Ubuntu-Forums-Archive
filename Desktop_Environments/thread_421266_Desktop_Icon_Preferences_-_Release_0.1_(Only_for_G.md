---
title: "Desktop Icon Preferences - Release 0.1 (Only for Gnome)"
date: 2007-04-24
forum: Desktop Environments
---

### Post by chakkaradeep on 2007-04-24
Please refer this [thread]("http://ubuntuforums.org/showthread.php?t=419713")

This application helps every newbie (and everybody) in showing and hiding the gnome desktop icons namely,

1) Computer
2) Network
3) Documents
4) Home
5) Trash
6) Volumes

This is the first release. I have attached the files.The steps are as follows,

[LIST]
[*]tar xjvf dic-0.1.tar.bz2
[*]cd dic-0.1
[*]sudo ./install (to install the application)
[*]sudo ./un-install (to uninstall the application)
[*]Go to menu System-->Preferences-->Desktop Icon Preference
[/LIST]

_**Things To DO**_
[LIST]
[*]Build a deb package (need help :( )
[*]Try to find ways to show/hide specific volumes in the desktop (sda1,sda2)
[*]Option to create new icons in the desktop (should we really need this?)
[*]Try to merge with any existing gnome application
[/LIST]

Any queries/bugs please post here in this thread. Soon, will create launchpad and other entries.

Thanks :)

---

### Post by bwhite82 on 2007-04-24
This is absolutely great. However, why not work with the Gnome/KDE developers to make this a default option?

---

### Post by Hex_Mandos on 2007-04-24
I like it. Would you like me to translate it into Spanish? I've done a few English->Spanish translations (gShutDown, KBlogger, and a few other tools), it wouldn't take too much work.

---

### Post by gashcr on 2007-04-24
I think these are the little details developers don´t consider and are actually very important, in order to get a better customization. This is a great option for newbies. Would be great if you manage to let people change the icons from the application. ( I haven´t tested it yet so I don't know if its already possible, but could be a good idea if not implemented, as some people don't like the trashcan icon of some iconsets... it happens to me sometimes... )

---

### Post by Dralt on 2007-04-24
Isn't that what GConf is for?

---

### Post by chakkaradeep on 2007-04-24
Hi All,

> **Soldierboy said:**
> This is absolutely great. However, why not work with the Gnome/KDE developers to make this a default option?

Thanks Soldierboy. I would like to work with the developers to make this default. But I think there should be more improvements in this small application,like,

1) hide/show specific volumes - show sda1 , hide sda2 whenever the user needs to. Now as a whole, you can hide and show volumes being used.

The above mentioned problem seems to be very tough as I have not found any solution, so will be digging into it more in the coming weeks :) 

> **Hex_Mandos said:**
> I like it. Would you like me to translate it into Spanish? I've done a few English->Spanish translations (gShutDown, KBlogger, and a few other tools), it wouldn't take too much work.

Mandos, I am programming by learning, and I have to include translation too. I will sure ping you soon for the translation :) . Thanks for the help !

> **gashcr said:**
> I think these are the little details developers don´t consider and are actually very important, in order to get a better customization. This is a great option for newbies. 

Yes, I too thought the same gashcr :) 

> **Dralt said:**
> Isn't that what GConf is for?

Yes, but for each time you cant edit GConf :D. You can change any settings in Gnome using GConf, but how many of us really use GConf. For example, to change the desktop background, it can be done via GConf and also via System-->Preferences-->Desktop Background :( 

Thanks for the support friends...sure we could make more customizations together :guitar:

---

### Post by jramey on 2007-04-24
For some reason the app failed to start, I like it though, it is nice to have it in prefs.

For those who have  the same problem.;

   1. Hit ALT-F2 and type: gconf-editor
   2. Select “Apps” > “Nautilus” > “Desktop”
   3. check/uncheck the boxes for computer_icon_visible, documents_icon_visible, or trash_icon_visible.

You should now see “My Computer” “My Documents” and “Trash” icons included on your desktop. Simply reverse these steps to remove any of the items.


-fear the Penguin

---

### Post by chakkaradeep on 2007-04-24
> **jramey said:**
> For some reason the app failed to start, I like it though, it is nice to have it in prefs.


jramey, can you run the application in the terminal, just do these steps,

1)open the terminal
2)type **desktop-icon-preference**

If any errors come, please do report here :)

---

### Post by chakkaradeep on 2007-04-26
> **chakkaradeep said:**
> 
1) hide/show specific volumes - show sda1 , hide sda2 whenever the user needs to. Now as a whole, you can hide and show volumes being used.


Currently the development is going on for the above mentioned feature :KS 

Got the idea of how to do that and yes i think many are in need of this , so the next initial version enabling to hide/show specific volumes will be out in this weekend or this monday O:) :p

---

### Post by smartboyathome on 2007-04-26
I might be able to package this for you (I am currently *trying* to learn packaging, and I may use this as my learning tool). Since it automatically installs itself, it shouldn't be too hard. ;)

---

### Post by smartboyathome on 2007-04-26
Is there any way you could make a version of this which uses the ./configure meathod? That would be easier for me to make into a debian file, as I do not have to configure it. ;)

---

### Post by chakkaradeep on 2007-04-27
> **smartboyathome said:**
> Is there any way you could make a version of this which uses the ./configure meathod? That would be easier for me to make into a debian file, as I do not have to configure it. ;)

Thanks smartboyathome :p

Its a python file :) I will check it out how I can make the compilation and installation simple so that i can be packaged.(just write something like *python setup.py install*)

---

### Post by chakkaradeep on 2007-04-27
Hi All,

I am glad to announce the next release of Desktop Icons Preferences.

**_What are the improvements_**

Enabled to show/hide specific volumes in the desktop. So now , if the user wants to hide *sda4* and have only *sda2* on the desktop, the user can do it now :) 

**_To Install_**
[LIST]
[*]tar xjvf dip-0.1.tar.bz2
[*]cd dip-0.1
[*]sudo ./setup install (for installing)
[*]sudo ./setup remove (for un-installing)
[*]Run it from menu System-->Preferences-->Desktop Icons Preferences
[/LIST]

**_Limitations_**

1) You cant keep custom names or icons for volumes shown on your desktop. So as of now, if its *sda2*, the icon name gets created as sda2

2) If you change the created desktop volume entry's name , the desktop-icons-preferences does not keep track of the name changes, however, you can change the icon

3) As per the standard, this works only for partitions mounted at **/media** and thus the default Ubuntu setup will work without any flaws.

**_Things to do_**

1) Still haven't created any source forge or launchpad entries :( 
2) The GUI has to be improved a bit
3) deb package has to be created
4) Translation to various languages
5) Enable to show other partitions mounted in other locations than /media  (is it really needed??)
6) To get the label of the partition and display instead of *sda4* or *sda5*

Please report your bugs and what you think of the improvement.

Here are some screen shots too attached :)

---

### Post by 16777216 on 2007-04-27
This is exactly what I need. I have been trying to create a "guest" account that is restricted to the "guest" home folder but allow access to the CD and DVD drives.
I have a Windows XP drive mounted rw and don't want the guest to mess with it.
I know it will still show up in the file manager but this will lower the chances of unwanted access.

Well,.. I get this error.

Traceback (most recent call last):
  File "/usr/bin/desktop-icons-preferences", line 6, in <module>
    ui=dipui.DipUI()
  File "/home/chaks/dip-0.1/dipui.py", line 197, in __init__
  File "/home/chaks/dip-0.1/dipui.py", line 122, in drawCustomSetupPage
IndexError: list index out of range

---

### Post by airtonix on 2007-04-27
i would like to see you make a metacity version of the theme manager for emerald.

but what it also lacks is what you are starting with here. bravo

---

### Post by chakkaradeep on 2007-04-27
> **16777216 said:**
> 
Traceback (most recent call last):
  File "/usr/bin/desktop-icons-preferences", line 6, in <module>
    ui=dipui.DipUI()
  File "/home/chaks/dip-0.1/dipui.py", line 197, in __init__
  File "/home/chaks/dip-0.1/dipui.py", line 122, in drawCustomSetupPage
IndexError: list index out of range

can you please check whether you have **/etc/mtab** file ?

---

### Post by chakkaradeep on 2007-04-27
> **airtonix said:**
> i would like to see you make a metacity version of the theme manager for emerald.

Well, this is not a theme manager :)  whereas a program to manage the default gnome desktop icons.

---

### Post by 16777216 on 2007-04-28
> **chakkaradeep said:**
> can you please check whether you have **/etc/mtab** file ?

Yep sure do.

```
/dev/hdb3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
/dev/hdb2 /boot ext3 rw 0 0
/dev/hdb7 /home ext3 rw 0 0
/dev/hdb1 /media/Storage vfat rw,utf8,umask=007,gid=46 0 0
/dev/disk/by-uuid/3E3451B63451723F /media/Windows fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/hdb5 /var ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
```

---

### Post by chakkaradeep on 2007-04-29
> **16777216 said:**
> Yep sure do.

```
/dev/hdb3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
/dev/hdb2 /boot ext3 rw 0 0
/dev/hdb7 /home ext3 rw 0 0
/dev/hdb1 /media/Storage vfat rw,utf8,umask=007,gid=46 0 0
/dev/disk/by-uuid/3E3451B63451723F /media/Windows fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/hdb5 /var ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
```

Thanks , I think I am getting what mistake I have done...will rectify it soon ..thanks for the file contents :)

---

### Post by psiu on 2007-04-29
That is a fantastic little bit of work there. I just installed Feisty last weekend, my first real foray into LInux in a couple of years, and am very impressed--one of the things that stumped me for a bit was getting my desktop "just right"--this would be a fantastic addition IMO.

Great work so far!

---

### Post by raeb on 2007-05-05
I seem to be having trouble on edgy w/ gnome.  It install fine and I see it in the correct location (System->Prefs->Desktop Icon Prefs).  However, when I click to start the app nothing happens.  I get the busy mouse for several seconds then nothing happens.  Typing desktop-icon-preferences in the terminal gives me:

```
me@mycomp:~$ desktop-icons-preferences
Traceback (most recent call last):
File "/usr/bin/desktop-icons-preferences", line 3, in ?
import dipui
ImportError: No module named dipui
```

I'm quite the linux newbie, any advice?

---

### Post by chakkaradeep on 2007-05-06
> **raeb said:**
> I'm quite the linux newbie, any advice?

This works out of  the box in feisty as its built using python2.5. You can however install python2.5 in edgy,try the below in the terminal,

**sudo apt-get install python2.5**

and please do update if its working :) 

Thanks

---

### Post by raeb on 2007-05-06
Fixed it by upgrading to fiesty instead, but that method did work in edgy.  Awesome little application, thanks  :D

---

### Post by nw_raptor on 2007-05-08
Looking good.

Problem:

I have several (7) network shares mounted via fstab, which normally show up on the desktop. The Custom Volumes Icon Setup tab doesn't show these. Instead, it only shows my local partitions (4).

the interesting part of fstab:

//tequila/linux	/media/Tequila\040Linux	cifs	username=username,password=password,gid=users,dir_mode=0777,file_mode=0777,codepage=cp737,iocharset=utf8,rw	0	0

//tequila/storage	/media/Tequila\040Storage	cifs	username=username,password=password,gid=users,dir_mode=0777,file_mode=0777,codepage=cp737,iocharset=utf8,rw	0	0

//tequila/junk	/media/Tequila\040Junk	cifs	username=username,password=password,gid=users,dir_mode=0777,file_mode=0777,codepage=cp737,iocharset=utf8,rw	0	0
//kiwi/linux	/media/Kiwi\040Linux	cifs	username=username,password=password,gid=users,dir_mode=0777,file_mode=0777,codepage=cp737,iocharset=utf8,rw	0	0

//kiwi/windows	/media/Kiwi\040Windows	cifs	username=username,password=password,gid=users,dir_mode=0777,file_mode=0777,codepage=cp737,iocharset=utf8,rw	0	0

and mtab:
//tequila/linux /media/Tequila\040Linux cifs rw,mand 0 0
//tequila/storage /media/Tequila\040Storage cifs rw,mand 0 0
//tequila/junk /media/Tequila\040Junk cifs rw,mand 0 0
//kiwi/linux /media/Kiwi\040Linux cifs rw,mand 0 0
//kiwi/windows /media/Kiwi\040Windows cifs rw,mand 0 0

Ideas?

---

### Post by Stickymaddness on 2007-05-08
Just wanna say nice one to chakkaradeep!! 

Thanks for this excellent little program, took care of a big annoyance of mine!!

---

### Post by chakkaradeep on 2007-05-09
> **nw_raptor said:**
> 
I have several (7) network shares mounted via fstab, which normally show up on the desktop. The Custom Volumes Icon Setup tab doesn't show these. Instead, it only shows my local partitions (4).


It reads only the partitions mounted at **/media** as that is termed as the common location where partitions are mounted by the distributions. Are your network shares mounted at **/media/<location>** ?

---

### Post by chakkaradeep on 2007-05-09
> **Stickymaddness said:**
> 
Thanks for this excellent little program, took care of a big annoyance of mine!!

Thanks :) 

Would anybody be interested to package this for ubuntu ? 

Thanks again :)

---

### Post by jketvirtis on 2007-05-09
I just want to say thank you.  I've been looking for a way to only display the volumes I want on the desktop for a while now.  This is just great.

---

### Post by nw_raptor on 2007-05-09
> **chakkaradeep said:**
> It reads only the partitions mounted at **/media** as that is termed as the common location where partitions are mounted by the distributions. Are your network shares mounted at **/media/<location>** ?

Sure are, that's why I attached my fstab...

//tequila/linux /media/Tequila\040Linux cifs username=username,password=password,gid=users,dir_ mode=0777,file_mode=0777,codepage=cp737,iocharset= utf8,rw 0 0

The only thing is that i use \040 to escape a space char. As in "Tequila Linux" in /media/.

---

### Post by chakkaradeep on 2007-05-09
> **nw_raptor said:**
> 
The only thing is that i use \040 to escape a space char. As in "Tequila Linux" in /media/.

Ok, will check this out. I think the use of the space char can be stopping it somehow.

---

### Post by smartboyathome on 2007-05-10
> **chakkaradeep said:**
> Thanks :) 

Would anybody be interested to package this for ubuntu ? 

Thanks again :)


I finally found a python-to-debian program to get a package for this!!! :) I hope this works!!! I tried it on my computer, and it did what it should, so it should work for you guys. I will try to keep this updated.

---

### Post by chakkaradeep on 2007-05-10
> **smartboyathome said:**
> I finally found a python-to-debian program to get a package for this!!! :) I hope this works!!! I tried it on my computer, and it did what it should, so it should work for you guys. I will try to keep this updated.

Hey, thats cool , thanks smartboyathome :) 

I think there is some problem. I installed it, neither i got the desktop-icons-preferences executable nor the menu item :(

---

### Post by smartboyathome on 2007-05-10
I guess it doesn't work then... :/

---

### Post by chakkaradeep on 2007-05-10
> **smartboyathome said:**
> I guess it doesn't work then... :/

Can you give me the link to that application for creating deb packages from python ?

---

### Post by smartboyathome on 2007-05-12
I can't give you a link, but I can give you a name of the program I used on Ubuntu (accidentally wiped ubuntu off my comp while trying to dual boot SAM Linux and Ubuntu). I think it is called EMP (or ENP, or something like that).

---

### Post by smartboyathome on 2007-08-26
I have been using this constantly, is there any new version? If not, mind if I build upon it once I finish learning python?

---

