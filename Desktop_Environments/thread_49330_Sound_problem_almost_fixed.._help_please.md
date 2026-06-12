---
title: "Sound problem almost fixed.. help please"
date: 2005-07-15
forum: Desktop Environments
---

### Post by Boggles3 on 2005-07-15
oh guys.. lol just to make sure i restarted and ya .. there was no sound again.. i fiddled with the analog stuff but thats not it..

i dloaded the drivers when i installed the alsa- lib,utils,driverand oss but i put them in a randome file on my desktop that i named alsa....
lol i think thats why my sound doesnt work.. i think they are sapposed to be in /usr/src/alsa  file... but i cant move them over because i dont have permision.. to write to that file..

how do i give myself permision.. i know its through console but i dont remember the commands..

or even better is there a way from root console that i can just grab a file from one folder and put it to another... like a move command or something????

cuz then i dont need permision right because ill me in as root...

anyone able to help.. i was so close .. lol ](*,)

---

### Post by not_yet on 2005-07-16
from a terminal:

to move

sudo mv [source] [destination]

to copy

sudo cp [source] [destination]

eg: I want to copy the file "myfile" from /home/mydirectory to  /usr/bin

sudo cp /home/mydirectory/myfile  /usr/bin

---

### Post by fresco on 2005-07-16
Sorry, I have similar question so I won't create new thread.
Boggles3, can I?  :grin: 


How to move/copy folder's **contents** to another dir? I've got clear with manipulating with folders, but not contents. E.g. how can I copy all files from the folder, If there's many of them, with single command?

---

### Post by angkor on 2005-07-16
try cp /foo/* [path-to-destination]

---

### Post by Boggles3 on 2005-07-16
ok that stuff works.. so i have move the files and installred and fallowed all the directions..

then i restart my gui.. with /etc/init.d/gdm restart.(sometimes id does not restart so i have to run the same while in console exept start instead or restart.. so that my sound restarts i geuss.. and i have sound that work perfectly..  if i go to my volume control on the top right of screen and right click-prefs i see two devices.. one has (oss) behind it and the other has (alsa) behind it.

but when i reboot the computer or shutdown at all ..
when it comes back up my sound works in the log in screen(i get the drum tap) but then when i log in a get no sound again..(also seems to hang a little here when transitioning from login to gui witch i would think means its doing something... i dunno like killing my sound :mad: .. lol.) 

anyways ya.. i also noticed that if i go look at my prefs like before that the (oss) one is gone....

why.. i can reinstall over and over again and get it back and then /etc/init.d/gdm restart and get my sound back but every time i reboot oss is gone..

i have heard of alsa killing other sound things like oss but dont know if its true will have to look into it..
orrrr... one of you could figure it out .. lol
im stumped right now so im ganna smoke a cigar and maybe there will be replies when i get back..

thanx in advance for any input at all.. its appriciated

---

### Post by llamakc on 2005-07-16
How about simply setting the mixer levels with something like aumix?

---

### Post by Boggles3 on 2005-07-16
lol wow look what i found 
in synaptic.. in the description of asla-base

ALSA driver configuration files
This package contains the ALSA initscript and various
configuration files for the ALSA drivers.

For ALSA to work on a system with a given sound card,
there must be an ALSA driver for that card in the kernel.
Linux 2.6 as shipped in kernel-image packages contains
ALSA drivers for all supported sound cards in the form
of loadable modules. For either Linux 2.6 or Linux 2.4
a custom alsa-modules package can be built from the
sources in the alsa-source package using the make-kpkg
utility (available in the kernel-package package). Some
pre-built alsa-modules packages are available in the
Debian archive.  Please read the README.Debian file for
information about loading modules.

[color=red]This package includes configuration files whose effect
is to prevent hotplug and discover from loading OSS
driver modules. If you want OSS driver modules to be
loaded by hotplug or discover then you must either edit
the relevant configuration files or purge (not just
remove) this package.[/color]

ALSA is the Advanced Linux Sound Architecture.
    [http://alsa.sourceforge.net](http://alsa.sourceforge.net)
OSS is the free version of the Open Sound System.
check out the stuff in red.. lol wtf.. so can anyone rell me how to alter the config so that is stops killing oss every time i install it?? so i can have sound afer i reboot instead of having to reinstall oss every time i boot.. 
cuz thats no fun lol

---

