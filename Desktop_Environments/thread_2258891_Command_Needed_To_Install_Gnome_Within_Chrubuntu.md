---
title: "Command Needed To Install Gnome Within Chrubuntu"
date: 2014-12-31
forum: Desktop Environments
---

### Post by perknh on 2014-12-31
Hello Ubuntu GNOME Lovers,

I'm having great difficulty installing Gnome desktop within developer's mode on my Chromebook using Chrubuntu.

Here's where I get lost, at the question marks:   ```
curl -L -O https://goo.gl/9sgchs; sudo bash 9sgchs -m ?????-desktop -u lts
```

I'd tried these combinations:* gnome-desktop*,* ubuntugnome-desktop*, *gnome3-desktop*.  I will try *ubuntu-gnome-desktop*, but, at this point, I'm not holding my breath!

Any suggestions would be appreciated.

And thank you very much.

perknh

---

### Post by schragge on 2014-12-31
It's just *gnome*.

---

### Post by perknh on 2014-12-31
> **schragge said:**
> It's just *gnome*.

Thank you, schragge.  I just tried *ubuntu-gnome-desktop, *the one I hadn't tried, and, that's the one that worked for me today!  But your way is much simpler.

So it appears there may be two ways to add GNOME desktop to to a Chromebook using Chrubuntu.

I thank you very much.

perknh

---

### Post by schragge on 2014-12-31
The two are not quite the same. The meta-package *gnome* is provided by Debian GNOME Maintainers and installs more or less vanilla GNOME environment while *ubuntu-gnome-desktop* is provided by Ubuntu GNOME Developers and contains Ubuntu-specific tweaks as well. Mine may be simpler, but yours is better and more Ubuntu-like. Actually, it's the recommended way to install GNOME on Ubuntu. I was just not sure it's present on Chrubuntu. But as you've just found out it is.

---

### Post by perknh on 2014-12-31
Well, I'm giving your "Vanilla GNOME" a shot as we speak.  It's downloading now.  I found my installation to be a bit buggy.  I got into Ubuntu's GNOME once within Chrubuntu, but after a reboot I couldn't get into the program again.  I'm going to try this entire process with Ubuntu's MATE too.  As you probably know, they're doing some gorgeous development work over at Ubuntu's MATE project.

Thank you so much, schragge.  You gave me some terrific insights here.

perknh

---

