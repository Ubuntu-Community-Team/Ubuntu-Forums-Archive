---
title: "Quake3 sound woes"
date: 2007-05-12
forum: Gaming &amp; Leisure
---

### Post by MikeReiner on 2007-05-12
The console says it can't map /dev/dsp, so I made it writable with 
chmod o+rw /dev/dsp

no change.

So I followed another guide to make quake3 look for /dev/dsp1 instead, so i added..
seta snddevice "/dev/dsp1" in the q3config.cfg file, but that didn't work either.

any thoughts? The game runs good.. 100 fps maxed settings.

Realtek ALC50 (AC97) ALSA
NVidia CK804 OSS

---

### Post by aidanr on 2007-05-12
> **MikeReiner said:**
> but it wants me to add..
seta snddevice "/dev/dsp1" in a q3config.cfg file in /quake3/baseq3.. but that file doesn't exist.

that file is at ~/.q3a/baseq3/q3config.cfg that's a hidden folder in your home folder (ctrl+h)

---

### Post by MikeReiner on 2007-05-12
> **MikeReiner said:**
> The console says it can't map /dev/dsp, so I made it writable with 
chmod o+rw /dev/dsp

no change.

So I followed another guide to make quake3 look for /dev/dsp1 instead, so i added..
seta snddevice "/dev/dsp1" in the q3config.cfg file, but that didn't work either.

any thoughts? The game runs good.. 100 fps maxed settings.

> **aidanr said:**
> that file is at ~/.q3a/baseq3/q3config.cfg that's a hidden folder in your home folder (ctrl+h)

Yeah... i just realized that.. didn't fix the problem though.. it just then says:
um- can't GETOSPACE? or something.. weird.

---

### Post by MikeReiner on 2007-05-13
bump.

---

### Post by Nehvrook on 2007-05-13
There are a lot of people having this problem (Including me)

People have suggested a lot of fixes in this thread [http://ubuntuforums.org/showthread.php?t=427435&highlight=Quake+sound](http://ubuntuforums.org/showthread.php?t=427435&highlight=Quake+sound)

But still none of these have helped me. 
Another place that might be helpful to you is
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3&back=HOWTO+INDEX+Linux+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3&back=HOWTO+INDEX+Linux+Games)

EDIT, scratch that. By typing in both of these commands one after the other into the root terminal

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

I have sound working in Quake 3

Edit again: That only gives sound in the menu, as soon as I boot up a map it crashes. :(



EDIT for a third time:

I have it working properly now. Here's how I did it

Go to wherever you installed Quake III (For me this was /home/lee/ProgramFiles/Quake3) and in that folder find the baseq3 folder. Inside there will be a bunch of archive files. Using the archive manager (comes with Ubuntu) open the one called pak0.pk3 (You'll have to change the permissions to let you read and write to this file) and find the music and hit delete. (I made a backup of pak0.pk3 (Just copy it somewhere else on your hard drive in a folder called backup or something) just incase)
Once you've deleted the music close the archive manager and go to the root terminal. In the root terminal type in
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
hit enter then type in
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
and hit enter
Then point the terminal at your quake 3 file (For me this was /home/lee/ProgramFiles/Quake3/quake3) and it will launch the game with sound and it shouldn't crash when you load maps

---

### Post by MikeReiner on 2007-05-13
ahhh!!
I did it once.. and the sound worked... but after closing the game.. sound doesn't work anywhere else now.. and now not even quake3.. i have no sound.. how do I undo these commands??
Edit: nvm restarting fixed it.

edit: the first time i did those commands the sound worked.. but not after a restart.. so i tried the commands again.. and now it doesn't work still. Uhg.

---

### Post by MikeReiner on 2007-05-14
come on guys.. there has got to be some other option..

---

### Post by Nehvrook on 2007-05-14
The solution I posted above works for me, other than that I doin't really know what to suggest.
I had problems with sound in Starcraft, and I fixed those by going to System>Preferences>Multimedia System Selector and changing my output and input to OSS instead of ALSA. I'm not sure if that will work for you but it's easy to change back so it's worth a try right?
(You might have to do System>Preferences>Main Menu and tick Multimedia System Selector to make it show up in the menu)

---

### Post by MikeReiner on 2007-05-14
Well my primary issue with your fix is that if I can't play on PB servers.. it's really not worth playing..

---

### Post by Nehvrook on 2007-05-14
I see, I mostly just play single player and LAN games myself see.
Well I have no idea if it'll work or not, but instead of deleting the music folder you could just replace the files with dummy files of the same name. That might prevent the crash still but make PB believe it's not edited and let you play. Though I'm just guessing here. Sorry I can't be more help

---

### Post by MikeReiner on 2007-05-15
Thanks, but it would know that the file size is different and kick me for not being 'pure'.. oh well.

edit: well I've given up on this for a while. For now, I'm gonna run the windows version of Q3 through wine.. the performance is nearly as good and the sounds work without flaw. Not to mention PB.

---

