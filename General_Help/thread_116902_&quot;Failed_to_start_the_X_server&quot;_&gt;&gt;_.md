---
title: "&quot;Failed to start the X server&quot; &gt;&gt; HELP!!!"
date: 2006-01-13
forum: General Help
---

### Post by platinum on 2006-01-13
hi,

i am pretty new to this linux stuff, but i do know that something is wrong here.

i tried installing ubuntu onto my laptop (Toshiba M50-Mx2), and the setup went great, but on the first (and every) boot, it comes up with a message that says 

"*Failed to start the X server (your graphical interface). It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem?*"

if i select "No", i get put into nowhere (not the shell or anything).

if i select "Yes", it comes up with all this information about the x window system version and stuff.

i don't know what happened during setup. no errors came up, and everything seemed to go smoothly. i didn't know that linux required so much knowledge. i kinda feel stupid :P

but this isn't the first linux to give me this problem. suse 10 did this to me, and i have no idea what to do. i'll talk to the suse people about that. 

i have no idea what to do. help!!

---

### Post by rjwood on 2006-01-13
first try ```
sudo dpkg-reconfigure xserver-xorg
``` See if that helps---answer the questions and unless you know what you are doing, I would suggest you accept the default info on there. go to the end of that and then type```
startx
```lets us know what happens.

---

### Post by dcstar on 2006-01-13
[QUOTE=platinum]hi,

i am pretty new to this linux stuff, but i do know that something is wrong here.

i tried installing ubuntu onto my laptop (Toshiba M50-Mx2), and the setup went great, but on the first (and every) boot, it comes up with a message that says 

"*Failed to start the X server (your graphical interface). It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem?*"

if i select "No", i get put into nowhere (not the shell or anything).

if i select "Yes", it comes up with all this information about the x window system version and stuff.

i don't know what happened during setup. no errors came up, and everything seemed to go smoothly. i didn't know that linux required so much knowledge. i kinda feel stupid :P

but this isn't the first linux to give me this problem. suse 10 did this to me, and i have no idea what to do. i'll talk to the suse people about that. 

i have no idea what to do. help!![/QUOTE]
Log onto a terminal session (CTRL-ALT-F1, username and password), and do:

sudo dpkg-reconfigure xserver-xorg

Select the VESA driver if you don't know exactly what video card you have.

Do "sudo init 6" to reboot afterwards.

---

### Post by platinum on 2006-01-13
after answering these questions it gave me to the best of my newbie-linux knowledge, it gave me this:

"*fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.*"

what do i do?

---

### Post by platinum on 2006-01-13
after answering these questions it gave me to the best of my newbie-linux knowledge, it gave me this:

"*fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.*"

what do i do?

---

### Post by platinum on 2006-01-13
after answering these questions it gave me to the best of my newbie-linux knowledge, it gave me this:

"*fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.*"

what do i do?

---

### Post by platinum on 2006-01-13
sorry for the triple post. i'm on a windoze machine, and it froze :P

---

### Post by rjwood on 2006-01-13
did you try dcstar's suggestion?? What is your graphics card?  Don't worry - we will get you up and going.

---

### Post by professor_chaos on 2006-01-13
do what rjwood sugests. Don't feel stupid, like you pointed out this happened on suse and I think its definately something that should be addressed in some form, to help new users get started in linux.
Hey, but on the up side once you figure out the problem and the solution, you will benifit from that knowledge and it will carry over into the OS in general.

---

### Post by platinum on 2006-01-13
i tried dcstar's and rjwood's solutions, and netiher of them worked.

on the toshiba M50-mx2 laptop, it has an ATI XPRESS 200M video card with 32mb shard memory (i adjusted it from 128mb shared to 32mb shared)

it gave me the error message i posted earlier (three times :P ), and then it tells me to look at the log file for more info. it gives me a directory, but i don't know how to navigate in the shell. :(

---

### Post by dcstar on 2006-01-13
[QUOTE=platinum]i tried dcstar's and rjwood's solutions, and netiher of them worked.

on the toshiba M50-mx2 laptop, it has an ATI XPRESS 200M video card with 32mb shard memory (i adjusted it from 128mb shared to 32mb shared)

it gave me the error message i posted earlier (three times :P ), and then it tells me to look at the log file for more info. it gives me a directory, but i don't know how to navigate in the shell. :([/QUOTE]
cd /directory-you-want-to-go-to
less log-file-name

---

### Post by platinum on 2006-01-13
k, i found the directory (/var/log), and the name of the log file is Xorg.0.log (there is also Xorg.0.log.old).

but when i type in either of these names, it says "command not found"

how do i view the log file?

---

### Post by rjwood on 2006-01-13
post the output of your var/log/syslog here.

---

