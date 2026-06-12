---
title: "frustrated beyond belief - sound/video"
date: 2006-07-01
forum: Desktop Environments
---

### Post by dmizer on 2006-07-01
how in xfce do i change the default sound mixer to alsa so i can watch flash videos where the sound syncs correctly?

i'm using the totem-gstreamer plugin to watch streaming video ... how do i fix this thing so the video isn't jumpy?

i've had success with mplayer on other installs, but it's buggy at best.  i've tried totem-xine and totem-gstreamer ... neither work correctly.

i'm already completely bald (for real) i don't have any more hair to pull out, and i'm completely sick of browsing through miles of posts for no resolution.  somebody save me.

---

### Post by grooverider on 2006-07-01
u can try vlc from videolan as a player if mplayer is too buggy, if ur soundcard is recognized u can see by doing lspci, it should show up there, then in case u have more soundcards u should be able to do this just by switching via the volume control, at least that's where i can do it.. good luck

---

### Post by dmizer on 2006-07-01
tried vlc earlier ... sound was okay, but no streaming video.

in gnome, you can switch from esd or oss via gui.  but in xfce, there's no gui that allows me to perform this switch.  i can't find any howto's that tell me how to switch the default mixer without using gui.

---

### Post by dmizer on 2006-07-01
mplayer can play the video okay, but it locks firefox at the end.

i also tried mozplugger which plays the video, but it's jumpy.  i'm dyin' here ...

---

### Post by dmizer on 2006-07-01
look, seriously ... i've been at this for literally 2 weeks and i have 0 progress.  mozplugger seems to have been the best answer so far, but it doesn't buffer long enough, so play is jumpy at the start.

could someone tell me how to configure this stuff?

this isn't about a simple inconveniece.  this has to work.  this computer is going to a special needs home and the kids there want to watch their movie trailers.

i'm begging here ...

---

### Post by dmizer on 2006-07-01
anyone? ...

flash locks firefox.
dvd playback blows
mp3 playback won't cycle to the next song automatically
streaming video is jumpy.

come on?  i get 0 multimedia support with xfce?

---

### Post by dolphinholmer on 2006-07-02
Doubt you're about to find any easy answer. Do you really need xfce?

---

### Post by dmizer on 2006-07-08
yeah so ... xfce is necessary because this machine is not fast enough to run gnome or kde.

i got an output from mplayer earlier that indicates my machine simply is not fast enough to play dvd's ... what?  i've played them on laptops that have the same processor.

this box is a 500mhz pIII with 190meg of ram (that's after having ran down to the local spares shop and purchased another 128meg for it).  and just in case ... i've also installed icewm to see if that corrected my issues.  nope. zero change.

and ... in reality, i haven't been what i would consider successful in making any online media function correctly in linux.  not that it's a huge deal for me.  if i really need it, i break out my extra win box and watch the junk.  but in this case, the whole purpose here is for online media.

windows is not the answer because it's not secure enough for these special needs users who neither have nor will ever be capable of developing positive browsing habits. in a linux world, there is always a solution ... someone give me a hand with this ... please?

---

### Post by Orc65 on 2006-07-08
Dmizer, have you checked your hard drive settings?

If not open a terminal and use the "hdparm" commands you can find the documentation on them in the man pages.

Your drive may be running on a low udma setting or may not be using udma at all.

Start with "sudo hdparm /dev/hdx" (x is your hard drive letter, in my case it is "sudo hdparm /dev/hda" 

This will give you a read out something like this: 

robert@wolverine:~$ sudo hdparm /dev/hda
Password:

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 195371568, start = 0
robert@wolverine:~$
robert@wolverine:~$ sudo hdparm -Tt /dev/hda

/dev/hda:
 Timing cached reads:   1860 MB in  2.00 seconds = 929.94 MB/sec
 Timing buffered disk reads:  186 MB in  3.00 seconds =  61.91 MB/sec
robert@wolverine:~$

---

### Post by Orc65 on 2006-07-08
If it's not your hard drive, the only other thing I've found that helps is disable deinterlacing if you have that option under the video settings of your player. I'm using Gxine for video, my vid was jumpy as hell hard drive and deinterlacing worked for me.

---

### Post by Orc65 on 2006-07-08
Another thought have you installedthe following?

"Libdvdcss2" and "w32codecs", You could also just switch ti xine and use the "libxine-extracodecs".

They all appear to be in non standard repos, though so it might pay to have a look here to get the addresses.

[http://www.ubuntuforums.org/showthread.php?t=185758]("http://www.ubuntuforums.org/showthread.php?t=185758")

---

