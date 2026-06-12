---
title: "Ubuntu 10.04 and multiple user accounts"
date: 2010-05-10
forum: Desktop Environments
---

### Post by Alcareru on 2010-05-10
Hi all

I decided to try Ubuntu 10.04 today. Looks nice and all, but switching between user accounts doesn't work. If I log in with my account. Then switch to my girlfriends account and then back to my account the screen brightness becomes so dim that I can barely see anything. Then I'm forced to log out and log back in. This "feature" renders this new version of ubuntu pretty much useless for me. Anybody has any ideas how to resolve this? Are others able to reproduce this bug?

I tried tweaking some flags for power management through gconf. As a result instead of getting dimmer the screen went all black, expect for mouse pointer which was brightly visible. Pressing ctrl + alt + F2 made also the mouse disappear, but no console login appeared. I was forced to press reset.. so embarrassing.

P.S.
Actually it seems the screen goes "all black" randomly, regardless of what flags are set through:
gconf-editor
apps->gnome-power-manager->backlight
and that "all black" isn't actually entirely all black. Instead if one looks very very very carefully it is possible to very faintly see some parts of the Desktop or log-in form.

---

### Post by Alcareru on 2010-05-10
Ok it seems I have fixed the issue. The problem disappeared after I installed the proprietary drivers for my nvidia graphics card.

---

### Post by mathieud on 2010-05-26
Hello,

I have the same problem on different computers with Intel (integrated) graphics cards...

Any idea?

---

### Post by Alcareru on 2010-05-30
No sry. Perhaps it's intel graphics card related issue. In addition to my nvidia graphics card I have integrated intel graphics too.

---

