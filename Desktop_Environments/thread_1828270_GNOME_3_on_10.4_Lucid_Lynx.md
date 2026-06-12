---
title: "GNOME 3 on 10.4 Lucid Lynx"
date: 2011-08-18
forum: Desktop Environments
---

### Post by Zeki1 on 2011-08-18
Is there a way to get GNOME 3 on 10.4? Please tell how.

---

### Post by MARP1961 on 2011-08-19
I don't think this is possible. Either upgrade to 11.04 then do this: [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3]("http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3") or better still, wait until 11.10 (Oneiric Ocelot) comes out and install Gnome Shell from the Software Centre much more simply.

---

### Post by collisionystm on 2011-08-19
Quote from the site

> There's also a way to install gnome3 on 10.10 without building it!

WARNING: This version works but it's outdated!

sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds
sudo apt-get update
sudo apt-get install gnome3-session
I tested it on my laptop with 10.10 installed and it works fine. Gnome2 doesn't get deleted, you can choose the session before logging in. There's "Ubuntu Desktop" and "GNOME 3".

I haven't tested it on 10.04 yet, but it should work on 10.04 too.

I hope you enjoy your GNOME 3 on 10.10,

Daniel

---

