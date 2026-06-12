---
title: "Sansa e250 will not connect to Ubuntu 9.04"
date: 2009-04-28
forum: General Help
---

### Post by Gartral on 2009-04-28
hello, I have a Rockboxed Sansa e250, i can't mount the device on Ubuntu 9.04, I took dmesg ([http://pastebin.com/f59e9d3ff](http://pastebin.com/f59e9d3ff)) and lsusb ([http://pastebin.com/f24ecdc38](http://pastebin.com/f24ecdc38)) pastebins, but no one can seem to help me on IRC.. some people said it was due to the firmware (unlikely as it mounted fine in 8.10) and someone sugested the the drive could have bad spots... but i need some help either repairing, or reformatting the device.. both drives are fat32 :(:(:(:x

---

### Post by freonchill on 2009-04-28
do you have the device in "USB drive mode" or "media mode" ?

---

### Post by Gartral on 2009-04-28
It's been Rockboxed (with post 3.2) so its in MSC (Disk) mode

---

### Post by timcredible on 2009-04-28
my granddaughter has an e250, if you don't get a solution to this, pm me and i'll make a point of testing it on one of my 9.04 systems.  she replaced it with an ipod recently, so she hasn't tried the e250 on 9.04 yet.

---

### Post by Garrovick on 2009-04-28
Did you try it in original Sansa configuration with MSC mode?

The e250 is a drag and drop device. I've owned two.

---

### Post by Gartral on 2009-04-28
yes, several times, with same results, same as MTP mode with rythmbox... nada...


::EDIT:: 

  Well... somewhere... i got it too connect in MTP mode under OFW (Original FirmWare) and i can browse and grab off of it what i need... still need to repair disk in MSC mode though

---

### Post by Gartral on 2009-04-28
Found the fix, HAL is the culprit! you need either delete, or comment out the sansa bits of /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi 
> gksu gedit /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi and restart HALd > /etc/init.d/hal restart this worked for me!

---

### Post by RandyNose on 2009-05-23
It didn't work for me. - So I at the moment the only way to update my Sansa is to use Sidux... Sigh...

---

### Post by jasonchow on 2009-07-20
Sorry, this didn't work for me either.
My Rockbox Sansa e250 won't mount either. Rhythmbox will just quit on me if I try to open it, but with Songbird is just fine. All I want to do is open my .scrobbler.log for last.fm, but I can't even see the file.

On a side note, Ubuntu has been nothing but problems for me; my printer, my mp3 player, etc. I want to make this work, but every corner I turn, there's another problem...

---

### Post by mwcrowley on 2009-07-22
I was having the same issue, but with a c250 Here are a couple of links worth looking at [http://randynoseworthy.blogspot.com/2009/05/sansa-e200-seires-not-mounting-bug.html](http://randynoseworthy.blogspot.com/2009/05/sansa-e200-seires-not-mounting-bug.html)

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

The patch has been working for some people.  I tried it and it dmesg shows that it's not hanging waiting for the device to settle, but still not all the way there.  I'll post if I find a solution.


Doing this is a bit dicey, it could effect some functionality, so it's not exactly for everyone to try, but I installed the following two upgrades from karmic and now thunar will pick up the sansa, but nautilus will not, I get ".Failed to execute child process "gnome-mount" (No such file or directory)"
[http://packages.ubuntu.com/karmic/i386/libgphoto2-port0/download](http://packages.ubuntu.com/karmic/i386/libgphoto2-port0/download)
[http://packages.ubuntu.com/karmic/i386/libgphoto2-2/download](http://packages.ubuntu.com/karmic/i386/libgphoto2-2/download)

Oops, forgot you need to create a text file ".is_audio_player" in the root directory of the sansa and the root directory of the microSD card.  I have an 8 gig sd card that works well with the sansa.  Nautilus and Rythmbox still won't see it until I mount it with thunar, go figure.  I take a look at it later and post what I can sort out.  A rockboxed 10 gigs in a sansa c250 makes for a nice mp3 player.   If I could only get it to talk to Rythmbox with out the extra gyrations.  
As it stands I can only mount the sansa and the SD card in thunar, then Rythmbox will see it and all is well.  This probably won't be completely sorted out until Karmic is released.

---

### Post by ElMonoGrande on 2009-07-22
> **Gartral said:**
> Found the fix, HAL is the culprit! you need either delete, or comment out the sansa bits of /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi 
 and restart HALd  this worked for me!

This worked for me with my e280. Thanks, Gartral!  :D

---

### Post by mimicoco on 2009-08-10
Hi can i ask you to clarify? 

when you say delete or comment out the sansa bits, how do i do this? do i just remove the word 'sansa' or do i need to replace it woth something?
i cant get my e250 to show an icon on the desktop. it will show in amarok, not in rhythmbox. 

i filled it with music for a roadtrip tomorrow and when i unplugged it the music evaporated.:(

---

### Post by ozzyprv on 2009-09-10
> **Gartral said:**
> Found the fix, HAL is the culprit! you need either delete, or comment out the sansa bits of /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi 
 and restart HALd  this worked for me!


It worked for me on a c250.
Commented using <!-- blah, blah blah --> structure.

Thank you.

---

