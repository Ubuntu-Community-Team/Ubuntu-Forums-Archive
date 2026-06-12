---
title: "microphone doesn't work on Inspiron 1545 after installing 9.10"
date: 2010-03-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by a cup of tea on 2010-03-11
I have a Dell Inspiron 1545 that came with Ubuntu 9.04 preinstalled. I decided to do a fresh install from the Ubuntu alternate install CD so that I could have full disk encryption. I think everything's working now except my microphone. I've tried fiddling with audio settings, and my friend fiddled with audio settings, and I'm not sure what to do now.

---

### Post by lz1dsb on 2010-03-12
I had a similar problem with my Dell Studio 1555. But the problem arose after an upgrade of the pulse audio package. You can check out the following regression in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819)
If this is causing the problem, than you'll see the steps there to solve it.

Cheers,
Boyan

---

### Post by a cup of tea on 2010-03-12
Thanks. I looked through comments there and followed one for my hardware, and I'm not sure how it worked, but it did and now my mic works. 

:)

---

### Post by perham on 2010-03-12
I have 1545 too, and my mic worked out of the box. isn't that a little weird? I mean, if it's a bug it should affect everyone, right?

---

### Post by lz1dsb on 2010-03-12
Well, not. It's because it's a regression. To me it happened after I upgraded to the latest version of the pulse audio package. So it really depends on which pulse audio package you've got when installing the system. As far as I know they change the ISO image by adding the latest packages. 
To me it also worked out of the box, because I installed the system at least four months ago, the issue happened after an update. So there are many variables here :p Isn't that the charm of Linux... well maybe sometimes it isn't that charmy....

Cheers,
Boyan

---

### Post by karlmsusa on 2010-03-14
I solved my problem with internal mic not working on the 1545 as follows:

In sound preferences  select - Hardware profile - Analog Stereo Duplex 
                                 select - Input - Connector

Adjust Input Volume - Microphone 1 for suitable level on EXTERNAL mic
Adjust Input Volume - Microphone 2 for suitable level on INTERNAL mic

---

### Post by brianfactors on 2010-03-18
Have a 1545, too.

I had some problems with Pulse, but they were actually fixed when I went to 9.10. Never had issues with the mic, though. That's really strange...

Apparently, as you said, it seems to be a problem using unsupported versions of Pulse. Has this been solved?

---

