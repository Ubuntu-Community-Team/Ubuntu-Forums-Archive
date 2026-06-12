---
title: "installing amsn &amp;&amp; root password"
date: 2006-02-20
forum: Desktop Environments
---

### Post by ELD on 2006-02-20
Hi all i installed amsn but the installable version from the package thing is out of date so i went on to the amsn website and downloaded the ubuntu package.

Just wondering how i install it, its a .deb package?

Also how do i find out/set my root password?

---

### Post by Ramses de Norre on 2006-02-20
```
sudo dpkg -i packagename.deb
``` should install it perfectely, only problem could be the dependencies, you should download them using sudo apt-get install packagename  (only the dependencies!) dpkg will make notice of them if they are needed.

What do you mean by root password? The password to use sudo is your normal user password, and with sudo you should be able to do everything (even log in as root with sudo su root).
You can enable the root password, but exept for a good reason I wouldn't do so.

Edit: if you'd really need the root password: sudo passwd root should do the trick;)

---

### Post by ELD on 2006-02-20
Thanks but i've found that Easy Ubuntu software, its taking forever to do the multimedia packages but it has the latest amsn in it, so i am hoping that it will work.

---

### Post by Lord Illidan on 2006-02-20
Generally nearly all problems involving root can be solved with sudo. This can prevent you from fscking up an installation.

If you want to enable the root password:

```
sudo passwd
``` should do it.

---

### Post by ELD on 2006-02-20
Okay thanks a lot but it seems automatix has sovled my problems! What a nifty program!

---

