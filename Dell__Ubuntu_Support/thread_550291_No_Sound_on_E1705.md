---
title: "No Sound on E1705"
date: 2007-09-13
forum: Dell  Ubuntu Support
---

### Post by EoRaptor013 on 2007-09-13
I have flat frakking had it! I have spent at least 40 hours trying to get a decent linux install on my Dell E1705. I'll skip the Fedora stuff in this forum and go to the Ubuntu, Feisty Fawn, issue: For a day or two after installing Ubuntu, sound worked just fine. Then, one day, while I was listening to tunes using Amarok, I paused playback to talk on the phone. When I hit play, no sound. And I haven't been able to get sound back since. I used alsamixer -c 0 from the command line and it identifies the correct card and sound volume is max. lspci shows the following:

00:1b.0  Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev01)

But I'm not sure this is really telling me anything -- ICH7 is the mobo southbridge which, I suppose, would be handling sound but no way to tell what sound card that is. 

As you maybe can tell I'm getting very testy about this. I've Googled everything, read hundreds of posts, downladed and isntalled packages, removed them when they didn't do anything. I don't know what else to do. Sound card, wireless card, lm-sensors; these are such fundamental things there should be no problem accessing, configuring, and using them in any OS, IMHO.

If anybody can help me out with this problem, I'd most certainly appreciate it.

Thanks.
EoRaptor

---

### Post by Afishionado on 2007-09-13
Have you rebooted (or even just logged in and out) since the problem started?

It *shouldn't* be a problem (famous last words...) with the new ALSA sound system, but in the days of the OSS sound system one program would sit on the sound device and prevent any other programs from accessing sound. That might be all that's wrong here.

---

