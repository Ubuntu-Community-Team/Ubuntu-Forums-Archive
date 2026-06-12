---
title: "Ubuntu 11.04 sporadic fuzzy / distorted sound"
date: 2011-07-18
forum: Desktop Environments
---

### Post by mortuk on 2011-07-18
Have been using the exact same hardware setup for a while now (last 5 or 6 releases) and since 11.04, occasionally my sound will go really strange and fuzzy / distorted.

It usually happens when I change music tracks I am listening to, but it will then effect all system noises. It will then go away as suddenly as it happened, again if I pause the track a few times to stop the distortion.

Its very strange and has only happened to me on 11.04

---

### Post by cmulloy on 2011-08-03
Hi,
I am experiencing the same problem!

I start Rhythmbox and start playing music. Sound is playing perfectly without distortion.

I send an email using Thunderbird, compact an email folder and then I hear a crackle and the sound quality of the music is degraded and now distorted.

I notice the that this is very similar to a corrupted pulseaudio driver problem that some people (including myself) had with an earlier version of Ubuntu. 

The temporary fix is to kill the pulseaudio process and this cures the problem of distorted sound. This worked for me in Ubuntu 11.04.

There is a more permanent fix, I'm sure, but maybe someone else might be able to advise.

Ciaran

---

### Post by popopow on 2011-08-29
Same here. It can occurs just by switching tabs on chromium. Sometimes restarting banshee is enough, sometimes I need to reboot.

---

### Post by XubuRoxMySox on 2011-08-29
If you don't have any applications that *depend* on PulseAudio, you can remove it. That's always one of the first things I do with a fresh installation.

---

### Post by osarusan on 2011-09-03
I have this problem all the time!! It's really frustrating. I have to run pulseaudio -k to end it each time.

Any ideas what is causing this or how to fix it?

---

### Post by mortuk on 2011-10-05
For some reason it seems to have calmed down since I posted this, but it still does it from time to time

Also another issue I have noticed is that I get a very slight tick / scratchy noise every other second, but when I move my mouse (wired USB logitech mx 518) this noise happens constantly as I move the mouse

Very annoying! Current solution is to drown it out with heavy metal, but not ideal if listening to a nice melodic guitar solo :(

---

### Post by cpburns on 2012-02-02
I occasionally experience this problem (Ubuntu 11.04) but using ```
pulseaudio -k
``` seemed to fix the problem.

---

