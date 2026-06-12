---
title: "Trouble installing Unity Place Filesearch"
date: 2012-03-31
forum: Desktop Environments
---

### Post by Tornikee on 2012-03-31
Hello. I've been trying to install the Unity Place Filesearch ( [http://bit.ly/GZlvq1](http://bit.ly/GZlvq1) ) lens for the possibility of searching for all files (not just previously opened) via Unity. After entering the install command:
```
sudo apt-get install unity-place-filesearch
```a "E: Unable to locate package unity-place-filesearch" error appears. Does this mean the software source package does not exist anymore? And if yes, where else can I find it / which package can I substitute it with?

---

### Post by zombifier25 on 2012-03-31
You forgot the first two steps of the guide:
```
sudo add-apt-repository ppa:pydave/unity-lenses 
sudo apt-get update
```
The package you need to install can only be found in the PPA above.

---

### Post by Tornikee on 2012-03-31
Sorry, forgot to mention I entered those two too, they just didn't cause any error messages, so I didn't include them in my post.

---

### Post by Krytarik on 2012-03-31
> **Tornikee said:**
> ... a "E: Unable to locate package **unity-place-filesearch**" error appears. Does this mean the software source package does not exist anymore? And if yes, where else can I find it / which package can I substitute it with?
The author has changed the name of the package since WebUpd8 posted about it in May last year, to **"unity-filesearch-lens"**; plus there wasn't ever a package with that old name for Oneiric 11.10.

Source: [https://launchpad.net/~pydave/+archive/unity-lenses]("https://launchpad.net/%7Epydave/+archive/unity-lenses")

Regards.

---

### Post by Tornikee on 2012-04-01
Thanks a lot.

---

### Post by Tornikee on 2012-04-02
Is there similar extension for GNOME? Couldn't find one.

---

### Post by stevenswall on 2012-10-23
Bump. Has anyone had success recently with this? I'm on 12.04, and the repository no longer seems to work. Is there a way around this or a .deb I could download?

---

### Post by Tornikee on 2012-10-24
> **stevenswall said:**
> Bump. Has anyone had success recently with this? I'm on 12.04, and the repository no longer seems to work. Is there a way around this or a .deb I could download?
While I'm not sure how you could solve this, I myself have switched to using *[Synapse]("http://bit.ly/SsOvM3")* for this need. Check it out.

---

