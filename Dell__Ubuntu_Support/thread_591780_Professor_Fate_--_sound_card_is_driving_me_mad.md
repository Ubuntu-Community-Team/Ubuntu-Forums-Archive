---
title: "Professor Fate -- sound card is driving me mad"
date: 2007-10-25
forum: Dell  Ubuntu Support
---

### Post by professor fate on 2007-10-25
OK, I've been fiddling with this sound card for quite some time now, and have made no progress.  What am I doing wrong?

results of lspci info:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

input the following terminal commands:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

installed the following from synaptic package manager:
alsaplayer-common

this actually installed a couple of other associated packages.

if i go to system > pref > sound and select the test buttons i get the following:
audiotestsrc wave=sine freq=512 ! 
audioconvert ! audioresample ! 
gconfaudiosink profile=music: 
Could not open resource for writing.

---

### Post by Bushwack on 2007-10-25
Try the methods on this page: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

I used Method G and it worked perfectly for me.

---

### Post by professor fate on 2007-10-25
Thanks.  It says to....

In the editor, add the following line at the end of the file:

 options snd-hda-intel model=dell-m42


Question: what file am I editing and where can it be found?
Also, you did this to a Vostro 1400?  It says in the liner notes that it doesn't work for 1400s.  Just curious.

---

### Post by Bushwack on 2007-10-25
According to the page you only need to do that if you have a Dell Latitude D630 or D830.  As I don't have one of those I skipped that step and everything worked fine.  If you need to edit the file though:

> 
 sudo gedit /etc/modprobe.d/alsa-base

In the editor, add the following line at the end of the file:

 options snd-hda-intel model=dell-m42


"The editor" here is the program "gedit" which is launched using the first command.  Using any text editor as root will work, the file to edit would be /etc/modprobe.d/alsa-base

---

### Post by professor fate on 2007-10-25
OK, I tried it w/and w/o the edited text file, and still nothing.  I have a mute symbol over the speaker, and when I click on it it says that I have no sound control or GStreamer installed.  I've got a lot of that though.  Here's a pic.

---

### Post by Bushwack on 2007-10-26
I see that you have a vostro 1400.  According to those instructions that method doesn't work with a vostro 1400, I'm not sure why that would be as it worked perfectly with my vostro 1700 and I can't see the hardware being that different.

I would read that page and see if any of the other methods are working with the vostro 1400 and try them out.

---

### Post by Martje_001 on 2007-10-27
Professor Fate,
Try to contact Dell.

---

