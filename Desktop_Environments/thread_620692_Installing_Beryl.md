---
title: "Installing Beryl"
date: 2007-11-22
forum: Desktop Environments
---

### Post by TV-VCR on 2007-11-22
Well, it seems the wiki that hosts how to install beryl has been hacked and is down, I was wondering how to install Beryl onto Ubuntu 7.10 Gutsy Gibbon?

Thanks. :)

---

### Post by TV-VCR on 2007-11-22
Oh, and maybe a theme for Wine that makes it look more like Vista's Aero? :confused:

---

### Post by genbuntu on 2007-11-23
Isn't it available in your synaptic manager? You may have to uninstall compiz before installing beryl.

---

### Post by PeterJS on 2007-11-23
You don't want to install Beryl if you're running Gutsy. Work on Beryl has stoped, and Beryl and Compiz have been merged in to Compiz-Fusion, which is installed by default on gutsy. To enable and configure Compiz-Fusion go to System -> Preferences -> Advanced Desktop Effects Settings.

---

### Post by TV-VCR on 2007-11-23
> **PeterJS said:**
> You don't want to install Beryl if you're running Gutsy. Work on Beryl has stoped, and Beryl and Compiz have been merged in to Compiz-Fusion, which is installed by default on gutsy. To enable and configure Compiz-Fusion go to System -> Preferences -> Advanced Desktop Effects Settings.

there is no "Advanced Desktop Settings" option. :(

---

### Post by ebsbox on 2007-11-23
in the Synaptic Package Manager find "compizconfig"

you should find "compizconfig-settings-manager" (mark this for install)

also find "emerald" and "gnome-compiz-manager" (and mark for install)

when you've marked them all for installation, click "apply", it will install everything needed.

Then you will find these things in "System > Preferences"

Happy Decorating!

---

### Post by TV-VCR on 2007-11-24
Thanks! How do I apply an emerald theme?

---

### Post by ebsbox on 2007-11-24
Once emerald is installed, you'll find it under:

System -> Preferences -> Emerald Theme Manager

You can import any Emerald theme (files ending with .emerald)

Select a theme from the Emerald Theme Manager, then
open a terminal window and give the comand:

emerald --replace

You'll notice that if you exit your terminal window, the theme disappears.
In order to save the changes, keep the terminal window open (after giving the above command) and restart Ubuntu.

---

### Post by FutbolEsVida on 2007-11-24
> **ebsbox said:**
> in the Synaptic Package Manager find "compizconfig"

you should find "compizconfig-settings-manager" (mark this for install)

also find "emerald" and "gnome-compiz-manager" (and mark for install)

when you've marked them all for installation, click "apply", it will install everything needed.

Then you will find these things in "System > Preferences"

Happy Decorating!

When i go into ithe Synaptic Package manager i cannot find "compizconfig". Any reason why?

---

### Post by astoltz on 2007-11-25
Try "compizconfig-settings-manager".

---

