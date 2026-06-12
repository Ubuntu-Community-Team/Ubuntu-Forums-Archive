---
title: "SLOW Xubuntu vs. Windows MC Install &amp; etc."
date: 2006-08-05
forum: Desktop Environments
---

### Post by ketnoe on 2006-08-05
Ok, this may end up being long.  I'm not a complete Newbie to Unix/Linux; but have kept from using it in the past due to time contraints on setting up exactly what I need / software compatabilitiy etc.

On to the problem:
System Specs:
Compaq ARMADA <sp> laptop, old 500mhz w 512ram 40g HD.  External 500GIG Networked HD (fat32).
What I wanna do with it:
MEDIA Player Box; i.e. I want to MAINLY control music through this box, using my SNAPSTREAM remote, with ocassional uses for streaming SCRUBS, or SEINFELD. -- thats it.  I was doing this with Windows Media Center (although I just used Winamp for all the above -- not the actual WMC gui)

Installed a second partition w GRUB, and Initially UBUNTU; the first install was great, I didnt try to customize anything; I then decided to try KUBUNTU, another easy install.  I overwrote the UBUNTU install so in the same partition.  It was just a little slow running on a 500mhz, w all the eyecandy.  I finally decided to go with XUBUNTU.  I wanted something fast I didnt have to mess with when I finished customizing.

The XUBUNTU install went well, just as easy; Now the problems begin.  I was initially impressed by Amarok, although It was running a little faster in XUBUNTU vs. KU, I ditched it due to LONG LONG LONG load times; just to list my folders.  I tried SAMBA, SMB4FS, CIFS was fastest (got that from another post in here), but finally running XSMBROWSER to mount my Network HD; still had to ditch Amarok.  Using XMMS, I can play without problems now, however, still does hang once in a while, If I try to import a large playlist.  And I CANNOT use the FILE ADD options using XMMSs playlist if I dont want to wait 5 hrs.  So I have to add music using THUNAR (drag and drop).  -- 

SnapStream -- BI**H to setup, I just got impatient and dropped the whole thing, I used LIRC, had to do it from scratch w RECORD, no patients for this; there isn't one config file out there!! so no remote -- strike 2

Streaming, havent even gotten to the SHOUTCAST issue.  Now I realize it takes more processor power/memory to decode RMVB files, but RealPlayer 10 should not be faster than MPLAYER.  oh, and Realplayer 10 ONLY runs faster than MPLAYER, if you set the option to BUFFER/CACHE entire CLIP.   --- I downloaded the NEWEST MPLAYER pre version, ./configured it, maked it <hehe> and installed it. -- never been on a flight so choppy w the sound running faster and faster over the horizon.. --ditched for now.  
strike 3... 

annoyed.  I havent installed anything extra in XUBUNTU, the BASE install is FASTER than WINDOWS is on my OLD ARZ system! thats great!, but what am I doing wrong regarding my media setup?

Can anyone help with my media setup?? -- 
-I would love to get SNAPSTREAM / Firefly functional!
-use ANY media player to play my MP3 collection w/o freezes
-stream, or play video files, not necessarily rmvb CLEAN.

- if possible, a simple method of doind a "Remote Desktop Connection" like in XP, to login to the current running session and change i.e. add to playlist from a remote PC.. 

- pretty much what I was doing w XP on the 500mhz laptop -- w 0-20mins setup.

--- i can take it if its not possible. I am already planning on dual booting my daily desktop which has more than adequate hardware to run anything for the next 2 years at least.. lol.. 

- ketnoe.

---

### Post by jonboy99 on 2006-08-05
Sorry, nothing to do with your problem, but how much quicker was xubuntu compared to ubuntu?

My laptop is near identical spec to yours, and rather sluggish with  ubuntu.  I'm wondering if it's worth the hassle of  installing xubuntu.

How does xubuntu compare to XP for day to day tasks, speedwise?

Cheers and sorry for spam.

---

### Post by ketnoe on 2006-08-05
Vs. Ubuntu, Xubuntu was slightly faster, but compared to Kubuntu it was WAY faster.  Kubuntu ran at about the speed of windows XP on my system, Windows might have actually ran a little faster.   Unless you get to MEDIA stuff again, Windows was faster than all 3!  accessing the files, playing the files, and no errors. 

--- honestly the only benefit / thing I loved about U(Xu) vs. XP was the fast bootup, core stability, and LOVED LOVED the terminal, command line..  

-- have hated so far, probably due to a bad setup -- i dunno -- slow file access times/specifically off my NFS, MEDIA ACCESS! anytype!!

I havent tried UbuntuLite yet, I wonder how that compares to Xubuntu.  

If you wanna try them out yourself, burn each on CD and just boot up with it; it wont install anything and you can test out the speeds.

---

### Post by lagartoflojo on 2006-08-07
> burn each on CD and just boot up with it; it wont install anything and **you can test out the speeds**.
The speed you will get from running Ubuntu as a live cd (ie. without installing it to the hard drive) will be very low compared to when it is installed, as everything (every program you try to run) will be read from the CD, a process that is much, much slower than reading from the hard drive.

---

