---
title: "Can I get some direct rendering diagnostic help?"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by Carbonfish on 2007-11-06
Hi All,

Well, I may have screwed things up good, but maybe someone can get me pointed back toward the default?

I am running Gutsy on an old T23 ThinkPad and I couldn't get the desktop effects to enable, so after reading a few of the threads around here, I thought that if I installed xserver-xgl, my troubles would be over.

I know, I know... don't say it. Anyway, it didn't work and now I no longer have direct rendering. I have attached a screenshot of the output of a glxinfo | grep dir 

I do not know what that output is suggesting that I do to find out why I no longer have direct rendering.

Any ideas about how I can get back to the gutsy default for my SuperSavage card?

Thanks in advance for any help.

KC

---

### Post by FuturePilot on 2007-11-06
Did you remove XGL? You won't get direct rendering with XGL running.

---

### Post by Carbonfish on 2007-11-06
Thanks for the reply. Yes, I removed xserver-xgl, but it didn't revert to the default (direct rendering = yes) after rebooting.

Suggestions?

TIA,

Kent

---

### Post by Carbonfish on 2007-11-06
Okay, after some poking around I found out how to get some information about the terminal output, which got me this: (see attachment)

Now, can anybody tell me how to find and install the driver, savage_dri.so?

Do I just gedit the directory and enter it?

Sorry about the noobish questions, but I'll admit that I haven't done any driver installation that didn't come in a .deb or as part of a larger package.

Thanks,

KC

p.s, If someone replies and I don't get right back to you, I have to be up in about 6 hours, so I'll check the thread in the morning.

Thanks again.

---

### Post by Carbonfish on 2007-11-06
I know that I am bordering on rude by bumping this so soon, but I thought that I would give a few more people a chance to think about it while I was at work this morning...  :>)

TIA for any suggestions,

Kent

---

### Post by Carbonfish on 2007-11-08
Well, I guess it appears that nobody knows what I might do to get direct rendering back, so can someone tell me how to go about either reinstalling the savage driver, or worst case scenario, how to reinstall the kernel so that it will be back to it's default state?

Thanks for any helpful suggestions.

KC

---

