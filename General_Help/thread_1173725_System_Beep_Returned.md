---
title: "System Beep Returned"
date: 2009-05-30
forum: General Help
---

### Post by ThatNerd on 2009-05-30
I'm using Jaunty Jackalope x64 on an HP laptop and find that my greatest annoyance with Ubuntu is the system beep that is constantly driving me nuts. I have already blacklisted the driver and that killed it for some time, except for shutdowns/restarts. Now, for some reason, the beep has returned and I can't figure out why. When I try to rmmod pcspkr it tells me that no such module exists but the beep continues. Any ideas? The beep does not make for a good first impression of Ubuntu.

---

### Post by kpkeerthi on 2009-05-30
Blacklist or rmmod pcspkr and snd_pcsp.

---

### Post by ThatNerd on 2009-05-30
> **kpkeerthi said:**
> Blacklist or rmmod pcspkr and snd_pcsp.

I've tried rmmoding it and it says the module does not exist, which is what is weird about this problem. It's as though the pcspkr is working without a driver.

---

### Post by kpkeerthi on 2009-05-30
Blacklist both pcspkr and snd_pcsp and reboot.

---

### Post by ThatNerd on 2009-05-30
I was able to re-blacklist it. Any idea how it was "un-blacklisted"?

---

### Post by bdoe on 2009-05-31
Here is a better question: Why, in the 21st Century, is Ubuntu still relying on the system beep as the primary aural means of getting the user's attention? Seriously: Ubuntu has user-definable system sounds (which, I may add, I have *never* seen/heard working properly). Why is Ubuntu not using these properly? It's a very basic function that even Windows does flawlessly: Allow the user to tie an event (system, desktop, notifications, etc.) to a specific sound, and *only* use the system beep when the normal sound system (OSS/ALSA) is completely unavailable!

New users are not going to understand, "Oh, just modprobe this and blacklist that," and making the system beep the default sound is not only *so *1980, it is also *not* a good way to leave new users with the impression that Linux is a modern OS.

---

