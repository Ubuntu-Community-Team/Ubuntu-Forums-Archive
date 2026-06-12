---
title: "ut2004 sound Problem and Pacthing"
date: 2006-12-21
forum: Gaming &amp; Leisure
---

### Post by kiyometane on 2006-12-21
hello i have 2 problems
i have no sound on my usb headset when playing ut2004. but the sound works elsewere.
the regular headset works fine but the sound is not too high.

can someone tell me step by step how to upgrade ut2004.
i want ece bonus pack and the latest patch 

help needed
thanks

---

### Post by Perfect Storm on 2006-12-22
upgrading:
Download the tar.bz2 file of UTMegapack and save it to your Desktop.

tar jxfv ut2004megapack-linux.tar.bz2
cd UT2004MegaPack

if you did go default with UT2004 installer path;

sudo cp -r * /usr/local/games/ut2004

---

### Post by kiyometane on 2006-12-22
> **Artificial Intelligence said:**
> upgrading:
Download the tar.bz2 file of UTMegapack and save it to your Desktop.

tar jxfv ut2004megapack-linux.tar.bz2
cd UT2004MegaPack

if you did go default with UT2004 installer path;

sudo cp -r * /usr/local/games/ut2004

i need clarification on how exactly to install that megapack.](*,) ](*,) ](*,) ](*,) 
is it 
tar jxfv ut2004megapack-linux.tar.bz2
cd UT2004MegaPack
sudo cp -r * /usr/local/games/ut2004[/QUOTE]

or this :
cd && cd Desktop
tar jxfv ut2004megapack-linux.tar.bz2
cd UT2004MegaPack
su
cp -r * /usr/local/games/ut2004

or that:
cd && cd Desktop
tar jxfv ut2004megapack-linux.tar.bz2
cd UT2004MegaPack
sudo cp -r * /usr/local/games/ut2004

i dont know if  i need ece bonus pack prior to that megapack
i'm using 64 bit edgy, i dont know if the magapack is valid for it

I installed the game with the cd version using this command
sudo sh /media/cdrom/linux-installer.sh
please help me on how exactly to install that megapack-linux.tar.bz2

---

### Post by Perfect Storm on 2006-12-22
It's 

cd ~/Desktop  (It's the same like cd && cd Desktop)
tar jxfv ut2004megapack-linux.tar.bz2
cd UT2004MegaPack
sudo cp -r * /usr/local/games/ut2004


All you need is the Megapack it includes all the stuff.
In Ubuntu you don't use **su** instead you put **sudo** infront of a command to do root stuff.

---

### Post by kiyometane on 2006-12-22
Oh your the one on ubuntu gamer forums :p 
i'm just being impatient posting in here and there at the same time
i'll do a clean install and input the code you gave me sine i messed up during the upgrading.
the game starter is a mess
 exec: 50: ./ut2004-bin: not found

thanks

---

### Post by Perfect Storm on 2006-12-22
Aye, it's me :)

---

### Post by kiyometane on 2006-12-22
Finally i got that sheit running after trials and errors](*,) ]
I had to rename ucc-bin-linux-amd64 to ucc-bin
and rename ut2004-bin-linux-amd64 to ut2004-bin

Now i still need to take care of my sound issue.
if this is solved i will dump windows for good

---

