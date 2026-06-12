---
title: "Window manager"
date: 2009-05-26
forum: General Help
---

### Post by porchrat on 2009-05-26
Arghh!

All of a sudden the window border and title bar are gone. Strangely enough though it only occurs for Firefox. For everything else the window border is fine.

I use compiz at the moment, when I move to metacity it solves the problem, but I really would like to keep using compiz.

I have also tried reloading the window manager and restarting the machine entirely.

It isn't super-critical as I can press F11 (full screen mode) twice and when it shrinks back it gets the window decorations back, but still it is annoying.

I see there is already something on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/251617")

Any suggestions?

---

### Post by kay-man on 2009-05-26
Maybe a silly question, but are you sure you're not running FF in full screen mode? Try F11

---

### Post by fooman on 2009-05-26
open firefox and press f11 twice to get to the normal size screen.
click the unmaximize button.
close firefox,  then reopen firefox.
click the maximize button.

that should fix it.

---

### Post by porchrat on 2009-05-29
As I mentioned in my original post I am currently using F11 and while it does help get the window border back it doesn't solve the problem as Firefox seems to lose the border at random.

That and F11 doesn't always restore the window border, sometimes I need to restart. It isn't crippling, just VERY annoying

---

### Post by abyrne on 2009-05-29
I've had this problem before (only I was using metacity). I forget exactly how I fixed it. Try re-installing firefox or compiz?

---

### Post by Viva on 2009-05-29
This happens when you enable legacy fullscreen support in ccsm workarounds. Disable it for normal firefox behaviour.

---

### Post by porchrat on 2009-06-02
> **Viva said:**
> This happens when you enable legacy fullscreen support in ccsm workarounds. Disable it for normal firefox behaviour.

Actually it seems to be completely spontaneous, seems to me that that would cause firefox to always load incorrectly, that is not the case, it happens very seldom. Once or twice the F11 trick has failed to solve it and I've needed to restart, if this continues I will probably reinstall firefox and compiz.

Rather annoying this little issue as other than this the machine runs wonderfully. I may end up scrapping compiz altogether as I don't really need it and it does slow the machine down slightly (my poor integrated chip just can't take the stress).

---

### Post by 4Orbs on 2009-06-02
A while back I discovered that the window frames were disappearing from my apps because I had used the nVidia settings mgr to change the screen resolution away from default. So I set nVidia back to auto and now change the resolution by editing the xorg.conf file. Also, occasionally I have the problem arise after changing Emerald themes repeatedly in a short span of time.

---

