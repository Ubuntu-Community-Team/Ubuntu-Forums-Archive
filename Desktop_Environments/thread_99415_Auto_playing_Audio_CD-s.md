---
title: "Auto playing Audio CD-s"
date: 2005-12-05
forum: Desktop Environments
---

### Post by michux on 2005-12-05
I wanted Kaffeine or KsCD to automatically start playing audio CD-s when inserted. But I encountered problems with both apps.

When I set "Play" (with KcCD) in Kcontrol->Peripherals->Storage media (for Audio CD), KsCD does show up but doesn't want to play music. I have to manually set "alsa" as it's engine every time and then it starts playing. It keeps forgetting it and switching back to arts (which doesn't work) regardless I apply changes every time.

When I set "Play audio CD with Kaffeine" it actually opens Kaffeine but asks me in a dialog for a device to play from! When I manually enter "/dev/cdrom" it starts playing the music. Pretty annoying. I have /dev/cdrom as a default audio cd device everywhere posiible in Kaffeine settings. Still it doesn't seem to notice that.

Am I doing something wrong or are these just bugs in KDE 3.5 that I should get used to?

Thanks in advance for your coooperation.

---

### Post by dcra19 on 2006-05-07
Hi michux

I have been having a similar problem.  I have Kubuntu 5.10 on an AMD64 Sempron, and none of the updates have fixed it, but:

I  may have a solution for you.  I was reading anotther post about ALSA and the OSS mixer, and the person
there said you need the libesd-alsa0 library instead of the libesd0 to make everything work well with ALSA.

I used Adept and installed libesd-alsa0.  Adept removed libesd0 as part of the installation.

KsCD works fine now *but* it still thinks it uses arts.  But it works now and autoplays, etc.  I think it has bugs.

---

