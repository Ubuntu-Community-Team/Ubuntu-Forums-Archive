---
title: "ZSNES Horrible Sound Quality"
date: 2009-12-05
forum: Gaming &amp; Leisure
---

### Post by Skyline969 on 2009-12-05
Well, normally I know what I'm doing with emulators, but I used ZSNES and the sound will randomly become very horrible when playing a game. For example, even in Bust-A-Move, when I'm playing all of a sudden the background music will become very choppy, and remains that way until I reload the game, and even then sometimes it's bad. The times when it's bad quality are totally random, it seems. What can I do to make quality better? It happens for several games, including Bust-A-Move, Doom, and Super Mario All-Stars & World.

---

### Post by Dark Aspect on 2009-12-05
> **Skyline969 said:**
> Well, normally I know what I'm doing with emulators, but I used ZSNES and the sound will randomly become very horrible when playing a game. For example, even in Bust-A-Move, when I'm playing all of a sudden the background music will become very choppy, and remains that way until I reload the game, and even then sometimes it's bad. The times when it's bad quality are totally random, it seems. What can I do to make quality better? It happens for several games, including Bust-A-Move, Doom, and Super Mario All-Stars & World.

Lower the sampling rate, its a bug in pulse-audio. Mine is at 22050hz and I don't have a problem.

---

### Post by Skyline969 on 2009-12-05
> **Dark Aspect said:**
> Lower the sampling rate, its a bug in pulse-audio. Mine is at 22050hz and I don't have a problem.

I'll try that. What about interpolation and lowpass?

EDIT: I switched to 22050, and Bust-A-Move is still horribly choppy in the sound department. Both interpolation and lowpass are off.

---

### Post by Dark Aspect on 2009-12-05
> **Skyline969 said:**
> I'll try that. What about interpolation and lowpass?

EDIT: I switched to 22050, and Bust-A-Move is still horribly choppy in the sound department. Both interpolation and lowpass are off.

Hm.. Yeah I have had *a few* sound issue even with the lowed sampling rate. Two more suggestions,

#1 Run zsnes in sdl mode

```
zsnes -ad sdl
```

#2 Kill pulseaudio

```
sudo killall pulseaudio
```

---

### Post by CharmyBee on 2009-12-05
You could also try raising the sampling rate to 48000Hz

---

### Post by Skyline969 on 2009-12-05
> **Dark Aspect said:**
> Hm.. Yeah I have had *a few* sound issue even with the lowed sampling rate. Two more suggestions,

#1 Run zsnes in sdl mode

```
zsnes -ad sdl
```

#2 Kill pulseaudio

```
sudo killall pulseaudio
```

Killing pulseaudio seems to have fixed my problem. However, that brings me to a few questions:
1. What is pulseaudio?
2. What does it do?
3. How can I be sure if it's killed or not?
4. If it's not useful for anything, how can I permanently kill it, so it doesn't start when I reboot my computer?

---

### Post by SunnyRabbiera on 2009-12-05
> **Skyline969 said:**
> Killing pulseaudio seems to have fixed my problem. However, that brings me to a few questions:
1. What is pulseaudio?
2. What does it do?
3. How can I be sure if it's killed or not?
4. If it's not useful for anything, how can I permanently kill it, so it doesn't start when I reboot my computer?

