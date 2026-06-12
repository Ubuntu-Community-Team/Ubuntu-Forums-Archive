---
title: "Can't install apps. using add/remove programs"
date: 2008-01-30
forum: Dell  Ubuntu Support
---

### Post by spiraleye on 2008-01-30
I have a dual-boot Dell laptop. I used Wubi to install 7.04 (I want to stay with it; the 7.10 upgrade caused too many problems). When trying to install Thunderbird, I get error message:

'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.'

I also cannot open Evolution email, it tries to but fails, so I have a great Firefox browser, but no email. Please help; I'm very new to Linux, and would appreciate step by step help as I find a lot of the jargon a bit confusing. Also is there a way of turning off the startup music? It's really loud and adjusting volume makes no difference. Many thanks.

---

### Post by stalker145 on 2008-01-30
> **spiraleye said:**
> I have a dual-boot Dell laptop. I used Wubi to install 7.04 (I want to stay with it; the 7.10 upgrade caused too many problems). When trying to install Thunderbird, I get error message:

'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.'

I also cannot open Evolution email, it tries to but fails, so I have a great Firefox browser, but no email. Please help; I'm very new to Linux, and would appreciate step by step help as I find a lot of the jargon a bit confusing. Also is there a way of turning off the startup music? It's really loud and adjusting volume makes no difference. Many thanks.

Have you tried running ```
sudo dpkg --configure -a
``` in the terminal? That's usually what fixes it for me.

As for the sound, you can check under Preferences ~> Sound and you should find a tab for your session sounds. Either change or disable the startup sound. You can also find other volume-related preferences there and under your Icon near the clock by right-clicking.

---

### Post by spiraleye on 2008-01-31
Thank you. I ran the sudo command (I wish "sudo" had been in the command line of the original error message) and things started to happen. Thunderbird still didn't load, but later  the "star" icon next to my internet connection icon turned orange and led me to a sun java loading problem. Once sorted, I was able to activate Thunderbird. 

I'm finding Linux a bit of a steep learning curve, and I'm really grateful for any responses. The main thing is I have Firefox and my preferred email app. - and I can stick two fingers up at Microsoft OSes for the time being whilst I carry on learning!

All the best.

---

