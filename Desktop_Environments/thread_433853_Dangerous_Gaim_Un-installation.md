---
title: "Dangerous Gaim Un-installation"
date: 2007-05-05
forum: Desktop Environments
---

### Post by october1917 on 2007-05-05
I tried to unistall Gaim in order to install pidgin.

Unfortunately every time i try to uninstall gaim (either using Synaptic, or console) it returns me that it will also remove "nautilus send-to" and "ubuntu-desktop"

It also happens with Evolution.

Is there a solution to this ...bug(?) or not?
What can i do to fix this?

---

### Post by zerwas on 2007-05-05
Hello,

ubuntu-desktop is only a [metapackage]("https://help.ubuntu.com/community/MetaPackages"). It is safe to remove it :-)

Best regards,
zerwas

---

### Post by hyperair on 2007-05-05
Here's a bit of advice: go to [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin) and download the pidgin DEB. Then just double click to install it. You DO NOT need to uninstall Gaim in order to install Pidgin. They do not conflict in any way. In the case that you are not using Feisty, but using Edgy or older, you can install it from source instead, and you still don't need to remove Gaim.

While ubuntu-desktop is only a metapackage, it is not advisable to uninstall it as there may be updates to this package, which would not occur if ubuntu-desktop is removed.

As for why these packages are forcefully removed when you try to remove Gaim, it's because each of these packages DEPEND on the gaim package. This is not a bug, and it will not be changed until Gaim is fully replaced with Pidgin (my guess is Gutsy Gibbon).

---

### Post by october1917 on 2007-05-05
I compiled the pidgin, using -in the last step- checkinstall  to build the final .deb package. While i try to install it, a conflict message appears in the details area of gdebi. When it tryies to replace the `/usr/bin/ld' file, which is also a binutils package. An after that is says dpkg-deb: paste killed by the signal (Broken pipe).

So there will not be any way to uninstall GAIM and install pidgin avoiding to lose anything? You think we have to wait until october?

It is imortant to me to substitute GAIM because it doesn't function well. Very often, many messages i send does never reach the recipient, and many other times my friends send me messages that i never get. And it happens only while using GAIM!!!

---

### Post by hyperair on 2007-05-05
Firstly, I also experienced the same problems regarding checkinstall. Just run a ```
sudo make install
```. Checkinstall for some reason has some bug compiling Pidgin.

Also, read your error messages carefully. It said that there is a conflict with binutils **_NOT**_ Gaim. /usr/bin/ld is also obviously not included as part of the Pidgin package, so checkinstall has generated a faulty DEB. 

[quote=october1917]So there will not be any way to uninstall GAIM and install pidgin avoiding to lose anything? You think we have to wait until october?[/quote]
You obviously did not read my previous post properly. I mentioned, "You DO NOT need to uninstall Gaim to install Pidgin". Anyway there is no way to uninstall Gaim without losing anything, but there is a way to install Pidgin alongside Gaim. Like I mentioned, no conflicting files.

---

