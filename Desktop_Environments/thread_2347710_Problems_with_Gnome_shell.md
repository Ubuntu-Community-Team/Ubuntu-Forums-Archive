---
title: "Problems with Gnome shell"
date: 2016-12-27
forum: Desktop Environments
---

### Post by macozz on 2016-12-27
Hi all,
just starting today, the Gnome shell does not allow to change the icons and the bottom bar appeared from nothing and cannot remove it. I already try several methods, from code editing and shell extensions with no luck. 
I am using Gnome shell 3.22.2 in Ubuntu 16.10 64-bit.
Any suggestion is welcomed. 

Cheers

---

### Post by tea for one on 2016-12-28
Do you have gnome-tweak-tool installed?

This is the utility which helps to manage extensions, icons, themes etc.

Best wishes

---

### Post by Frogs Hair on 2016-12-28
The user themes extension has to be installed and enabled in the Tweak Tool in order to use 3rd party themes and icons.

---

### Post by macozz on 2016-12-28
Thank you for the suggestions.
Both, gnome-tweak-tool is installed and user themes enabled... I am able to change themes, but no icons, despite the icon folder is recognized by GTT. Also, the extensions that supposedly make the bottom bar disappear seem have no effect.

---

### Post by Frogs Hair on 2016-12-28
> **macozz said:**
> Thank you for the suggestions.
Both, gnome-tweak-tool is installed and user themes enabled... I am able to change themes, but no icons, despite the icon folder is recognized by GTT. Also, the extensions that supposedly make the bottom bar disappear seem have no effect.

The bottom panel is a feature of the classic session. There are two sessions installed with the Gnome Shell.

---

### Post by macozz on 2016-12-29
> **Frogs Hair said:**
> The bottom panel is a feature of the classic session. There are two sessions installed with the Gnome Shell.

I try to find it. but I failed... Any suggestion on how to get ride of this?

Thanks!

---

### Post by Frogs Hair on 2016-12-29
I have only used up to 3.20 on 16.10 and each session on that version and those before it had a separate icon for each session on the greeter box where the password is entered. Did you install 3.22 via PPA ? There is an extensions package in the repository and I don't remember if it is installed by default.

---

### Post by macozz on 2016-12-29
I just found a couple files installed recently as dependency of other application that interfere with the shell. Removed and all is back to normal...
Thanks a lot!

---

