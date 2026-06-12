---
title: "Installation HELP!!!"
date: 2008-12-27
forum: General Help
---

### Post by dtrot55 on 2008-12-27
I currently got my hands on a second computer that i figured i would dedicate to Ubuntu.  It is a hand me down HP Pavillion a347x.  I upgraded the ram to 1gig...used to be 256...needless to say every attempt that i have tried has failed.

I first started out with stock everything in the computer..but the ram...and used the 8.10 cd i received in the mail from ubuntu.  It got all the way to about 70% and it went to a black screen and nuthing...no activity...so i used the other cd rom...same thing...then i switched hard drives...same thing...then i put in a different cd rom and same thing...so i tried the 8.04 disc...same thing and i also tried 7.10 and got the same thing...it just gets to a certain point and goes black....any ideas???

here is link on computer [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00043265&lc=en&dlc=en&cc=us&lang=en&product=374650](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00043265&lc=en&dlc=en&cc=us&lang=en&product=374650)

---

### Post by Dr Small on 2008-12-27
Are you letting the screen set while installation tries to finish, and a screensaver could be initiating that is freezing the system?

---

### Post by dtrot55 on 2008-12-27
i made sure to move the mouse and hit the keyboard so the monitor didn't go off

---

### Post by taurus on 2008-12-27
Try the alternate CD and make sure you burn it at a slow speed like 4x.

---

### Post by Dr Small on 2008-12-27
> **dtrot55 said:**
> i made sure to move the mouse and hit the keyboard so the monitor didn't go off
Ok. Then you can either try running a disk error check from the livecd (at the bootup prompt), burn it again at a lower speed, or try the alternate CD as taurus suggested.

---

### Post by dtrot55 on 2008-12-27
i downloaded 8.10 and burned it...trying this disc...my other was one i was sent from ubuntu...if this doesnt work ill burn at lower speed

---

### Post by dtrot55 on 2008-12-27
just got a cant open /lib/lsb/init-functions error during installation of the system  :( about 5% in this time

---

### Post by abn91c on 2008-12-27
its probably the Intel 845 series video card,its not compatible with compiz, did you try the live cd first?

---

### Post by dtrot55 on 2008-12-27
doing a check disc...will do live cd after this

---

### Post by dtrot55 on 2008-12-27
check disc came back fine

---

### Post by abn91c on 2008-12-27
from the live cd disable the desktop effects then run the installation, hopefully it will "remember" the settings when you reboot. On the other hand if the install seems to complete and you get to the log in screen then try ctrl+alt+f1 to get to the prompt, then remove compiz

---

### Post by dtrot55 on 2008-12-27
ran the live disc....black screen...going to put in my only other video card taht i could use and thats a pci ATI 9200SE

---

### Post by Dr Small on 2008-12-27
> **dtrot55 said:**
> ran the live disc....black screen...going to put in my only other video card taht i could use and thats a pci ATI 9200SE
As long as you have spare parts, that's the way to go ;)

---

### Post by dtrot55 on 2008-12-27
cant even get a screen to pop up using the pci video card....maybe its just a lost cause :(

---

### Post by abn91c on 2008-12-27
> **dtrot55 said:**
> cant even get a screen to pop up using the pci video card....maybe its just a lost cause :(
did you go into the bios  and setup the new ati card?

---

### Post by dtrot55 on 2008-12-27
yep told it main video was in PCI....also just tried to install windows and it failed...switching hard drives

---

### Post by dtrot55 on 2008-12-27
good news...got it to install and get me all the way to the log in screen no problems...now when i log in all i get is a orange screen :(


cant win!!

---

### Post by abn91c on 2008-12-27
> **dtrot55 said:**
> good news...got it to install and get me all the way to the log in screen no problems...now when i log in all i get is a orange screen :(


cant win!!
 now you are almost there, do ctr+alt+f1, at the prompt type  sudo apt-get remove compiz, followed by sudo apt-get remove compiz-core

---

### Post by dtrot55 on 2008-12-27
HELLO FROM UBUNTU 8.10!!! WOOOOOT!!!

THanks everyone...that was brutal...

just to summarize everything incase someone else has this problem.

I had to change a option in the bios...called Large Disc Access...Set that to "Other"

THis was the option that allowed me to get all the way through the installation

Then i did the ctr+alt+f1 at the login screen and typed:

sudo apt-get remove compiz

following that i did

sudo apt-get remove compiz-core

Restarted and IT WORKED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by abn91c on 2008-12-27
Welcome to 8.10 :popcorn:

---

### Post by dtrot55 on 2008-12-27
What exactly did i remove with teh compiz? Just the ability to do all the 3d and warping window stuff...should this slow down video performance without it?

---

### Post by Dr Small on 2008-12-27
> **dtrot55 said:**
> What exactly did i remove with teh compiz? Just the ability to do all the 3d and warping window stuff...should this slow down video performance without it?
No. On the contrary, Compiz will most likely slow down video preformance.

---

### Post by dtrot55 on 2008-12-27
well it is integrated intel crapzor video card..so i guess i cant expect much...now just to get flash installed hehe...on to the next problem

---

### Post by dtrot55 on 2008-12-27
would removing compiz mess with me getting flash installed?? I keep getting this...

dtrot@ubuntu:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for dtrot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

---

### Post by Dr Small on 2008-12-27
> **dtrot55 said:**
> would removing compiz mess with me getting flash installed?? I keep getting this...

dtrot@ubuntu:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for dtrot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
Sounds like you need to enable the universe repositories, else you installed the wrong version.

---

### Post by dtrot55 on 2008-12-28
would that be something i could do in the package manager? or is that somewhere else???

---

### Post by mkvnmtr on 2008-12-28
Enable that repository in software sources. You will probably want to enable the Medibuntu repository also. I don't have a tutorial in front of me but you can find several just googling Medibuntu.

---

### Post by hxcgrunger on 2008-12-28
Nevermind

---

