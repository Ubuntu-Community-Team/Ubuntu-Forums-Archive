---
title: "why is XFCE so unstable"
date: 2007-07-24
forum: Desktop Environments
---

### Post by AceofSpades19 on 2007-07-24
Why is xfce so unstable in ubuntu, it runs slower then gnome and the top and bottom bars have disapeared on me for the umpteenth time, anyone else having this problem?

---

### Post by kerry_s on 2007-07-24
sounds like a screwed up install, did you check the disk?

i always found the debian version faster.
[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

---

### Post by ugm6hr on 2007-07-24
> **AceofSpades19 said:**
> Why is xfce so unstable in ubuntu, it runs slower then gnome and the top and bottom bars have disapeared on me for the umpteenth time, anyone else having this problem?

My panels disappeared too, but as long as I leave the Save session.... box ticked when I Quit, it seems to be OK.

Otherwise, *xfce4-panel* needs to be added to autostarted applications.

It's slower than GNOME? Really?  I use it cos I started on a more basic laptop, but like it so much I use it on my new system too.

---

### Post by dannyboy79 on 2007-07-24
> **ugm6hr said:**
> My panels disappeared too, but as long as I leave the Save session.... box ticked when I Quit, it seems to be OK.

Otherwise, *xfce4-panel* needs to be added to autostarted applications.

It's slower than GNOME? Really?  I use it cos I started on a more basic laptop, but like it so much I use it on my new system too.

I am using Xubuntu Feisty on my older Hitachi Laptop (266mhz Pentium MMX, 128mb ram, Neographic Graphics Card), I can't seem to get Audacity to record anything?? I have even compiled and installed Alsa per this [http://ubuntuforums.org/showthread.php?t=451586&page=2](http://ubuntuforums.org/showthread.php?t=451586&page=2), I have checked my alsamixer capture settings and all. Still no go. I have a MIC, Line-In, Line-Out on my laptop. What's weird is that the sound from my turn-tables is actually coming thru the Laptop speakers, not sure why? Any suggestion or have you never tried to record audio input before?

And I have heard about sound-recorder but it's only a command line program in Xubuntu?

---

### Post by crimesaucer on 2007-07-24
> **ugm6hr said:**
> My panels disappeared too, but as long as I leave the Save session.... box ticked when I Quit, it seems to be OK.

Otherwise, *xfce4-panel* needs to be added to autostarted applications.

It's slower than GNOME? Really?  I use it cos I started on a more basic laptop, but like it so much I use it on my new system too.


I have save system checked also, but I think the proper command is "xfce4-panel &"...with the "&" sign it keeps the process of xfce4-panel running.


I have only used ubuntu once or twice and I though my xubuntu was WAY faster...and my low end hp pavilion laptop is from 2005/06.


What I like about xubuntu, is the way the menu's and the file system is...and how fast it is. I have noticed some programs just don't work for me though...like banshee never worked for me, or VLC...but I always thought it had to do with Beryl or Conky.

---

### Post by ugm6hr on 2007-07-24
> **crimesaucer said:**
> I have noticed some programs just don't work for me though...like banshee never worked for me, or VLC...but I always thought it had to do with Beryl or Conky.

Must be something to do with your setup, since I use Banshee and VLC as my preferred multimedia apps in Xubuntu.

I like the thunar integration most about Xubuntu.

---

### Post by bapoumba on 2007-07-24
I have to admit that after running Xfce on an old, second hand, laptop, I am also running it on my regular laptop and dektop (which used to run GNOME).
How did you install it ?

---

### Post by dannyboy79 on 2007-07-24
I understand that my question may be off topic but can't anyone comment that they have successfully recorded audio within Xubuntu? THere's a thread below that I would appreciate any feedback on. thank you.

[http://ubuntuforums.org/showthread.php?t=451586](http://ubuntuforums.org/showthread.php?t=451586)

---

### Post by bapoumba on 2007-07-24
@ dannyboy79: I have never tested this, but I know a couple of persons much into multimedia stuff. I'll ask them about the thread you mentioned.

---

### Post by ugm6hr on 2007-07-24
> **bapoumba said:**
> How did you install it ?
Xubuntu7.04 LiveCD for both laptops.  It actually replaced PuppyLinux on the old machine when I upgraded from 128MB to 256MB RAM.

Only thing I don't like is the lack of decent GUI wifi control - fixed that with Wicd easily though :)  I believe that Adam (wicd developer) is currently trying to package Wicd for the repos, and perhaps the Xubuntu developers will see the need for a default wifi GUI and include it in a future release!  Had another thought - thunar's (Xubuntu's) only downfall is no default search function, but catfish fixed that too (with easy thunar right-click integration).

---

### Post by ugm6hr on 2007-07-24
> **dannyboy79 said:**
> I understand that my question may be off topic but can't anyone comment that they have successfully recorded audio within Xubuntu? THere's a thread below that I would appreciate any feedback on. thank you.

[http://ubuntuforums.org/showthread.php?t=451586](http://ubuntuforums.org/showthread.php?t=451586)

I'm afraid that thread's too complicated for me.  

But I can confirm that it is not Xubuntu that is causing your problems.  I installed Audacity when I thought my microphone wasn't working, but it didn't help.  I managed to get the microphone issue solved (the main issues were amixer capture and alsamixer input selection/volumes/unmuting):
[http://ubuntuforums.org/showthread.php?t=506515](http://ubuntuforums.org/showthread.php?t=506515)

So I just checked in Audacity - and it records from the microphone perfectly now.  Sorry if that doesn't help you...

---

### Post by crimesaucer on 2007-07-24
> **ugm6hr said:**
> Must be something to do with your setup, since I use Banshee and VLC as my preferred multimedia apps in Xubuntu.

I like the thunar integration most about Xubuntu.

I don't believe VLC had a problem with xfwm4 and xubuntu, because it worked when I turned Beryl and Conky off.

But when I turned Conky and Beryl back on, it would flicker out to a black screen...so I went back to Xine-ui which I never had problems with when using Beryl and now Compiz Fusion...

...as for banshee, it would crash every time I loaded it (again it was back when Beryl was pretty new), so I just used Listen, then Audacious, and the I found Exaile!, which I still use and like the best out of any music player I've ever used.


And I also love Thunar and it's Configure custom actions....and the plug-in for editing music tags rules.


As for a wifi GUI, I found WiFi Radar to work nicely: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

---

### Post by dannyboy79 on 2007-07-25
> **ugm6hr said:**
> I'm afraid that thread's too complicated for me.  

But I can confirm that it is not Xubuntu that is causing your problems.  I installed Audacity when I thought my microphone wasn't working, but it didn't help.  I managed to get the microphone issue solved (the main issues were amixer capture and alsamixer input selection/volumes/unmuting):
[http://ubuntuforums.org/showthread.php?t=506515](http://ubuntuforums.org/showthread.php?t=506515)

So I just checked in Audacity - and it records from the microphone perfectly now.  Sorry if that doesn't help you...

thank you, so you're saying that you didn't need to compile and install alsa 1.0.14? All you did was verify the amixer capture and alsamixer input selection/volums/unmuting? Can you maybe provide screen shots of your alsamixer settings at imageshack.org and provide me the links please? i would really appreciate that, I have been trying to get this to work for the last 3 months. Are you using Gutsy, Feisty or which version?

---

### Post by ugm6hr on 2007-07-25
> **dannyboy79 said:**
> thank you, so you're saying that you didn't need to compile and install alsa 1.0.14? All you did was verify the amixer capture and alsamixer input selection/volums/unmuting? Can you maybe provide screen shots of your alsamixer settings at imageshack.org and provide me the links please? i would really appreciate that, I have been trying to get this to work for the last 3 months. Are you using Gutsy, Feisty or which version?

I use Xubuntu7.04 (Feisty) with original kernel (2.6.20-15 I think), since the update broke my alsa (so I reverted to original).  This is a known issue with Acer Aspire 5050.

I did not compile alsa - it is pre-installed with (X)Ubuntu (uncertain which version).

The problem was that I couldn't change the capture settings from alsamixer - I had to do it with amixer Terminal commands (see my other linked post).  As for alsamixer settings - they are not that diffenet to the screenshots given in the linked post too, but I have edited them to re-mute unnecessary channels.  I have linked them below again.  

Please note that on my laptop, "Surround" are the main laptop speakers, "Front" is the headphone socket, and "Front Mic" is the plug-in microphone (which I have recorded from).

The important alsamixer setting for recording was to change the "Input Source" to "Front Mic", and for amixer:
```
amixer sset Capture 31
amixer sset Capture cap
```

---

### Post by samjam on 2007-08-01
Thanks!

Those two commands solved it for me on my Acer 9301.
I can't get the internal mic to work on windows vista, but I can on linux now.

Thanks
Sam

---

### Post by ugm6hr on 2007-08-01
> **samjam said:**
> Thanks!

Those two commands solved it for me on my Acer 9301.
I can't get the internal mic to work on windows vista, but I can on linux now.


Ubuntu 1, Vista 0 :popcorn:

---