### Post by rjwood on 2006-01-13
do ```
less /var/log/Xorg.0.log
```

---

### Post by platinum on 2006-01-13
[I](==) Log file : "var/log/Xorg.0.log" time: fri jan 13 15:48:42 2006
(==) Using config gile: "/etc/x11/xorg.conf"
(==) serverlayout "Default layout"
(**) |-->Screen "Default Screen" (0)
(**) |     |-->Monitor "Generic Monitor"
(**) |     |-->Device "ATI Technologies, Inc. Radeon Xpress 200M (RC410)
(**) |-->Input device "Generic Keyboard"
(**) |-->Input device "Configured mouse"
(**) |-->Input device "Synaptics Touchpad"
(WW) The directory "/usr/share/x11/fonts/cyrillic" does not exist
              Entry deleted from path
(WW) The directory "usr/share/x11/fonts/CID" does not exist[/I]

whatever the heck that means, i do not know :P

---

### Post by Xorg on 2006-01-13
In your /etc/X11/xorg.conf find

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
Driver "ati"
BusID "PCI:1:5:0"
EndSection

Add 
Option "noaccel" 
just before the EndSection to end up with

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
Driver "ati"
BusID "PCI:1:5:0"
Option "noaccel"
EndSection

Then restart the GUI by typing
startx

This should solve all your problems with the GUI not loading. :)

EDIT: to get into the file, type vi /etc/X11/xorg.conf

---

### Post by platinum on 2006-01-13
woah!!!!!

for no reason whatsoever, i did nothing but restart, and now it works!!!!!!!

EDIT: i'm in ubuntu now, and the first thing i check is the resolution:

1280x768            > good

but 0hz refresh rate?????????

---

### Post by Xorg on 2006-01-13
A 0Hz refresh rate?

Something tells me that it's not quite that slow... ;)

If it is, are you SURE you posted that? :p

---

### Post by rjwood on 2006-01-13
happy your back----:cool:

---

### Post by platinum on 2006-01-13
it says 0hz, but i don't care. its working!!! :D :D

now, in my history of using operating systems, there comes a time when i want to tweak it (change the look, different sounds, desktop look, etc)

where can i get different themes for gnome (i like blue-ish more than brown-ish)

i also want to know how i can get updates for ubuntu? (patches, security updates, program updates)

and lastly, how do i install a program? i know it sounds silly, but i know that it isn't just an exe to open. i have a snes emulator i want to run called zsnes. how do i install it?

---

### Post by andrewlt on 2006-01-13
574r7x

---

### Post by platinum on 2006-01-13
what do u mean startx (or in 1337: 574r7x, $7/\|2+><, etc) lol

x is already started.

---

### Post by Xorg on 2006-01-13
> where can i get different themes for gnome (i like blue-ish more than brown-ish)
System > Preferences > Theme or [Gnome Look](http://www.gnome-look.org)

> i also want to know how i can get updates for ubuntu? (patches, security updates, program updates)

apt-get update <package>

> and lastly, how do i install a program? i know it sounds silly, but i know that it isn't just an exe to open. i have a snes emulator i want to run called zsnes. how do i install it?

The easier ways are:
 Synaptic package manager (System > Administration > Synaptic Package Manager) 
Add or Remove Programs  (Applications > Add Applications)
[Automatrix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatrix) 


Also, look at the apt-get man page (type man apt-get into the Terminal)

If it's a .run file, open the Terminal, navigate to the directory, (type cd /path/to/directory) and then type sh ./filename.run

---

### Post by Jaygo333 on 2006-01-13
To the original poster if question hasn't been answered. If Answered, IGNORE.1?1
Just type
sudo /etc/init.d/gdm restart
That should work. Always works for me. If you want more options, type
...gdm /?

;):h34r: Jaygo333 ;)h34r:

---

### Post by platinum on 2006-01-13
thx everyone,

you've all been a great big help!!!

i have one more question for today:

i have downloaded zsnes ( a snes emulator), and i want to install it.

there are no *.run files. there is one file called install.sh, but i i have no idea how to use it.

---

### Post by platinum on 2006-01-13
k, i've gotten the tar.gz file for the program i want to install

i just got gcc too (ubuntu does not come with it????? odd :P )

anyway, i type ./configure, and it tells me to specify a build type.

what is that, and how do i do it?

---

### Post by platinum on 2006-01-13
k. now i've got gcc and everything i need, but now i need nasm.

where can i get it, and how do i install it?

---

### Post by platinum on 2006-01-13
k. i got nasm, and i'm trying to get sdl1.2, but it isn't installing correctly..

i used ./configure, then make, then sudo make install, and it does not work.

it says [install-recursive] error 1

---

### Post by Charon on 2006-01-14
tried "sudo apt-get install zsnes" yet?

---

