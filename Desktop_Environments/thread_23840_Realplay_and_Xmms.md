---
title: "Realplay and Xmms"
date: 2005-04-04
forum: Desktop Environments
---

### Post by wxm505 on 2005-04-04
I upgraded warty to hoary today. Some problems happend.
First Xmms doesn't work. I can open it and choose the 
music directory.But when I push the play button it crashed
and I had to kill the process.

For the realyplay , I can not open it at all. I typied in realplay
in terminal it did not pop up , I typed in ps -aux to check the
process. It was invoked. So confused.

The strange thing is both xine and totem worked very well
as before

any help??

---

### Post by astoltz on 2005-04-04
No help with the Realplayer problem, but for XMMS, try setting the output to Esound.  It's located somewhere in XMMS options dialog - sorry I can't be more specific but I'm not sitting at my Ubuntu machine right now.

I had the same issue and the change to Esound solved it.

---

### Post by wxm505 on 2005-04-04
Great!! It is very helpful. Problem had been solved !. Cheers mate.
The realplay problem is really annoying.
I tried several ways. I can run it at the moment. I mean
I can open the GUI window but can not play anything...
no idea where the problem is

---

### Post by jameswilhelm on 2005-04-04
It sounds like some audio problem with Realplayer. Realplayer for Linux refuses to run unless the audio is working or not being used by another program. Does the sound system change between Warty and Hoary? Could it have something to do with esd running? On my PC Realplayer will come up, but then just sit there if some other program is using audio. Can't even play video-only clips.

---

### Post by wxm505 on 2005-04-04
The problem is that I followed two paths to solve this problem.
First I removed two Swf files in the /opt/realplay/plugin.
Then I run realplay , it pop up but when I play a .rmvb file it 
crashed. I had to force quite it.
Second I change the esd setting in /etc/esound/esd.config
I set auto-span=1.
realplay can pop up either but the same thing happend.
When I play a rmvb file it cashed .
So I do not know how to fix it.
any help??

---

### Post by ericj on 2005-04-04
Realplayer seems to hang until  unless the  System>Preferences>Sound

start sound server at startup checkbox is unchecked.   This, however, seems to kill the esd sound apps.   An unhappy circumstance.

---

### Post by wxm505 on 2005-04-04
haha, I made it work anyway
by changing the esd.config.
Firstly change auto-span=1
then reboot it.It works now.
Thank all the friends who gave me so much
help!!

---

### Post by jameswilhelm on 2005-04-04
Perhaps you can make up a script for each sound app that first starts esd? Then create a launcher for each script. A workaround I don't like - not a good way to sell Linux to people!

---

### Post by shof2k on 2005-04-04
I found that Realplayer 10.3 doesn't seem to work for me, but 10.2 with the previous hints.  

Running I-Friend laptop Celeron 2.0Ghz, 512MB ram, Dual boot with XP, Intel 810 motherboard.

Btw: This is my first post in ubuntu :), so excuse the noobie-ness.  After 6 months of reading the forums I have decided to contribute.

---