1: Pulseaudio is a sound server [http://en.wikipedia.org/wiki/Sound_server](http://en.wikipedia.org/wiki/Sound_server)
2: [http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)
3: actually I dont know this one
4: you could remove pulse but Ubuntu is very dependent on it.
Its sort of why I like openSUSE 11.2 KDE

---

### Post by Dark Aspect on 2009-12-05
> **Skyline969 said:**
> Killing pulseaudio seems to have fixed my problem. However, that brings me to a few questions:
1. What is pulseaudio?
2. What does it do?
3. How can I be sure if it's killed or not?
4. If it's not useful for anything, how can I permanently kill it, so it doesn't start when I reboot my computer?

1. pulseaudio is a sound server and a really bad one at that. It was designed to be able to have sound input from multiple sources but as you know it is riddled with bugs.

2. It allows applications to use audio like any other sound server.

3. You can get a list of background task with the top command:

```
top
```

4. You can permanently delete pulseaudio only if you install another sound server in its place. [Here is a howto]("http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html") that replaces pulseaudio with esd.

---

### Post by Skyline969 on 2009-12-05
> **SunnyRabbiera said:**
> 1: Pulseaudio is a sound server [http://en.wikipedia.org/wiki/Sound_server](http://en.wikipedia.org/wiki/Sound_server)
2: [http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)
3: actually I dont know this one
4: you could remove pulse but Ubuntu is very dependent on it.
Its sort of why I like openSUSE 11.2 KDE

Hm... things seem to run fine even while the pulseaudio service is killed. I saw what would happen if I tried to uninstall it via Synaptic Package Manager, and it said it'd uninstall a lot of stuff, including ubuntu-desktop. Needless to say I cancelled. I wonder... could I edit the launcher on the Games menu in some way, shape, or fashion that it would kill the pulseaudio service before it started ZSNES?

EDIT: Would replacing pulseaudio with ESD fix my ZSNES issue permanently?

---

### Post by Dark Aspect on 2009-12-05
> **Skyline969 said:**
> Hm... things seem to run fine even while the pulseaudio service is killed. I saw what would happen if I tried to uninstall it via Synaptic Package Manager, and it said it'd uninstall a lot of stuff, including ubuntu-desktop. Needless to say I cancelled. I wonder... could I edit the launcher on the Games menu in some way, shape, or fashion that it would kill the pulseaudio service before it started ZSNES?

Ignore that message, ubuntu-desktop doesn't get removed with pulseaudio. Heres a [link]("http://ubuntuforums.org/showthread.php?t=1154608") about that; its just a meta package dummy data if you will.

---

### Post by Dark Aspect on 2009-12-06
> **Skyline969 said:**
> EDIT: Would replacing pulseaudio with ESD fix my ZSNES issue permanently?

Yes,

Edit: Sorry double post

---

### Post by Skyline969 on 2009-12-06
> **Dark Aspect said:**
> Ignore that message, ubuntu-desktop doesn't get removed with pulseaudio. Heres some [link]("http://ubuntuforums.org/showthread.php?t=1154608") about that; its just a meta package dummy data if you will.

Ah, I see. And deleting it won't affect Compiz Fusion, AWN, or anything else I have installed? I'm sorry that I'm asking a million and one questions, but it's better I do things prepared than just blindly go deleting stuff.

And it says replacing pulseaudio with ESD may possibly completely disable sound at all on my computer... that can't happen. Is there a way that I can guarantee that it won't completely disable my sound? Obviously I want to listen to music, hear sound on ZSNES, etc. I can live without the African sounding login/out sounds... I was meaning to disable those anyways. =P

---

### Post by Dark Aspect on 2009-12-06
> **Skyline969 said:**
> Ah, I see. And deleting it won't affect Compiz Fusion, AWN, or anything else I have installed?

uh.....Thats not a good sign, how many packages is it wanting to remove? Ubuntu-desktop is the only safe package to remove, Try this:

```
sudo apt-get remove --purge pulseaudio
```

Alright this is what I get and its safe to press y:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
[B]  libcanberra-pulse* pulseaudio* pulseaudio-esound-compat*
  pulseaudio-module-bluetooth* pulseaudio-module-gconf*
  pulseaudio-module-udev* pulseaudio-module-x11* ubuntu-desktop*[/B]
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 5,411kB disk space will be freed.
Do you want to continue [Y/n]? 
```

**[COLOR="Red"]DO NOT PRESS Y IF IT WANTS TO GET RID OF ANYTHING ELSE[/COLOR]**. Although its not that big of a deal since you can simply reinstall any packages that gets deleted.

> **Skyline969 said:**
> And it says replacing pulseaudio with ESD may possibly completely disable sound at all on my computer... that can't happen. Is there a way that I can guarantee that it won't completely disable my sound? Obviously I want to listen to music, hear sound on ZSNES, etc. I can live without the African sounding login/out sounds... I was meaning to disable those anyways. =P

Well let me put it to you this way, if esd doesn't work which *could* happen depending on what hardware you have, you can just simply reinstall pulseaudio.

---

### Post by Skyline969 on 2009-12-06
This is what it says it'll remove if I remove pulseaudio:
libcanberra-pulse
pulseaudio-esound-compat
pulseaudio-module-bluetooth
pulseaudio-module-gconf
pulseaudio-module-udev
pulseaudio-module-x11
ubuntu-desktop

---

### Post by Dark Aspect on 2009-12-06
> **Skyline969 said:**
> This is what it says it'll remove if I remove pulseaudio:
libcanberra-pulse
pulseaudio-esound-compat
pulseaudio-module-bluetooth
pulseaudio-module-gconf
pulseaudio-module-udev
pulseaudio-module-x11
ubuntu-desktop

See above,

Your fine, go for it.

---

### Post by Skyline969 on 2009-12-06
> **Dark Aspect said:**
> See above,

Your fine, go for it.

Here goes nothing... I'll be back in 10 or so minutes with the results.

EDIT: Standstill... already. Just to check in here, on the instructions you gave me, it says to make all sound playback use ALSA, and to disable system sounds. I can't change sound playback to use ALSA, but I can choose no sound theme for system sounds. I didn't see anything about ESD. Would it still be safe to proceed if I just disabled the Ubuntu sounds theme?

---

### Post by Dark Aspect on 2009-12-06
> **Skyline969 said:**
> EDIT: Standstill... already. Just to check in here, on the instructions you gave me, it says to make all sound playback use ALSA, and to disable system sounds. I can't change sound playback to use ALSA, but I can choose no sound theme for system sounds. I didn't see anything about ESD. Would it still be safe to proceed if I just disabled the Ubuntu sounds theme?

Okay..........

My bookmarks are slightly outdated, that howto was for Ubuntu 9.04, for Karmic do this:

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4")

Thank you for your patiences, I am not the best with human communication.

---

### Post by Skyline969 on 2009-12-06
> **Dark Aspect said:**
> Okay..........

My bookmarks are slightly outdated, that howto was for Ubuntu 9.04, for Karmic do this:

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4")

Thank you for your patiences, I am not the best with human communication.

Ah it's fine, I'll try this out tomorrow. It's getting late, and I don't want to make a mistake due to being tired. Thanks a lot for your help, I appreciate it!

---

### Post by sparky8251 on 2009-12-29
I had the exact same problem but I didn't remove pulseaudio, I changed the way that ZSNES outputs audio. To do this enter your home folder and under the view menu there is an option that says "show hidden files." Click it. Now a ton of folders should show up but you want to enter the one called ".zsnes" and find a file called "zsnesl.cfg" Open it and find the line that looks like this:

libAoDriver="auto"

You need to replace "auto" with a different sound server. To determine which sound servers you can use type "zsnes --help" into a terminal. The second option lists the sound servers that you can use. Find one and replace it "auto" in "zsnesl.cfg" with the sound server that you chose and save "zsnesl.cfg". Restart Zsnes and see if the sound is any better. If not repeat the process. I actually used "pulse" because for me "auto" chose "alsa" and that was giving me choppy sound.

---

### Post by mister_playboy on 2009-12-30
ZSNES hasn't been updated since, what... 2005?  You may want to give bsnes a try.  The dev even visits this forum.  :guitar:

[http://byuu.org/bsnes/](http://byuu.org/bsnes/)

---

### Post by batjew_beyond on 2010-01-30
All of these solutions may work, but I don't think they are the best option.
Newer Versions of Ubuntu use pulse, so the simplest thing to do is have ZSNES do the same specifically.

Simply use the following in a terminal, close zsnes, and you should be running perfectly.
```
zsnes -ad pulse
```

---

