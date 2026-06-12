---
title: "Help with TacOps:Crossfire"
date: 2008-10-14
forum: Gaming &amp; Leisure
---

### Post by adamovera on 2008-10-14
I've installed UT2004 in /home/adam/games/ut2004 by clicking the installer on the dvd. I've installed the megapack & linux patch version 3369.2 by moving them into /home/adam/games/ut2004. I edited the ut2004 file to reflect the amd64-bin. UT2004 works great no problems. I installed TOCrossfire 1.9a full by clicking the installer & changing the UT2004 directory to /home/adam/games/ut2004. When I try to play TO it will display the TO splash screen & then take me to UT2004. I've tried this with the launcher for TO in home & from terminal by doing ut2004 -MOD=TOCrossfire. I've added the -log=TOCrossfire. I've tried all kinds of caps & no caps variants. Totally outta clues. Please Help, this is like day 5 now for me.

---

### Post by Perfect Storm on 2008-10-14
[http://gaming.gwos.org/doku.php/guides:64bit:tactical_ops_crossfire](http://gaming.gwos.org/doku.php/guides:64bit:tactical_ops_crossfire) might help you. Note it aaassume that you have installed globally.
If you change the the patch to yours etc. and don't use sudo.

---

### Post by adamovera on 2008-10-14
I've since found the guide & followed it to the letter. I'm using the latest TO version 1.9a. I had to change the instances where the version number was different & had to make the install.sh an executable, but everything else is the same. The link in menu/games doesn't work at all & the terminal command brings up Ut2004, no TO splash screen this time. I've found that if you add the -log command the splash will not show. So basically I've installed as user by GUI & then installed as sudo in terminal, both ways have the same problem Ut2004 plays but not TO. BTW I'm using a fresh install of 8.04. I've gotten this to work before with 8.04 x64 but with the older version of TO, I think 1.8. Any ideas?

---

### Post by adamovera on 2008-10-14
Note: when TO 1.8 was working there was a strange problem, when you kill an enemy they didn't fall down, they just stopped moving & stayed standing and pointing the gun like they are still alive. I'd be happy to just reinstall 1.8 to try to fix that problem but since it's an old version that make online play impossible.

PS: I just tried removing the -log & the TO splash screen came back but still launched into regular UT2004.
I'm going to look for a simpler UT2004 mod & see if any of them will work or just launch UT2004. I think we can rule out a permission problem, of a problem with UT2004 itself so I'm thinking it's something to do with the mod launcher links.

---

### Post by adamovera on 2008-10-14
Sorry to triple post, but I just saw this in the terminal:

open /dev/[sound/]dsp: Device or resource busy

Could this be stopping the mod from initiating?!?

---

### Post by Perfect Storm on 2008-10-14
Going to test it again (both UT2004 and TO), though on 8.10 and globally.

---

### Post by Perfect Storm on 2008-10-14
> **adamovera said:**
> Sorry to triple post, but I just saw this in the terminal:

open /dev/[sound/]dsp: Device or resource busy

Could this be stopping the mod from initiating?!?

Do you have any other using audio in the background? You could try kill(restart) the pulseaudio.

---

### Post by adamovera on 2008-10-14
I just restarted & the sound is back & the message is gone but still loads into regular UT2004. When I run the /usr/local/games/ install from the terminal I get this message after UT2004 loads & I exit out: 

WARNING: ALC_EXT_capture is subject to change!

No idea what that means, but once again if I remove the -log command I get the splash screen at least.

---

### Post by Perfect Storm on 2008-10-14
nwm

---

### Post by Perfect Storm on 2008-10-14
Try;

```
sudo modprobe snd_pcm_oss
ut2004 +set s_driver oss
```

---

### Post by adamovera on 2008-10-14
This is what I got when I put in your code:

Failed to enter +set: Can't find file '+set'

History: 

Exiting due to error

The game tried to start then closed & sent the above message.

The sound is functioning, I looked up that WARNING message on other posts & it is to do with audio capture support & is really more like a NOTICE. Since sound is working it's not the problem.

---

### Post by Perfect Storm on 2008-10-14
Found this, might be helpful;

[http://www.linuxquestions.org/questions/linux-games-33/no-sound-in-games-459872/](http://www.linuxquestions.org/questions/linux-games-33/no-sound-in-games-459872/)

> The sound is functioning, I looked up that WARNING message on other posts & it is to do with audio capture support & is really more like a NOTICE. Since sound is working it's not the problem.

AFAIK, it's still audio related.

---

### Post by adamovera on 2008-10-14
Yeah, that's the post that I found, It appears to be related to mic not speakers. I had alot of apps open & did alot of stuff before when the sound didn't work, a reboot fixed it and I've run UT2k4 alot since & there is still sound. It's got to be something to do with the installation of TO & not UT, specifically the linkage to the TO mod. Something must have changed from TO 1.8 to 1.9. This is one of those things that's probably going to come down to a capitalization error in the links.

---

### Post by Perfect Storm on 2008-10-14
> **adamovera said:**
> Yeah, that's the post that I found, It appears to be related to mic not speakers. I had alot of apps open & did alot of stuff before when the sound didn't work, a reboot fixed it and I've run UT2k4 alot since & there is still sound. It's got to be something to do with the installation of TO & not UT, specifically the linkage to the TO mod. Something must have changed from TO 1.8 to 1.9. This is one of those things that's probably going to come down to a capitalization error in the links.

okay.

I'll report back when it's installed etc.

---

### Post by adamovera on 2008-10-14
The ALSA/OSS issues where a problem in the wine install, not the native one, but yeah switching to OSS fixed the no-sound issues for UT & TO under wine. native never had a problem. I think my install of VLC sometimes doesn't like firefox or java or maybe flash & kills audio on occasion. A reboot or at least a login/logout always fixes it though.

---

### Post by Perfect Storm on 2008-10-14
Ok, I have now tested both guides (and both games). On my PC it works. So I don't know what the issue can be.

[http://gaming.gwos.org/doku.php/guides:64bit](http://gaming.gwos.org/doku.php/guides:64bit)

I made some few changes, but only vers. number etc.

---

### Post by adamovera on 2008-10-14
Are you using 8.04 x64? I've reformatted & put on a fresh install maybe 3 days ago, so my system is pretty clean. I need to format my girlfriend's computer & put ubuntu x32 on it (she has mandy 2008.1 right now & I waited for 2009, but I don't like it very much so she'll get ubuntu this time). I'll also redo my system again for 8.10 x64 when the final comes out. If the x32 works & the x64 doesn't I'm pretty sure it's got to be something with the linkage. I'll remove my installs of UT & TO and try again both using the guide & GUI as user one more time, but I'll wait for the new version before I reformat again.

PS - Since I have a pretty fresh install, do you know of any packages that I'd need other than libgtk1.2 that might be holding TO back?

---

### Post by Perfect Storm on 2008-10-15
No, I have the standard ia32libs installed.

---

