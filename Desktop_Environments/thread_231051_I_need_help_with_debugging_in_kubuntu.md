---
title: "I need help with debugging in kubuntu"
date: 2006-08-06
forum: Desktop Environments
---

### Post by dennisharrison on 2006-08-06
#begin newbtroduction
I am a lifelong windows user.  I have always been able to fix my problems because I knew where to look to find what the error is and I research the specific problem until I come up with some kind of solution or use someones ready baked solution.  I am severly lacking in my ability to debug this kubuntu install on my main machine.  Because I am a newb :) I really really really like kubuntu.  Between kqemu, cedega, adept, automatix, and streamtuner. I am in love with the OS.  Ok, now on to what I just can't seem to get a grasp of mentally.  Hoping someone can help me cross that bridge,not too many insults please ;p  
#end newbtroduction

Using dapper 6.06 lts 2.6.15-19-386
any higher kernel and I have to disable acpi, and my computer acts funky.
 I am fine not having the newest kernel because this one works fine, and im sure the problem I am having will be resolved at some point soon.

I have used breezy before on this computer as my only os, well I wanted to install windows for a dual boot because I wanted to play some newer games (namely prey and fear) Ok so getting to the point

I had radeon drivers from ati working in breezy just fine.  When I installed dapper everything went fine and I got in using the default ati in xorg but now no matter what guide or walkthrough I follow I can't get the fglrx drivers to work.  I am supposed to be using them according to my  x config file.  when I do a fglrxinfo I am being told that mesa is being used. So, how do I track this sucker back to where mesa is loading instead of fglrx? I just don't know enough about the configuration layout of the system and I don't want to mess it up. maybe if someone could get me started I could figure the rest out?

Appreciate any leg up on this I can get! ;p

---

### Post by dennisharrison on 2006-08-06
bump
I have been wrestling with this off and on for almost a month ;p

---

### Post by dennisharrison on 2006-08-06
bump again

I am just trying to get some more views on this to see if someone has any suggestions.  I have read every article and post I can find with google using various configurations of

ati radeon fglrx ubuntu xorg mesa install guide help tutorial

I just plain old can't get mesa to go away and I don't know why it's even being loaded.

should I just reinstall and try from scratch? I would rather not since I have this install customized already, and I use satellite for internet.  It takes me forever to update everything.

---

### Post by dennisharrison on 2006-08-06
another bump

did I just choose a really bad title or something?

I haven't gotten a single reply ;p

---

### Post by dennisharrison on 2006-08-07
and another bump before bed

anyone? anything? please?

---

### Post by Barney2006 on 2006-08-07
I think it doesn't help you... but I've got the same problem :(
Maybe you post your /var/log/xorg.0.log per pastebin ([http://paste.uni.cc/](http://paste.uni.cc/) for example)

Btw. everything worked for me with Breezy...

---

### Post by dennisharrison on 2006-08-09
make sure your universe and multiverse repositories are enabled and updated

edit
*/etc/default/linux-restricted-modules-common*
and add fglx to disabled modules
**DISABLED_MODULES="fglrx"**

uninstall 
[I]fglrx-control
fglrx-kernel-source
xorg-driver-fglrx[/I] (and everything else with fglrx in it)

delete everything in your
*/usr/lib/* */usr/src/*
and
*/usr/X11R6/lib*
relating **fglrx**
in your */usr/lib/* move all files with mesa in the name (libGL.mesa.so or something like that) to your home directory for backup reasons

then uninstall 
*libgl1-mesa*

next download the ati drivers that support your chip from the ati website, I used the .run installer (r300 and better I am assuming since you are unhappy with mesa meaning you are wanting your 3d back?)

make sure the directory you downloaded the file too has no spaces in the name otherwise the installer will crap out on you when building packages

now install these packages
[I]module-assistant 
build-essential 
fakeroot 
dh-make 
debconf 
libstdc++5 
gcc-3.3-base[/I]

once thats done run the .run installer with the --buildpkg Ubuntu/dapper option on the end (./ati.installer.version.something.run --buildpkg Ubuntu/dapper)

you should generate 3 .deb files
install them however you like. 

[I]sudo dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.27.10-1_i386.deb
sudo dpkg -i fglrx-control_8.27.10-1_i386.deb
[/I]

are the commands I used because I was still in the terminal window

then here comes the part I was skipping because I didn't know any better (and I worked on this for freakin hours and hours)
[B]sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
[/B]then a
**sudo depmod -a**

after all this good stuff you go back to the same old
[I]sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
[/I]

then reboot x

this worked for me from an upgrade of breezy (even though I eventually just reinstalled apper anyway because I borked some other parts of my system playing with firewire cameras and image capture)

oh yeah and I fixed the kernel issue by updating the bios on my motherboard. And before the update I was able to get around the lockup by using options pci=noacpi and irqpoll after the boot command in grub

just in case anyone else is having the same problems (hopefully I can save someone from the 900 pages or so I read on the two topics ;p)

---

