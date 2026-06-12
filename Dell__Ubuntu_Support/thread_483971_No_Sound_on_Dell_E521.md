---
title: "No Sound on Dell E521"
date: 2007-06-25
forum: Dell  Ubuntu Support
---

### Post by Jkane13 on 2007-06-25
I bought a new E521 with dual core Athelon a few weeks ago.  Vista really is a horrible performer.  Worse than I ever imagined!  Tried to run Ubuntu in a VMWare session, and it seemed to work, but the network only worked the first two times I booted it.  After a while, I gave up and re-partitioned and made Ubuntu my main O/S and am running Vista in a VMWare session under it.

It took me a couple days, but finally found a set of sync numbers that made the 20" flat panel screen work right.  Very sweet now!  I really like the bigger and sharper monitor.  Now if I could see more than just jpg's on it.  Any attempt to run a mpg just hangs.  :-(

I am having problems getting any video (mpg)  or audio (mp3) to work.  I suspect it's more the audio, and not the video that is hanging.  This is because even adjusting the audio properties gives no sound out.  Funny enough, the Vista install in VMWare has sound!  Only 2 channels, but that's good enough for it.

Any ideas what's happening?  I normally use KDE, but am going with the default Gnome this time.  Maybe it has something to do with Gnome? Oh yeah, this is 64 bit Feisty Fawn current stable release that I downloaded and installed after burning a CD (using Vista just to make it ironic.)  Not in front of it now to give exact version number.  Sorry.

Any ideas or suggestions would be appreciated.

---

### Post by magicfab on 2007-06-28
For MP3, see: [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)
For MPG, not sure, maybe you have the wrong video driver. Can you post the content of your /etc/X11/xorg.conf file ?

---

### Post by seekers on 2007-06-29
I also have a E521.  However I am using the 32 bit version of Feisty fawn.  I am not having any problems with sound.   It works sweet.   [ 1930.764000] Buffer I/O error on device sr0, logical block 9  this is the only problem I am having with my E521 but it still burns my music and stuff.  So it works.   I have to agree that Vista is slow as a cow even with 3 gigs of ram.   I was quite disappointed.  Feisty is very fast indeed.  So you reload with the SYSTEM restore cd in a VMWARE?

---

### Post by Jkane13 on 2007-07-09
Sorry, been out for a while.  Need to get back to figuring this one out.  Haven't tried anythign new yet.

Yes, I used the Dell restore CD and reinstalled Vista in a VMWare session.  Haven't tried to license it yet.  Hope that works when the 30 days ends.  That should be very soon.  However, I really haven't had to use that session since the install.  ;-P

---

### Post by Zeratul7 on 2007-07-09
Just in case I mention that there are more than one place to turn off Your sound. Make sure You have both channels (Master and PCM) maximized. You can see different channels by choosing Edit -> Preferences from volume control.
It sounds really stupid, but I have had the same problem once when after a fresh install one of the channels was minimized and it took me quite a lot of time to figure it out :)

---

### Post by jtltgl on 2008-07-15
I had no sound just modprobe snd CRTL ALT BACKSPACE then just under system preferences Sound. Chick on Sound TAB test by clicking play log in.
Hope that helps.

---

### Post by jtltgl on 2008-07-15
Sorry forgot step here are the steps :

sudo modprobe snd
crtl alt backspace
check sound under system preference Sound
click on sounds tab play log in
sudo gedit /etc/modules add snd at end

---

