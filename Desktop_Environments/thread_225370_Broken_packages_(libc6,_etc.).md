---
title: "Broken packages (libc6, etc.)"
date: 2006-07-29
forum: Desktop Environments
---

### Post by kloy1334 on 2006-07-29
I tried installing electricsheep today using GDebi and it had asked me to install dependencies. Knowing my system already had a version of libc6, I decided to run apt-get install for electricsheep. It said that my system doesn't have the required libc6 version (which is newer than the one installed). Apt-get tells me to run apt-get -f install to fix the problem... so I do and now I have four broken packages that can't be unmarked.

What can I do?

Broken packages:
electricsheep - I prefer to remove this
libc6 - Only allowing removal/complete removal, but I think I do need this
libc6-dev - Marking reinstallation wants system to remove hundreds of other applications
libc6-i686 - Same issues as libc6-dev

Does anyone know how to recover from this problem? I have attached a picture of my Synaptic broken packages section to aide you in helping out.

Thank you.

---

### Post by win_zik on 2006-07-29
Correct me if I'm wrong, but did you install some non-ubuntu libc?

This is generally a bad idea, as would be removing libc6.

I'd try to first get rid of electricsheep via sudo dpkg -r electricsheep, then open synaptic and try to get the right, that is ubuntu, version of libc6 back.

To do this, select it, then click on package in the menu (should be something like this, I'm not on an English system right now), choose force version and then choose the ubuntu version.

Hope this helps.

---

### Post by kloy1334 on 2006-07-29
Thank you so much. You have saved my system for the neverending annoyance of broken packages!
:)

---

