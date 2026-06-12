---
title: "Several issue with Wine and Cedega un fiesty"
date: 2007-04-16
forum: Gaming &amp; Leisure
---

### Post by trespin on 2007-04-16
I have been trying to install several games on my ubuntu box. I have had success installing WoW and HL2 from folders where i pulled all data from the CD(dvd) and installed from the folder. But when i try and install from a disk (like with Diablo 2) it ends up asking me to put the Install disk in the drive.

 I have been reading through pages of how-to's on this subject, but nothing seems to work for me to get either Wine or Cedega to read games directly from a CD to install. 

Cedega: Will see the disk and populate all fields for a Diablo 2 install. but once I click install within cedega it says i need to put the install disk in, which it is in.

Wine: I can actually get wine to start the install process. I get all the way to the screen coming up to show progess of the game being installed to the system, and it just never does anything. A small window appears asking me to insert the install disk.

 I have tried many different work arounds that I have found from here, wine, and cedega forums along with searches around the net. Nothing seems to work for me where many others get this to install without a hitch. I am puzzled.

 I have ran all of the tests in both programs and my system runs and passes them all.

my system:

Asus A8n-E
2 gb Corsair DDR 3200
1 Seagate 120gb hraddrive (linux install)(sata port 4)
7800 GT Nvidia card

 I am at work and will post the specs that will be needed later today when I can.

 things that i am trying to figure out:

1. checking hal-device-manager shows my DVD/CD drive is /dev/scd0 (which is wierd for an IDE DVD drive) I see no input in fstab for /dev/scd0. I see a /dev/hdc that is /media/cdrom0 under fstab. I will post the output from fstab a little later.
2. I know wine a cedega work and run games, as I ahve installed several from my system folders. I just want to get my cdrom drive working.

I am just trying to play Daiblo 2 within ubuntu and it is driving me crazy. Not a newb, but newb to this.

 let me know what you need and i will post it throughout the day to help someone help me.

thank you

Will

---

### Post by Jarn on 2007-04-16
You could try copying all the files from all the disks off the disks into a folder and then running the setup from that folder. I don't know about this specific instance, but I know that can help with problems installing off discs quite often.

---

