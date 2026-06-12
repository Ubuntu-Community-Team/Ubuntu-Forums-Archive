---
title: "Java acts strange when playing some Club Pogo Games"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Crochetchick on 2006-08-19
I love Club Pogo Games, and for some games I have to log into windows to play. The applet will just freeze the game, or some games will just slow down. There is also sound loops and skipped sound. It's not very enjoyable sometimes, and I do not want to go to windows all the time.

When I use command
> java -version
here is what I get:

java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

This I compiled from the Sun Java site. 

When I use command
> sudo update-alternatives --config java
I set it as the default java.

Anyone have some advice? ](*,)

---

### Post by kchris623 on 2007-01-19
I am having the same problems. I have a slightly higher version, though.

java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

One thing I have noticed is that every now and then I can right click on other players names and get a context menu, but most of the time it causes a crash. I also have the same sound looping and choppiness about 90 % of time. 

I looked around the web and found lots of great advice for *installing* java, but nothing about this particular problem until I looked here. I didn't see a better post/answer than this when I searched, so I thought I would add here that I was experiencing the same type of problem.

I'm pretty new to Linux, so I'm willing to admit it might just be I did something wrong :oops:, but from what I'm seeing when I search, it kind of seems like java and ubuntu (or just *nix in general) don't get along so well.

Any help would be greatly appreciated, and outside of having problems with pogo.com games and java...I am *HOOKED* on Kubuntu. I can't believe I haven't crashed in over 2 weeks! :o

---

### Post by jmitch52 on 2007-09-09
I am having the same problem with the sound looping or repeating. I am on a clean install of Ubuntu and latest java. I had the same problem with slow downs and pogo freezing on checking profiles till I did the new install.. It works great now..  The sound is what gets me

---

### Post by play0r on 2008-02-01
i was experiencing the same problem with my soundcard that used the emu10k1 module. all i did to resolve the issue was comment out the .asound.asoundconf settings, add the following lines, and restarted alsa. then everything functioned as normal.

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
#</home/username/.asoundrc.asoundconf>
!defaults.pcm.card 0
defaults.ctl.card 0
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.device defaults.pcm.device

```

---

### Post by Biznarie on 2008-03-08
I'm also having problems with pogo games, some of them run slow and choppy like high stakes pool. I'm not sure about the sound i dont have speakers hooked up atm.

---

