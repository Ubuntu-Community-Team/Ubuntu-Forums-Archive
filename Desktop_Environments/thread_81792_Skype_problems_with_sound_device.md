---
title: "Skype: problems with sound device"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Xappe on 2005-10-25
Hi,

I used skype without any problems on Hoary. Now, using breezy, I have weird problems with the sound:

1. Call echo123, no problems
2. Hangup
3. Call echo123 again, no go --> "problems with sound device"
4. Skype is now locking the sound for all applications on my system
5. Quit skype --> back to normal

Seems like skype somehow locks the /dev/dsp device even for it's own use. 

Are the sound settings somehow different in Breezy?
Suggestions?

---

### Post by Xappe on 2005-10-25
aha! found a workaround for the problem:

[http://juljas.net/linux/skype/]("http://juljas.net/linux/skype/")

seems to work just perfect... :)

---

### Post by sailor420 on 2005-10-26
Bah, I wish there were a better way to do this...

---

### Post by Xappe on 2005-10-27
there is, but they've not implemented it yet. ALSA!

---

### Post by kris kincaid on 2005-12-07
I found this thread while trying to correct my "problems with sound device" issue. The solution that worked for me is to just downgrade to 1.1.0.20. So far it seems to be working fine. 

[http://download.skype.com/linux/skype_1.1.0.20-1_i386.deb]("http://download.skype.com/linux/skype_1.1.0.20-1_i386.deb")

---

### Post by henriquemaia on 2005-12-12
[QUOTE=sailor420]Bah, I wish there were a better way to do this...[/QUOTE]

Xappe's tip is awesome, works flawlessly. I simply substitute the session command for skype for skype_dsp_hijacker. No need to downgrade skype.

Go for it.

---

