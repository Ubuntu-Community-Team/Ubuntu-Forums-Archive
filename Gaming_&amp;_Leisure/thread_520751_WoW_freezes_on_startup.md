---
title: "WoW freezes on startup"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by Parlay on 2007-08-08
When I run WoW under wine the terminal starts displaying text, then stops, and my entire computer freezes.  I'm running Ubuntu Feisty Fawn.  I can run the Launcher.exe but not WoW.exe.  This is very aggravating.  I've been using linux for about 9 months and I've been using wine successfully for about 7.  I've looked at FAQs and walkthroughs for WoW instillation, but none seem to be taking me anywhere productive.  One problem may be I never installed WoW, but copied the program files from my windows box (WoW works on my windows box).  I've put the copied files into my /home/user/.wine location thingy.  If anyone can help me that'd be great.

Parlay

Update

I did some tweaking, and I still have the same problem as above, but I get about 1 second of the opening WoW sound before my computer locks up

---

### Post by Parlay on 2007-08-08
I'm about to get pushed off the page, anyone have any wisdom they can share on this?

---

### Post by graigsmith on 2007-08-09
what kind of videocard are you using? what driver?

---

### Post by Parlay on 2007-08-09
I'm using the integrated one that comes with the laptop.  Its an intel integrated, worked fine in XP, never played WoW on it though.

Section "Device"
    Identifier    "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection

---

### Post by hikaricore on 2007-08-09
> **Parlay said:**
> I'm using the integrated one that comes with the laptop.  Its an intel integrated, worked fine in XP, never played WoW on it though.

Section "Device"
    Identifier    "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection

While certain Intel integrated video chipsets are able to play WoW via WINE in Linux at very low or medium quality.  Most are not.  Shortcutted shotty hardware that relies on DirectX+CPU power, and mostly abandoned video drivers created by Intel make for a sad combination.

When I was using my Intel chipset the best FPS I could hope for is between 5 and 8.  That was indoors away from anyone, just farming instances.  Anything outside or in towns either dropped to 1fps or less or crashed the game completely.  That along with texture issues prompted me to get a NVIDIA card and be done with the mess.

There may be a solution for you, but what I'm saying is don't get your hopes up.  If you can't get a new video card/find a solution with your current card I suggest dual booting.

---

### Post by Parlay on 2007-08-09
> **hikaricore said:**
> While certain Intel integrated video chipsets are able to play WoW via WINE in Linux at very low or medium quality.  Most are not.  Shortcutted shotty hardware that relies on DirectX+CPU power, and mostly abandoned video drivers created by Intel make for a sad combination.

When I was using my Intel chipset the best FPS I could hope for is between 5 and 8.  That was indoors away from anyone, just farming instances.  Anything outside or in towns either dropped to 1fps or less or crashed the game completely.  That along with texture issues prompted me to get a NVIDIA card and be done with the mess.

There may be a solution for you, but what I'm saying is don't get your hopes up.  If you can't get a new video card/find a solution with your current card I suggest dual booting.

Okay, thanks.  Well, gives me a good reason to get a bigger HD and dual boot...

---

### Post by misconfiguration on 2007-08-09
I had the same card in my laptop, you're better off not trying. Driver support really sucks for these intel chipsets. I sold my laptop and got one with a nvidia chipset.

---

