---
title: "Resolved WOW stutter on radeon 9800 by turning off fast writes"
date: 2007-06-15
forum: Gaming &amp; Leisure
---

### Post by MikeEvans on 2007-06-15
OS: Feisty
CPU: athlon xp 1700
Mobo: Nforce 2  w/ > 1 gig ram
sound: soundblaster audigy ls
video: ati radeon AIOW 9800 on ATI drivers 8.36.5 installed with envy
Wine installed from add/remove
Sources:
[INDENT][http://www.rage3d.com/board/showthread.php?t=33793288]("http://www.rage3d.com/board/showthread.php?t=33793288")
[http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine")[/INDENT]

I install world of warcraft by following the guide over at wow wiki.  Once in the game I noticed heavy distortion in the sound, slow loading of characters (they are invisible for about 15 seconds after logging in), a 2 second stutters occurring every 10 seconds. The stutters where accompanied by cracking distortions in the sound.  In between these problems the game was running smooth.  Since I have some sound issues in all my 3d games I thought it was a problem with my sound driver but I was able to resolve everything yesterday by turning off fast writes in my X configuration file.  This is something I had to do in windows but just didn't know how in linux.  This is how I did it.

This may only work on the radeon 9xxx series of cards but I'm note sure about that. [ First follow the guide on the WOW wiki]("http://www.wowwiki.com/Linux/Wine").  You need the ATI driver installed, your sound buffers increased, and wow told to run in OpenGL mode instead of D3D.  If you just did this reboot your system before continuing. 

Next we check if fast writes is on or off.  Look in your system logs, in the' messages log' search for "AgpCommand "  You should see an entry logged last time your system booted that looks like this:
```
[fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
```
The second to last number in that hex code (in this case the zero between the three and the two) represents the status of your fast writes.  one = on and zero = off.  Only continue if that value is 1(on).  We are going to set it to zero (off).  

Open up your X configuration file
```
sudo gedit /etc/X11/xorg.conf
```

Add the following lines to the 'Device' section:
```
Option  "AGPMask"	"0x00000010"
Option  "AGPv3Mask"  "0x00000010"
```
***WARNING: this is a sensitive file.  If you make a mistake here X will not start on your next boot.  You may want to make a backup copy of xorg.conf and know how to restore it if that happens.***

Save the file and reboot your computer.  When it comes back up you need to check your system logs again to see if that bit changed to a zero, indicating that fast writes are now off.  Finally, try running WOW.  

I saw a immediate and dramatic improvement.  WOW is now running at least as good as it did in windows for me.
:D

---

