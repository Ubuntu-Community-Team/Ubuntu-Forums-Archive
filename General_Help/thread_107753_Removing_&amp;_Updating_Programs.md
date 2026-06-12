---
title: "Removing &amp; Updating Programs"
date: 2005-12-23
forum: General Help
---

### Post by Drahcir on 2005-12-23
I've just recently installed Ubuntu 5.10 just the other day and I've really enjoyed it. It's a large amount better then most of the other distributions I have tried.

Something that's troubling me is that Ubuntu comes with a large amount of programs  that I'll never need to use (BitTorrent, Gaim, Evolution, etc). I've tried removing them by it gives me a minor dependency hell like screen. Asking me to remove a core Ubuntu package called *ubuntu-desktop*. How can I remove these without causing damage to any other programs on the system?

The other problem I'm facing is that many of the programs are outdated. Firefox is just one of them. Installing Blender 3D only gives me the option to install version 2.37. Can I just upgrade these programs without needing the Ubuntu installation software and by just downloading the software from their site?

Thanks to anybody who replies.

---

### Post by dcast on 2005-12-23
It doesn't matter if you remove the ubuntu-desktop package it doesn't actually do anything I removed it and no problem. I also removed apps like the ones you specified. And to upgrade from a site just install the package it will automatically remove the obsolete one

---

### Post by Iandefor on 2005-12-23
Ubuntu-desktop is a metapackage; it in itself does nothing, but has, as dependencies, all the packages that go into making the Ubuntu Desktop environment, such as GNOME, OpenOffice.Org etc. You can remove it without fear of harming your system. Also, to get the latest software, you can try the [backports repositories]("https://wiki.ubuntu.com/UbuntuBackports") and searching around the forums. For instance, there are several good howto's in the Customization Tips and Tricks forums for getting Firefox 1.5 installed.

---

