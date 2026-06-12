---
title: "Pitfalls of using an old home directory with a new Natty install?"
date: 2011-05-05
forum: Desktop Environments
---

### Post by morrisjones on 2011-05-05
I've been unsuccessful with a Natty upgrade, in this sense:  I'm unable to use anything but a Metacity theme ("Ubuntu Classic (No effects)").  So I lost all my Compiz effects, the most valuable of which, for me, was the grid layout tool.  I think the problem is confused Radeon/ATI driver issues -- fglrx was dead on arrival with the update, and falling back to the generic ATI driver gets me Metacity but not Compiz.

I'm now considering preserving my /home directory and doing a clean install of Natty on my system drive.  Unity works decently well on a USB drive boot -- not that I'm especially fond of it, but I want to give it a fair shake.  Presumably it will work with a clean install.

But I'm frankly concerned about all the hidden gnome and X configuration files in my restored home directory.  When I plop my old homedir onto a new 11.04 system install with all my old packages, what's going to happen?

(What are the chances of someone actually seeing this and knowing?  :)  )

(amd64, RV710 Radeon HD 4550, dual monitors)

Mojo

---

### Post by Paddy Landau on 2011-05-05
Back up your home folder and try! The worst that can happen is you don't like it, and reinstall your previous version.

Another alternative is to install 11.04 and restore only your data, not your hidden folders & files.

---

### Post by Tekmoor on 2011-05-05
I have my home on a separate partition and I tried using my old (10.10) home folder with 11.04 and it worked but was pretty messed up to the point where for me it was worth reinstalling with a clean home directory.

Based on my experience I recommend backing up your home folder, installing 11.04 with a clean one and then manually picking and choosing which folders from your backup home to copy over to your new home. I generally copy over settings as I need them, for example the day after I installed 11.04 I realized I really need a certain program so I install it and then copy the settings from my backup home.

Hope that helps!

---

### Post by morrisjones on 2011-05-06
Both good suggestions, thank you! Manually rebuilding my home dir seems the way to go. Sadly. :)

---

### Post by Paddy Landau on 2011-05-06
> **morrisjones said:**
> Both good suggestions, thank you! Manually rebuilding my home dir seems the way to go. Sadly. :)
Not really sadly. As Tekmoor says, restore your data, and then restore settings only as needed. I have done it myself when upgrading from 8.04 to 10.04 and it really was no big deal.

By the way, are you aware that settings are stored in hidden folders in your home drive (not in some registry as with Windows)?

(If you feel we've answered your questions, please mark the thread as Solved.)

---

### Post by ivanovnegro on 2011-05-06
> **Paddy Landau said:**
> Not really sadly. As Tekmoor says, restore your data, and then restore settings only as needed. I have done it myself when upgrading from 8.04 to 10.04 and it really was no big deal.

By the way, are you aware that settings are stored in hidden folders in your home drive (not in some registry as with Windows)?

(If you feel we've answered your questions, please mark the thread as Solved.)

I do it always this way, nothing hard or time consuming, the best way to go for the OP.

---

