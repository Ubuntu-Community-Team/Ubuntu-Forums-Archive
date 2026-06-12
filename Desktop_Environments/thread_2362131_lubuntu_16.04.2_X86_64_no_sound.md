---
title: "lubuntu 16.04.2 X86_64 no sound"
date: 2017-05-24
forum: Desktop Environments
---

### Post by yigithaluk on 2017-05-24
Hello all...

This is not first time I have installed linux but first time l/ubuntu... During installatin I did not check install codecs flash etc box because I did not want flash player on my pc...

Now I have no sound. 

How can I fix it? I have searched sometihng on net but It did not work 

Thanks in advance

---

### Post by TheFu on 2017-05-24
Lubuntu uses ALSA for audio.
Many tools require Pulse-Audio these days.  Firefox recently changed to requiring pulse. If you use firefox AND want sound through it, then pulse-audio needs to be installed.

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) is a guide about sound issues.

Can you be more specific about "no sound?"  Does aplay work?  amixer?  vlc?  Did you try switching between all the different audio output choices?  Make certain that HDMI isn't selected, for example.

Without exact, specific, data, we probably cannot help. The link should help you make it using alsa-info.

---

### Post by vasa1 on 2017-05-25
> **TheFu said:**
> Lubuntu uses ALSA for audio.
Many tools require Pulse-Audio these days.  Firefox recently changed to requiring pulse. If you use firefox AND want sound through it, then pulse-audio needs to be installed.
...
I've stopped following the issue of Firefox dropping alsa, but I understand that the Canonical version of Firefox has been compiled to allow alsa to still be used at least for now. See [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1671273/comments/10](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1671273/comments/10)

Eventually, maybe by v56, even that may not be possible ...

---

### Post by TheFu on 2017-05-25
So if you only stay within the Canonical repos, everything should work.  Hopefully, if/when they change, pulse-audio will be a package dependency for firefox.

However, if anyone uses the more current mozilla PPAs, then they are already required to have pulse-audio loaded.

Good to know.

---

### Post by yigithaluk on 2017-05-25
Thank you for your all efforts and helps folks...

I have reinstalled and problem solved.

Thank you very much

---

### Post by TheFu on 2017-05-25
Did you wipe your firefox configs too or just reinstall firefox or reinstall the OS or ... ???

---

### Post by yigithaluk on 2017-05-27
> **TheFu said:**
> Did you wipe your firefox configs too or just reinstall firefox or reinstall the OS or ... ???

Sorry, I had to be clear, my bad, I have reinstalled the OS... and checked the install 3rd party software box. 

Have a nice day

---

