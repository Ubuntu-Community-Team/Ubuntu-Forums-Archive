---
title: "beep on key combinations"
date: 2009-05-02
forum: General Help
---

### Post by johnnash on 2009-05-02
I've just installed Ubuntu 9.04.

An annoying thing is the system gives a beep whenever I have a keep combination, with alt or shift or ctrl. I get a beep when I release the second key.

I turned off all the sound/alets from system->preferences->sound

and I did the  
sudo nano /etc/modprobe.d/blacklist
adding
blacklist pcspkr

The beep sound is actually gone. Don't know which one of the two worked, but it is silent now.

but none is helping.

Can someone tell me how to disable the key combination beeps?
Thanks!

One of the two worked. It is silent now. Administrator, please delete the thread if necessary.

---

