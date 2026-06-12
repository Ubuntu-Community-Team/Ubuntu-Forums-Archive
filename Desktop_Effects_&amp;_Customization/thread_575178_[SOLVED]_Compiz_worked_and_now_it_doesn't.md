---
title: "[SOLVED] Compiz worked and now it doesn't"
date: 2007-10-13
forum: Desktop Effects &amp; Customization
---

### Post by wbrady4927 on 2007-10-13
I installed the development version of Gutsy a couple months ago and was amazed by how awesome Compiz was. It was working beautifully and most importantly, automatically. I install updates daily and just recently (probably at the time that Beta version was released) I installed some updates, restarted my computer and BAM! Compiz did not work anymore. I went into Preferences->Appearance and then to the Visual Effects tab. I tried selecting Normal, Extra, or Custom and each one would give me an error saying "Desktop Effects could not be enabled".

I have an ATI Radeon 9550 graphics card. I don't understand why it could go from working to not working. Updates are supposed to be good aren't they?

---

### Post by Forlong on 2007-10-14
> **wbrady4927 said:**
> I have an ATI Radeon 9550 graphics card.
Did you install the proprietary (restricted) driver? Then you need to install Xgl as well: ```
sudo apt-get install xserver-xgl
```

---

### Post by wbrady4927 on 2007-10-14
It works great, I installed the proprietary driver and xserver-xgl, restarted the computer and everything works. Thank you very much.

Do you know if that would also be the correct way to get compiz working on a laptop running an ATI Radeon Xpress 200M IGP graphics card?

---

