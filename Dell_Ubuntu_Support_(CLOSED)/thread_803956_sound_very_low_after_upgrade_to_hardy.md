---
title: "sound very low after upgrade to hardy"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wjhildreth on 2008-05-22
Hello all,

We done a distribution upgrade to hardy a couple of days ago. Most things seem to work fine and the video card on our 1420n is now removed from the blacklist. But, there is a problem with the sound. Audio works but there seems to be very little volume, where before on Gutsy, the machine was actually quite loud. I looked at Dell's site and the only thing they have is a section on if the sound does not work at all. Any ideas on where to look?

Warm Regards,

Joe Hildreth

---

### Post by xfceuser on 2008-05-22
firstly look if there is no hardware volume that is set to low.
then look at the volume-control-mixer, depending on the sound card there might be many controls that must be checked. sometimes you may not have access to all the controls on the default mixer-control, so you might install gnome-alsa-mixer if not there already, also alsa-mixer-gui and see what controls are there.
if these not help, there may be problem with the sound driver.

---

### Post by wjhildreth on 2008-05-24
Thanks for the tip. I was able to go into the volume control and adjust the "front" volume and that seems to have taken care of it. Thanks for your time.

Regards,

Joe

---

### Post by garrison742 on 2008-05-27
front volume fixed mine also. thanks guys

---

### Post by einfeldt on 2008-06-05
> **xfceuser said:**
> firstly look if there is no hardware volume that is set to low.
then look at the volume-control-mixer, depending on the sound card there might be many controls that must be checked. sometimes you may not have access to all the controls on the default mixer-control, so you might install gnome-alsa-mixer if not there already, also alsa-mixer-gui and see what controls are there.
if these not help, there may be problem with the sound driver.

hi, I am running 32 bit Hardy and the above directions worked for me in solving my low volume problems.  The key is to be sure to get both gnome-alsamixer and alsamixergui and then run the alsamixergui and turn up the volume on PCM and front.  Please note the correct spelling of those two packages, as xfceuser had slightly misspelled them.  Many thanks to xfceuser, as his / her directions worked perfectly! 

In case it is helpful to anyone, I will paste my post from another list where I had asked the same question.  Thanks again, xfceuser!

*****************

I am running 32 bit Hardy (GNOME) on the TeraByte Beast (tbb), but the sound is misbehaving.  It is playing very low, despite the fact that I have turned up the volume on both the applications that are playing sound, as well as the system sound in the upper right had corner.

I have tried running the sound test in System > Preferences > sound, and that works okay for three of the four tests there:  Sound events > Sound playback; Music and Movies > Sound playback; Audio Conferencing > Sound playback; but the test for Audio Conferencing > Sound capture does not work at all.  

For the first three tests, the sound works, but the volume is very low, despite the fact that I have the volume turned up all the way on the sound controller on the upper right hand corner of the top GNOME bar.
 
Sound capture is currently set for ALSA, and the Default Mixer Tracks is set for Realtek ALC885.

Most vexing of all is that the volume sound from the video that I have shot for the Digital Tipping Point film is very low when I open it in Totem, Mplayer, Kino, or VLC. I have tried using a wide variety of video segments in a .dv, .mpg, and .ogg formats.  I have tested these audio clips on another Gutsy system and they work fine.

I am able to play commercial CDs such as KISS's "Love Gun" album, but it also plays at low volume. 

The output of

$ cat /etc/modprobe.d/also-base is here:

[http://pastebin.ca/1039186](http://pastebin.ca/1039186)

The output of cat /proc/asound/version is here:

cje@tbb:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on May 6 2008 for kernel 2.6.24-17-rt (SMP).
cje@tbb:~$

---

### Post by Kronie on 2008-06-05
**xfceuser**
ill just quote wjhildreth's comment istead of writing my own :P
> Thanks for the tip. I was able to go into the volume control and adjust the "front" volume and that seems to have taken care of it. Thanks for your time.

---

### Post by einfeldt on 2008-06-06
> **einfeldt said:**
> hi, I am running 32 bit Hardy and the above directions worked for me in solving my low volume problems.  The key is to be sure to get both gnome-alsamixer and alsamixergui and then run the alsamixergui and turn up the volume on PCM and front.  Please note the correct spelling of those two packages, as xfceuser had slightly misspelled them.  Many thanks to xfceuser, as his / her directions worked perfectly! 

Dang, my issue has returned.  I updated Hardy,and now I can play commercial CDs and YouTube but I cannot play my own footage with either vlc, movie player (Totem), Mplayer, Kino, Kaffeine, or Firefox streaming the footage from the Internet Archive.  When I do attempt to play a video, the sound is once again very low on just my own footage (.ogg and .mpg) under those six movie players.  Here is a sample of the footage that I am talking about.  Left click on the first link on the left under play / download:

[http://www.archive.org/details/e-dv034_01_heather_baker_002.ogg](http://www.archive.org/details/e-dv034_01_heather_baker_002.ogg)

I am able to hear that footage well when I watch that footage on my hard drive under Gutsy or stream it from the Archive under Gutsy, but I am not able to hear it well under Hardy.  The volume is low under Hardy.  

I don't know why the problem has returned.  The problem went away when I updated Hardy once, and then I updated Hardy again (all standard updates) and that is when the problem occurred.  Thanks in advance for any help.

---

