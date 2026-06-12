---
title: "xfce fails to start after dist-upgrade"
date: 2014-10-09
forum: Desktop Environments
---

### Post by raccoonstrait on 2014-10-09
Good Morning

After update, upgrade and dist-upgrade last night xfce fails to start. I get the login page, and then a blank screen with the wallpaper only. CNTRL-ALT F1 and I have tried startxfce4 but get:
(EE)
Fatal server error:
(EE) Server is already active for display 0

then

XIO" fatal IO error 11 (resource temporarily unavailable) on X server ":0"
    after 7 requests (7 known processed) with 0 events remaining

it hangs.

I have tried aptitude reinstall xfce4 lightdm xserver xserver-common (etc, I looked up the correct filenames @ [http://www.x.org/wiki/](http://www.x.org/wiki/)) but no joy.

The system has been running well, for a long time before this, I really would not like to start over again.

Any ideas?

Raccoonstrait

edit, actually I have tried so many things I do not remember them all, reinstall libgtk2.0-dev is another, also tried removing the .X0-lock and restarting

I suppose I should add that this is an older IBM ThinkPad r50e that has been running linux for about 10 years, first as a dual boot, then as a tri-boot (ubuntu dual booting with windows XP and kde on an external drive) but since XP support went away, a single boot with XFCE since about January.

---

### Post by raccoonstrait on 2014-10-09
Sorry folks, cannot wait any longer, doing a system reinstall.

Raccoonstrait

---

