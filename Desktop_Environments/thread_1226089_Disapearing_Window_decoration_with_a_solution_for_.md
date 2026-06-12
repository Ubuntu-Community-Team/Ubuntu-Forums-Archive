---
title: "Disapearing Window decoration with a solution for some of us"
date: 2009-07-29
forum: Desktop Environments
---

### Post by satriaulie on 2009-07-29
Hi everyone!
Had any problems with disapearing Window decorations and desktop effects?

This may be your solution. I Just got it solved on my old desktop with Nvidia Geforce4 mx440.

The problem is the Nvidia driver and not the settings in compiz and Metacity.
I'm afraid I don't know how to reverse an allready ****** up configuration setting, so this is for those of you who do not mind making a fresh install.

So to the simple solution.
When you have installed the Nvidia drivers and activated it, do not start nvidia-settings! I don't think the problem is when you start it, but when you start changing the settings. Or more specific, when you save to X.
As far as I've noticed these settings doesn't aply anyway. They just **** up the compiz effects. Unfortunatly I don't know how to undo the dammage when it's done. So only way I know is a fresh install.

My laptop, also running Ubuntu, doesn't mind that I change the Nvidia settings, but it still doesn't affect the display. So I guess this problem only exists on some Nvidia cards.

To those of you who know more about ubuntu and linux programming, maybe you can give us a better solution?

---

### Post by satriaulie on 2009-08-02
I'll just add that you can edit nvidia settings, but not save to x.
Just been testing a bit.

---

### Post by ccnjim on 2009-08-02
I'm also new here. I spent a couple of weeks trying to save my Nvidia settings. Re-installing/purging drivers. I stumbled across a post that said in order to save changes you have to open  NVIDIA X Server Settings from the terminal, not from the start menu. This has made life much easier. After you save your settings. Log out/in to your desktop.

```
$sudo nvidia-settings
```Any idea how to keep windows from becoming transparent when you open them? lol that's my mission of the day(s)!

---

