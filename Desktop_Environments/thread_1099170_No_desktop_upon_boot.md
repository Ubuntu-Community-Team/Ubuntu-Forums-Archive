---
title: "No desktop upon boot"
date: 2009-03-17
forum: Desktop Environments
---

### Post by solracarevir on 2009-03-17
Hi, I have just booted a fresh install of Kubuntu 9.04 alpha6 and once kubuntu boots (After logging in successfully)  I only get a black screen, I can move my cursor, i get therun prompt if I press alt + f2 and can run apps like konsole, k3b, notification dialogs works, even Dolphin WM works, still I got no panel. 

I did some research and folowed some advice like erasing the .kde folder & disabling compositing with ```
kwriteconfig --group Compositing --key Enabled --file kwinrc false
```And still got no panel, any Idea???? I really want to give KDE another try cause I havent tried it since the initial KDE4 release, but with so many issues maybe i should stick with xfce.

---

### Post by MST3Kakalina on 2009-03-17
I'm having the same problem.  I had managed to install kde4 fine in the past but hated it; now that it seems kubuntu is more or less abandoning 3.5 I'd like to actually switch, but now I can't.

I tried from apt and also following the instructions here: [http://www.ubuntugeek.com/how-to-install-kde-41-on-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-install-kde-41-on-ubuntu-810-intrepid-ibex.html)

---

### Post by solracarevir on 2009-03-18
The funny fact is that I have three Laptops here @ home and I´m having the same issue on all of them

HP Compaq nc6220
HP zv 5000 series
Dell Inspiron 1501

---

### Post by iamkrazee on 2009-03-18
Try restarting KDM from tty1 ```
sudo service kdm restart
```

---

### Post by MST3Kakalina on 2009-03-18
I don't know if this is the best or easiest hack, but this is what I did.

I purged KDE from my system entirely, kde3 AND kde4.  I just tooled around in Gnome and used Synaptic Package Manager to make sure every last bit of kde stuff was cleaned up, since apt-get purge $kde_related_package didn't do the trick entirely.  Then I installed kubuntu-kde4-desktop with apt-get; there are some minor broken dependencies (with okular, for one) but if you apt-get install them individually they work fine.

I'm now posting from 4.1 without any real software problems, just a couple cosmetic ones.

---

### Post by solracarevir on 2009-03-18
> **iamkrazee said:**
> Try restarting KDM from tty1 ```
sudo service kdm restart
```


No luck restarting KDE from tty1, now Im uninstalling the whole KDE desktop and installing it again

---

### Post by D3ath on 2009-03-18
Has anyone tried kicking it?

---

### Post by solracarevir on 2009-03-18
No luck yet, maybe I should wait for the Final Release.

---

### Post by Zorael on 2009-03-18
What's happening is probably Plasma crashing. I've seen a few threads covering this with suggestions that may or may not work.

[http://ubuntuforums.org/search.php?searchid=56884064](http://ubuntuforums.org/search.php?searchid=56884064)

---

