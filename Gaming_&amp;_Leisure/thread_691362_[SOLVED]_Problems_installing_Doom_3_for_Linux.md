---
title: "[SOLVED] Problems installing Doom 3 for Linux"
date: 2008-02-08
forum: Gaming &amp; Leisure
---

### Post by Djalmahal on 2008-02-08
Hi,

i'm trying to install doom 3for linux  on linux, tried around for a couple of hours now, so:

WHen I run doom3-linux-1.1.1282x86.run from the CD 1 in a terminal, it checks integrity, lets me enter my root password  but then can't write to /usr/local/games due to permission. Do I have to run it with sudo or such and if so how do I switch to the cdrom0 before in the terminal

One other (silly) question: What's a x86 machine? How do I find out if I have one?

Thanks
Andreas

---

### Post by Perfect Storm on 2008-02-08
Well, if you want to install it at /usr/local/games it requires sudo infront (so you install it globally). Note don't run the game with root afterwards.

You could install it locally (more safe).

---

### Post by ErusGuleilmus on 2008-02-08
It is a CISC processor. Essentially, you can only run a 32bit OS on it.

---

### Post by cacharreo on 2008-02-08
Try to change the path in the terminal using the *cd* (change dir) command where *doom3-linux-1.1.1282x86.run* is located, then run 
*sudo doom3-linux-1.1.1282x86.run*

x86 is the intel processor architecture to design to the computers with intel build in processors (standard PC's)

Good Look!

---

### Post by Djalmahal on 2008-02-08
Ok, how do I change to the cdrom0 using cd, the command

cd cdrom0 doesn't work,

only then can i run

sudo doom3-linux-1.1.1282x86.run

Till now i  started the file with right-clicking the file. 

So how do I change to my cdrom drive in order to run it as sudo?

I'm not sure if i have a x86 machine, am I able to run it on a 32-machine?

---

### Post by w5cgu on 2008-02-08
Where does one get good games that will run on Linux?
Am I missing the boat here.
I sure want to get away from WinBloz for my gaming ....

Thanks in advance,  John :)

---

### Post by Djalmahal on 2008-02-08
Well, for a change I myself (andreas, the guy who started this thread) can give an answer. THere are plenty of free games which you can access from your Synaptic Manager, or you google "Linux Games" and will get to some web pages which will introduce some games. Now, most of these games have been developed as a "hobby" so they are not backed by a massive budget and such. I'm just trying to install Doom 3 which would be the first "commercial" game that i would try on nativly  Linux.

Hope that helped you a bit.

Andreas

---

### Post by Cappy on 2008-02-08
32-bit is x86. As long as you aren't running it on a handheld embedded device it will work =P

To get to the cd-rom use
```
cd /media/cdrom
```
or
```
cd /media/cdrom0
```

now run
```
sudo sh doom3-linux
```
and then hit TAB before you hit enter. This will autocomplete the name.
I'm suggesting this because I don't think the file name you posted is right because it doesn't bring up any results on google.

"sudo doom3-linux-1.1.1282x86.run" won't work as previously suggested. It would need to be ```
sudo ./doom3-linux-1.1.1282x86.run
``` to be done like that.

---

### Post by Djalmahal on 2008-02-08
Thanks Cappy

nice answer, hot the spot, i look in the Ubuntu Bible how o cd to the cd rom, but i didn't find no straight answer.

Now, it went ahead but the output is


DOOM 1.1.1282 linux-x86 Oct  4 2004 08:21:14
Hostname: andreas-laptop
IP: 127.0.1.1 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Request &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
------ Initializing File System ------                         &#9474;  
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x16cf3b8a
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Current search path:        < Yes >       < No  >              &#9474;  
/home/andreas/.doom3/base&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
/usr/local/games/doom3/base                                       
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)link
game DLL: 0x0 in pak: 0x0                           Installing symlink /usr/locafile system initialized. /usr/local/games/doom3//doom3-dedicated
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg
andreas@andreas-laptop:/media/cdrom$ 

What should i think of that?

Thanks for your reply
Andreas

---

### Post by Cappy on 2008-02-08
According to this thread: [http://ubuntuforums.org/showthread.php?t=394154](http://ubuntuforums.org/showthread.php?t=394154)
you need to "copy pak000.pk4 and game00.pk4 from your doom3 cds/dvd."

It seems you need to find them on the cd-rom set and copy them into /usr/local/games/doom3/base/
Someone who has installed Doom 3 may know more.

---

### Post by Djalmahal on 2008-02-08
Thanks Cappy, i'll try things out, look up the thread you told me

---

### Post by Djalmahal on 2008-02-08
Ok Cappy (or whichover geek is reading this)

how do i copy to usr/local (tells me i don't have permission), do i have to type in long path descriptions with sudo in front and look up the proper command?

No easier way?

---

### Post by Cappy on 2008-02-08
if you REALLY want to do it the gui way you can use
```
gksudo nautilus /usr/local/games/doom3/base
```
(gksudo is for GUI apps. sudo is for terminal-based apps)


If it were me I would use the terminal, switch to the cd, and
```
sudo cp whatever.q4 /usr/local/games/doom3/base
```

---

### Post by w5cgu on 2008-02-08
So, where and how does one buy the cd rom you need to install in Linux???????????

Thanks in advance, John  :popcorn:

---

### Post by gisman on 2008-11-15
[http://zerowing.idsoftware.com/linux/doom/Doom3FrontPage#head-312a1b2c00cf18c0eacea2ded04a88d3a33767d4](http://zerowing.idsoftware.com/linux/doom/Doom3FrontPage#head-312a1b2c00cf18c0eacea2ded04a88d3a33767d4)

Go here to learn how to install doom 3 etc

---

### Post by mag1strate on 2008-11-24
I used the url that gisman gave and it worked perfectly:)

---

