---
title: "Unwanted duplicate icons"
date: 2018-09-06
forum: Desktop Environments
---

### Post by steve169 on 2018-09-06
I run Ubuntu 18.04 on a Dell Inspiron 660 PC.

NOTE: I've installed Nemo as my file manager and set it to control my icons.

Here is the left side of my desktop:

[ATTACH=CONFIG]281007[/ATTACH]

I installed the icons at the bottom marked "A."

A second set of icons, marked "B," also appeared. Clicking these icons apparently does nothing.

I have tried to delete the "B" icons in every way I know, but they persist.

How do I get rid of them?

---

### Post by speartip on 2018-09-06
Try checking your /Home/.config/autostart folder, and see if any of those icons appear in there. If so you should be able to delete them from that folder and restart your session.

---

### Post by steve169 on 2018-09-06
Dear [**[COLOR=#000000]speartip[/COLOR]**]("https://ubuntuforums.org/member.php?u=1776664"),

Before I received your message I stumbled upon a solution.

I installed GNOME Tweaks, then went to "Desktop" and turned off "Show icons." Only the unwanted icons disappeared. Woo-hoo.

Many thanks for your message.

---

