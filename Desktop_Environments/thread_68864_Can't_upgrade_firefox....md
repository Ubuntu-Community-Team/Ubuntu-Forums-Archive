---
title: "Can't upgrade firefox..."
date: 2005-09-24
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-09-24
I tried to upgrade firefox to 1.0.7 through synap and this is the error that I got at the end of the installation process...
```
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
```

---

### Post by evilghost on 2005-09-24
I had the same exact issue, and the fix is pretty easy :)

In Terminal:

```

cd /var/cache/apt/archives
sudo dpkg -i --force-all mozilla*1.07*.deb

```

That should fix it.

---

### Post by imagine on 2005-09-24
Or use the search function to find this thread: [http://ubuntuforums.org/showthread.php?t=68530](http://ubuntuforums.org/showthread.php?t=68530)


If "**sudo dpkg --install --force-all mozilla*1.07*.deb**" gives you a lot of errors because you tried to update also other applications together with firefox, just do a **sudo apt-get install** afterwards.

Remember to kill firefox with "**killall firefox-bin**" if a broken, not visible instance of it is still running in the background. Unlike other users suggested, you do not have to reboot Ubuntu just to stop firefox-bin :)

---

### Post by YourSurrogateGod on 2005-09-24
Nice, thanks guys.

---

### Post by Grafster on 2005-09-24
[QUOTE=evilghost]I had the same exact issue, and the fix is pretty easy :)

In Terminal:

```

cd /var/cache/apt/archives
sudo dpkg -i --force-all mozilla*1.07*.deb

```

That should fix it.[/QUOTE]
 I actually had to use the individual file names but... thank you!!!
Saved much frustration.

---

### Post by crane on 2005-09-24
Thanks  :)

---

