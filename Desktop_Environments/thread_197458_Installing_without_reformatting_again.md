---
title: "Installing without reformatting again"
date: 2006-06-15
forum: Desktop Environments
---

### Post by bdowd on 2006-06-15
Is there any way to install an upgrade or do a re-install without having to reformat the HD and thereby destroy the existing disk contents which reside on an already formatted disk? My upgrade from 5.10 -> 6.06 failed (X server on a Toshiba Satellite P35) and the existing forum threads do not seem to help any. I would like to reinstall either 5.10 so that I can retrieve my data. -Brian

---

### Post by teaker1s on 2006-06-15
while I don't guarrantee it will work start  computer, at grub hit Esc and select recovery mode.
then [here]("http://ubuntuforums.org/showthread.php?t=187765") as I broke mine

---

### Post by raptros-v76 on 2006-06-15
did you lose your xserver? can you boot? if so then first, edit your /etc/apt/sources.list so that all there are only the offical repositories enabled. then, sudo apt-get update, and sudo apt-get upgrade.

---

### Post by bdowd on 2006-06-15
Nope. The kernel is fine and provides a # prompt. But neither networking nor X function. If I could get either eth0 or ath0 working I could pull stuff off this machine and do a new install.

---

### Post by raptros-v76 on 2006-06-15
oh, to finish upgrading to 6.06, replace all instances of breezy in the sources.list with dapper, then sudo apt-get dist-upgrade

---

### Post by raptros-v76 on 2006-06-15
wait. networking doesnt work. shoot.
try this. do (with root) startx, and post the output.

---

### Post by raptros-v76 on 2006-06-15
wait a sec. do you have parted installed? you could concievabley partition your harddrive so that you have a second partition to put all your data on, but is seperate from the partion with the buggy ubuntu, and then fresh install the partition with the troubled system

---

### Post by bdowd on 2006-06-15
That might just work :) 
I do have a licensed copy of Ghost, too.

---

### Post by bdowd on 2006-06-15
I meant 'Partition Magic'

---

### Post by bdowd on 2006-06-15
...which, of course, doesn't support linux ...
I'm downloading parted off another machine ... we'll see it that flies.
I think your concept is AOK

---

### Post by teaker1s on 2006-06-15
try 
sudo apt-get install ubuntu-desktop

 as it's cached on harddrive.failing that what about 

sudo apt-cdrom add

sudo apt-get update


and either install

ubuntu-base and ubuntu-desktop

or try dist upgrade from cd

---

### Post by raptros-v76 on 2006-06-16
thats the problem. his network stuff on that computer doesnt work. he has to reinstall from a disk.

---

### Post by teaker1s on 2006-06-16
yes with the way I suggested you can use synaptic and ubuntu cd no network required, also the hard drive package cashe should have some stuff in it from  install that failed

---

### Post by raptros-v76 on 2006-06-16
ok. didnt understand you. still, might as well do the /home as a separate partition trick. just in case he has to do the fresh install. but if fresh installing can be avoided, then avoid it.

---

