---
title: "Lubuntu chrome stable low dpi"
date: 2015-06-02
forum: Desktop Environments
---

### Post by bjakke on 2015-06-02
Hi, I upgraded my PC to newest kernel, i'm running Lubuntu.
After the upgrade it used a horrible display resolution, so I Installed the Nvidea official kernel, that adds a xserver to the xserver config.
Eversince this upgrade my google-chrome-stable application looks like it runs with a really low DPI, all other appliations has a normal look.

I tried reinstalling chrome using:
sudo apt-get install --reinstall goolge-chrome-stable
But that didn't help.

---

### Post by Copper Bezel on 2015-06-02
Hmm. Could you possibly have hardware acceleration enabled in Chrome (chrome://flags)? That might be getting confused. I'm trying to think what could have to do with the kernel and-or drivers that would affect Chrome. 

Do you see the same problem in Chromium, or on logging in on an alternate account?

---

### Post by bjakke on 2015-06-03
I tried to create a different user, it had the same problem.
In chrome://flags all hardware accl. options are turned off.

I installed Chromium, this look completely normal. You can clearly see the difference:
[IMG]http://i.imgur.com/9oAuTgX.png[/IMG]

I uninstalled chrome-stable, deleted:
/home/USER/.cache/google-chrome/
/home/USER/.gnome/apps/chrome*
/home/USER/.config/google-chrome/
reinstalled, the problem still occurs.

---

### Post by v3.xx on 2015-06-03
My understanding is chromium just lacks the restricted package(s) to be chrome.  Could be more to it, but maybe install pepper flash.  Use it instead.

---

### Post by Copper Bezel on 2015-06-03
Could it be related to recent tweaks to Chrome for the high-DPI mode? As [here]("https://code.google.com/p/chromium/issues/detail?id=143619")? I think I'm out of my depth. = /

---

### Post by bjakke on 2015-06-03
I have struggled with Chrome specific plugins in Chromium before. I think its just easier to install Chrome, it works perfectly with flash, pdf, netflix, out of the box.

---

### Post by Copper Bezel on 2015-06-03
Oh, agreed - I use Chrome as well. 

I'm not sure what to try, but do any of the command-line flags for DPI scaling have any effect?

---

### Post by bjakke on 2015-06-04
> **Copper Bezel said:**
> Could it be related to recent tweaks to Chrome for the high-DPI mode? As here? I think I'm out of my depth. = /


I tried changing the dpi as mentioned in the link you found. It scales chrome according to the input values, but but the sweet spot is somewhere between
xrandr --dpi 100
and
xrandr --dpi 101


So now it doesn't take up too much space of my screen, but it still looks wrong.

---

### Post by Copper Bezel on 2015-06-04
Okay. The closest I can get to reproducing your problem otherwise is by changing my system DPI scaling (from Ubuntu's Displays plug, which you don't have in Lubuntu) and starting Chrome. The Chrome interface scales to match this setting, and it makes it big and ugly. This control in Ubuntu changes [these dconf settings]("http://askubuntu.com/questions/471425/scale-title-bars-and-menu-in-ubuntu-14-04-with-gnome"), but I can't imagine how yours could have been fussed up ... since Lubuntu does not respect these values and Chrome does, though, if you have gconf installed, it *could *theoretically cause a bug you're seeing only in Chrome. Maybe?

---

### Post by bjakke on 2015-06-09
I updated Chrome to the newest version today, and the error is gone. Very weird.

---

### Post by Copper Bezel on 2015-06-10
Given that there's active attention and work on DPI scaling in Chromium at the moment, and that a lot of changes are being made and everything seems to be a mess of workarounds and stacks of scaling factors, I'd say you encountered a bug in one of those factors that was fixed at some point in the interim.

---

