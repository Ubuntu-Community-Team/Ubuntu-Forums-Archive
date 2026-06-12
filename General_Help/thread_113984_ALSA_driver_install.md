---
title: "ALSA driver install"
date: 2006-01-07
forum: General Help
---

### Post by dirkhaim on 2006-01-07
I have an Asus W3A, and I understood that to make the sound work I have to install the newest ALSA driver. See a guide here:
[http://wingware.com/support/asus_z63a_ubuntu_5.10](http://wingware.com/support/asus_z63a_ubuntu_5.10)

While trying to configure with:
./configure --with-oss=yes --with-cards=hda-intel --with-kernel=/usr/src/linux-source-2.6.12

I got the following error:
checking for built-in ALSA... "yes"
configure: error: You have built-in ALSA in your kernel.

any idea how I can solve this problem? any other option to set the sound on these intel sound adapters?

Thanks.

---

### Post by miscz on 2006-01-07
From what I understand you have to recompile your kernel without ALSA. There are some howto's on this topic, just search the forums.

---

### Post by newuser111 on 2006-01-08
you can just uninstall the restricted kernel modules right?  It has the alsa drivers in it

---

