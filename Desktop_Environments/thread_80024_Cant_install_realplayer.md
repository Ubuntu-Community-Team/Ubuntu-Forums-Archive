---
title: "Cant install realplayer"
date: 2005-10-21
forum: Desktop Environments
---

### Post by Darrin on 2005-10-21
Or maybe I did but it isnt working. I did ```
sudo apt-get install realplayer
```. I see realplayer listed in Applications and I click on it. I can see it at the bottom of the screen trying to load and then after a few seconds it just quits. How do I correct this?

---

### Post by brk3 on 2005-10-21
try running it from the command line and it should tell you what the error is. then post the error up here and we should be able to help

---

### Post by Darrin on 2005-10-21
[QUOTE=brk3]try running it from the command line and it should tell you what the error is. then post the error up here and we should be able to help[/QUOTE]

Will do. Just one little question first......Where do I go to get to the command lin? :confused: 

Newbie Here :(

---

### Post by paddyg on 2005-10-21
here's my experience:

i've never used apt-get with realplayer.

In Hoary i manually downloaded the file from realplayer site and installed it with no problems whatsoever.

In Breezy I downloaded the file from the site, but i had some problems with /usr/lib/libstdc++.so.5.0.7 as Breezy uses version 6. I copied and pasted the lib Realplayer wanted from my Hoary disk (I've got both Hoary and Breezy) and everything was ok.

---

### Post by paddyg on 2005-10-21
[QUOTE=Darrin]Will do. Just one little question first......Where do I go to get to the command lin? :confused: 

Newbie Here :([/QUOTE]

Your Terminal

---

### Post by Perfect Storm on 2005-10-21
Download realplayer here: [http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner](http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner)

Then
```
chmod a+x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin

```
(remember to do this in the right directory)

As paddyg says, you'll need /usr/lib/libstdc++.5-something

```

sudo apt-get install libstdc++5

```

---

### Post by Darrin on 2005-10-21
Heres what came up.
```
darrin@ubuntu:~$ sudo apt-get install realplayer
Password:
Reading package lists... Done
Building dependency tree... Done
realplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
darrin@ubuntu:~$

```

---

### Post by heart_reaver on 2005-10-21
[QUOTE=Darrin]Heres what came up.
```
darrin@ubuntu:~$ sudo apt-get install realplayer
Password:
Reading package lists... Done
Building dependency tree... Done
realplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
darrin@ubuntu:~$

```[/QUOTE]

I think you have installed the realplayer

---

### Post by Darrin on 2005-10-21
It does appear it should be installed but it wont launch. :(

---

### Post by Darrin on 2005-10-21
Thanks Artificial Intelligence. Ill try what you said when I get home from work.

---

### Post by Darrin on 2005-10-21
Im totally confused here. I am very new to linux and am lost by all this code stuff. I downloaded Real and placed in my home folder.
I went to the terminal and pasted this:```
chmod a+x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin
```

I have no idea what this means: "As paddyg says, you'll need /usr/lib/libstdc++.5-something"

So this is pretty much where im at right now. Very confusing for me. I wish it was just launch and install like in windows. 
I think I need baby steps here. ;)

---

### Post by Darrin on 2005-10-21
I kept messing with it and tried installing it again according to the realplayer website instructions. It works, but its not in my application menu. How do I get it to show up there. I want it to be where it should be.

---

### Post by Darrin on 2005-10-22
Im really making a mess here. I ended up having a realplayer folder in /opt. I try to delete it and its not allowing me to do so because of permissions. How do I delete this folder. This whole thing is getting soo frustrating. I spent several hours and cant figure this out..errrrr. Windows isnt looking soo bad now.

---

### Post by AnakiMana on 2005-10-22
Hi, I installed RealPlayer also, and found that I can only run it by using the File Browser (under Applications menu, then Accessories) and going into the folder \usr\local\RealPlayer\ and then double-clicking on realplay.bin.

I want a shortcut on my desktop.  I've tried right-clicking on the desktop and "Create launcher..." to create this shortcut.  I know I'm browsing to the same location, but it doesn't launch it!  I've also tried dragging a shortcut from the File Browser onto the desktop.  Still can't get RealPlayer to launch.  What's going on??  Is this a Ubuntu problem or a RealPlayer problem or a user-problem?  ;)

---

### Post by bionnaki on 2005-10-22
[QUOTE=Darrin]Im really making a mess here. I ended up having a realplayer folder in /opt. I try to delete it and its not allowing me to do so because of permissions. How do I delete this folder. This whole thing is getting soo frustrating. I spent several hours and cant figure this out..errrrr. Windows isnt looking soo bad now.[/QUOTE]

...then give your username permissions to do so.

sudo -s
chown [your username] [directory]
and the right-click & change write permissions.

---

### Post by AnakiMana on 2005-10-22
[QUOTE=AnakiMana]Hi, I installed RealPlayer also, and found that I can only run it by using the File Browser (under Applications menu, then Accessories) and going into the folder \usr\local\RealPlayer\ and then double-clicking on realplay.bin.

I want a shortcut on my desktop.  I've tried right-clicking on the desktop and "Create launcher..." to create this shortcut.  I know I'm browsing to the same location, but it doesn't launch it!  I've also tried dragging a shortcut from the File Browser onto the desktop.  Still can't get RealPlayer to launch.  What's going on??  Is this a Ubuntu problem or a RealPlayer problem or a user-problem?  ;)[/QUOTE]

Ok, I realized what I did wrong.  My shortcut needed to point to "realplay", not "realplay.bin".  Makes me wonder why double clicking on realplay.bin opened it in the file browser, though.  *shrug*

---

### Post by l0c0dantes on 2005-10-22
Hi! Ive just installed realplayer, But I cant find a way to make a media library, is that possible in the linux version?

---

### Post by heart_reaver on 2005-10-28
[QUOTE=Darrin]I kept messing with it and tried installing it again according to the realplayer website instructions. It works, but its not in my application menu. How do I get it to show up there. I want it to be where it should be.[/QUOTE]


You are not getting realplayer icon in menu of application :)

go to [www.ubuntuguide.org](www.ubuntuguide.org) see how MySQLCC's icon is created in Application menu

Like that u can make of any applcation u have made. 

Also you can use smeg menu editor for the same

---

