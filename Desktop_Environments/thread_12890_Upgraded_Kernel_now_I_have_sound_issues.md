---
title: "Upgraded Kernel now I have sound issues"
date: 2005-01-27
forum: Desktop Environments
---

### Post by timgt on 2005-01-27
Hi everyone, this is my fist post asking a question. I have fell in love with Ubuntu and I have tried almost every flavor of linux out there, just wanted to get that off my chest. Now on to the question

Ok, I just upgraded my kernel to 2.6.10-2-686-smp and everything works great except the sound. when I first booted the computer up I had no sound at all, after farting around with my /etc/asound.conf file I found that if I set the section that looks like this

pcm "hw:0,0"

to

pcm "hw:1,0"

then I get basic sound, like when i first boot up and running apps such as xmms and xine, but other apps have no sound. For instance my Playstation and N64 emulators. I am sure there are other apps that are soundless but I haven't gone through all the apps yet.

Any suggestions? or how do i get it to work with pcm "hw:0,0" again? i think that will fix it, because currently I think it is setting my modem as the primary sound card.

---

### Post by timgt on 2005-01-28
geez, thought this would be an easy one for you guys. Nobody knows what to try?

---

