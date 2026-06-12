---
title: "Manual Updates Download"
date: 2009-05-15
forum: General Help
---

### Post by 6205 on 2009-05-15
Hi,

I have one ubuntu 9.04 desktop without internet connection where i want to install updates from repos jaunty-security, jaunty-updates, jaunty-proposed and jaunty-backports

But issue is, i don't know from where they are available for download. Is there some kind of FTP or something to download entire directory content, all packages of for example jaunty-updates?

When i download those packages i will simply install them with sudo dpkg -i *.deb

---

### Post by dcstar on 2009-05-15
> **6205 said:**
> Hi,

I have one ubuntu 9.04 desktop without internet connection where i want to install updates from repos jaunty-security, jaunty-updates, jaunty-proposed and jaunty-backports

But issue is, i don't know from where they are available for download. Is there some kind of FTP or something to download entire directory content, all packages of for example jaunty-updates?

When i download those packages i will simply install them with sudo dpkg -i *.deb

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by 6205 on 2009-05-18
Thanks i know that site, but i cannot download them all together.

---

### Post by s3a on 2009-05-18
I'm not sure if the Ubuntu DVD would have this but if it's like Debian (if it's not maybe you should consider Debian since Ubuntu is based off it) then you can download (a) DVD(s) and use that as an offline repository so when you do lets say apt-get install pidgin, it will search for the pidgin .deb as well as its dependencies from the disc(s) then install them for you.

IF the Ubuntu DVD is like Debian then it's here: [http://cdimage.ubuntu.com/releases/jaunty/release/](http://cdimage.ubuntu.com/releases/jaunty/release/)
Debian has 5 DVDs though since it's repository is larger. You'll have to confirm yourself though if that DVD actually contains the rest of Ubuntu's repositories or if it's just an .iso made for a DVD disc without benefit.

Edit: Oops! I just realized you wanted to update instead of just installing packages! (I think Ubuntu only updates the .iso files of its LTS releases)

---

### Post by bobbocanfly on 2009-05-18
Debs can be pulled directly off the mirrors (over HTTP), you just have to have the correct address. For example, the latest firefox-3.0-branding package from jaunty-updates is at:

[http://cz.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.10+nobinonly-0ubuntu0.9.04.1_i386.deb](http://cz.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.10+nobinonly-0ubuntu0.9.04.1_i386.deb)

You could probably write a quick python script that would do this for you (if you can write Python, that is).

---

### Post by zvacet on 2009-05-18
You can try [Keryx.]("http://crashsystems.net/2009/01/keryx-tutorial/")

---

### Post by EXCiD3 on 2009-05-18
Like zvacet mentioned, Keryx does that and much more. Once a project is created, you go to a computer with highspeed internet, load the project, hit Get Updates and it lists every update that is available and downloads them all for you. It also lets you do everything Synaptic from a separate computer such as downloading new software and packages for your offline machine.

---

### Post by Cheesemill on 2009-05-18
+1 for Keryx

---

