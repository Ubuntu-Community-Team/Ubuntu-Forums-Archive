---
title: "Where are the live cd's desktop settings?"
date: 2010-05-08
forum: Desktop Environments
---

### Post by directedition on 2010-05-08
I'm building a custom version of the live CD, sort of knoppixesque and not really for installation. Anyway, I'm looking to do things like set the desktop background, change the theme, and remove the 'install ubuntu' icon, but the /home directory is empty. Where is the desktop environment stored?

Also, if anyone knows the setting to use in isoLinux to have it always boot into the grub prompt, that would be much appreciated as well.

For those interested, this is the guide I used. It's old, but it worked like a charm: [http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd](http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd) It allows for much finer grained control than the Startup Disc Creator, or those other apt-based tools, which is useless for those who want to set their iptables, privoxy settings, and whatnot.

---

### Post by directedition on 2010-05-09
I found what appears to be the key file:
/var/lib/gconf/debian.defaults/%gconf-tree.xml
Which appears to house pretty much all the relevant data.

---

