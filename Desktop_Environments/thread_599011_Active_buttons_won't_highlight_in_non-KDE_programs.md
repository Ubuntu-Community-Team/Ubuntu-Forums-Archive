---
title: "Active buttons won't highlight in non-KDE programs"
date: 2007-10-31
forum: Desktop Environments
---

### Post by AndyMan1 on 2007-10-31
In many cases I like to tab around my menus and dialogs. For most KDE programs, if you hit the tab key, the item you're currently on will highlight. For example, when you go to configure the desktop, tabbing around will highlight Help, Defaults, OK, Cancel, etc.

For a few programs this highlighting of the active button will not display. I've seen the issue with non-KDE programs. Specifically with Firefox, but also with Thunderbird, Pidgin, and Eclipse.

For example, in Firefox when I enter a password on a page, it will pop up a message asking if i want to remember the password. The buttons "Never for this site" "not now" and "remember" will not give any indication which one is active. I can hit space and the default "not now" will be clicked. I can tab and the others will also be clicked respectively. But there is no way to tell which one is currently active. This seems to happen with any of the usual dialog options, e.g. radio buttons etc.

I'm currently running Kubuntu 7.10 Gutsy. I've tried the Polyester and Plastik themes to see if it's theme specific, but it doesn't seem to be. 

I've attached a file to point out what I'm talking about.

Any ideas how to fix this?

---

### Post by bingoUV on 2007-10-31
> **AndyMan1 said:**
> In many cases I like to tab around my menus and dialogs. For most KDE programs, if you hit the tab key, the item you're currently on will highlight. For example, when you go to configure the desktop, tabbing around will highlight Help, Defaults, OK, Cancel, etc.

For a few programs this highlighting of the active button will not display. I've seen the issue with non-KDE programs. Specifically with Firefox, but also with Thunderbird, Pidgin, and Eclipse.

For example, in Firefox when I enter a password on a page, it will pop up a message asking if i want to remember the password. The buttons "Never for this site" "not now" and "remember" will not give any indication which one is active. I can hit space and the default "not now" will be clicked. I can tab and the others will also be clicked respectively. But there is no way to tell which one is currently active. This seems to happen with any of the usual dialog options, e.g. radio buttons etc.

I'm currently running Kubuntu 7.10 Gutsy. I've tried the Polyester and Plastik themes to see if it's theme specific, but it doesn't seem to be. 

I've attached a file to point out what I'm talking about.

Any ideas how to fix this?


If I understand correctly, you log on to a KDE session, but have non KDE programs installed. Do you also have gnome installed?

For firefox, try changing to a firefox theme which supports this. Firefox is also affected by the gnome (if you have it) theme. Gnome theme should become effective even when you are running under KDE if you run the following
```

gnome-settings-daemon

```

Which are the other non KDE programs that you have trouble with?

---

### Post by AndyMan1 on 2007-11-01
> If I understand correctly, you log on to a KDE session, but have non KDE programs installed. Do you also have gnome installed?
That is correct. Kubuntu 7.10 KDE session, running an assortment of KDE and non-KDE based programs at various times. No Gnome, as i'm rather partial to KDE  :grin:

I've also noticed this in Pidgin (preferences menu), Thunderbird, and Eclipse. I don't use too many other programs on a regular basis, so I'm not sure what else. Firefox is definitely the most noticeable because I'm usually already quite settled into both-hands-on-keyboard mode, while in other programs I might take up the keyboard-mouse position (if that makes sense; creature of habit and so forth)

I'll give the gnome theme in firefox a try in a bit, and see if it helps.

---

### Post by bingoUV on 2007-11-01
> **AndyMan1 said:**
> That is correct. Kubuntu 7.10 KDE session, running an assortment of KDE and non-KDE based programs at various times. No Gnome, as i'm rather partial to KDE  :grin:

I've also noticed this in Pidgin (preferences menu), Thunderbird, and Eclipse. I don't use too many other programs on a regular basis, so I'm not sure what else. Firefox is definitely the most noticeable because I'm usually already quite settled into both-hands-on-keyboard mode, while in other programs I might take up the keyboard-mouse position (if that makes sense; creature of habit and so forth)

I'll give the gnome theme in firefox a try in a bit, and see if it helps.

No, since you do not have gnome, forget what I said about gnome theme. Try installing a firefox theme that you like, and see if it helps you.

---

