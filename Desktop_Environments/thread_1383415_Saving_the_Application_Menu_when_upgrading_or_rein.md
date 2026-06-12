---
title: "Saving the Application Menu when upgrading or reinstalling Ubuntu"
date: 2010-01-17
forum: Desktop Environments
---

### Post by miiichaaaeeel on 2010-01-17
I was wondering if it was possible to back up the application menu layout when doing an upgrade or reinstalling Ubuntu.

It is just a pain to re-arrange it every single time.

Thanks

---

### Post by lovinglinux on 2010-01-17
You can keep all your settings, including the menu, if you create a separate partition for home. I strongly recommend you do that. It saves a lot of time and trouble.

See [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you don wan to do that, you could backup your home directory and restore it after the installation.

You can also create a list of installed applications, so you can install them all at once after installing Ubuntu. See the Umarks extension from my signature.

---

### Post by miiichaaaeeel on 2010-01-18
I actually have my disk already fully partitioned... so maybe I should not format /home when I reinstall. I was looking for the folder to save like I do for FF or Thunderbird.

Your addon seems pretty cool. I will try it out.
Are you considering a stand alone program as well?

---

### Post by lovinglinux on 2010-01-18
> **miiichaaaeeel said:**
> I actually have my disk already fully partitioned... so maybe I should not format /home when I reinstall. 

Yes, don't format home, just mount it as home again during the installation process.

> **miiichaaaeeel said:**
> I was looking for the folder to save like I do for FF or Thunderbird.

I'm currently using KDE, so I don't know where it is, but you should be able to copy the folder with the menu entries.

> **miiichaaaeeel said:**
> Your addon seems pretty cool. I will try it out.

Thanks.

> **miiichaaaeeel said:**
> Your addon seems pretty cool. I will try it out.
Are you considering a stand alone program as well?

Nope. You can do that from Synaptic, by selecting "File >> Save Markings As" and ticking the option "Save full state, not only changes". To install, use the "Read markings option.

Anyway, with my extension you can keep several versions of the installed package list, export, import lists, can see which packages are included in each list and search several sites (ubuntu, allmyapps...) by just selecting the package name.

---

