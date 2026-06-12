---
title: "Ubuntu 8.10 + LTSP + Skype = Microphone is not Working on Client"
date: 2009-03-09
forum: General Help
---

### Post by srangelov on 2009-03-09
Hi,

I succeeded to set up pulseaudio and skype is working with pulse on the server - I can hear and I can talk. On the client - I can hear but I cannot talk, i.e. on the skype test call I cannot hear myself.

I would appreciate any help on how to set up a working microphone on client. Thank you in advance.

Regards,
Sotir

---

### Post by C-- on 2009-03-09
Did you check the gnome audio settings to make sure the mic is not muted? By default it usually is.

---

### Post by srangelov on 2009-03-10
Yes, I've already unmuted the microphone and all other settings. 

Do you have any other ideas?

---

### Post by srangelov on 2009-03-18
> **srangelov said:**
> Hi,
I succeeded to set up pulseaudio and skype is working with pulse on the server - I can hear and I can talk. On the client - I can hear but I cannot talk, i.e. on the skype test call I cannot hear myself.


I noticed that if I blow strongly into the mic, I will here this noise. I tested it with Sound Recorder and there is the same result - as though if I had decreased the mic volume. I rechecked all controls in the Volume Control and they are all up to the top.

So the mic is actually working but it's volume is very, very small.

Does anyone use skype (with pulse) on thin client?

Any ideas are appreciated!

---

### Post by lns on 2010-01-26
Have you gone to a TTY (CTRL+ALT+F1), logged in and run 'aslamixer' ? There are more fine-grained volume controls for mic, etc. there..usually that's the fix for me.

---

### Post by jamesisin on 2010-01-26
Also, check that you are connected to the mic jack and not a line out jack (this will sometimes result in barely audible mic pick-up).

Have you gone through this thread?

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

There is a specific section on Skype.  The problem I run into most is selecting the correct mic choice from the drop down.

---

### Post by Troya.one on 2010-01-26
i v got such problems on hp pavilion dv66550(amd64). I am new user of Ubuntu (9.10) and i tried everything suggested in this topic - nothing happens - i still have no microphone. Also i noticed that i don't have any devices in sound option  - just pulse audio and some time message appears in right bottom - something bout problems with pulse audio...

---

### Post by jamesisin on 2010-01-26
> **Troya.one said:**
> i don't have any devices in sound option  - just pulse audio and some time message appears in right bottom - something bout problems with pulse audio...

You will definitely want to look at the link I posted above.

---

