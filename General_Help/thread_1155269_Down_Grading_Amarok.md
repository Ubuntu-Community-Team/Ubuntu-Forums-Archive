---
title: "Down Grading Amarok"
date: 2009-05-10
forum: General Help
---

### Post by osc1882 on 2009-05-10
I have the newest version of Ubuntu and they upgraded my Amarok to the newest one. I now understand why people don't like the new vertion. I was wondering how I can downgrade to Amarok 1.X. I don't think I like the lay out of the new one and MY SOUND DOESN"T WORK (lol) with the new version. So it's kinda a big deal.

---

### Post by osc1882 on 2009-05-10
Anyone?

---

### Post by sandyd on 2009-05-10
add this to /etc/apt/sources.list, then apt-get update
```

deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main

```then ```
sudo apt-get install amarok-kde3
```note that this will not show up in kde4, but you can do this....

```

sudo apt-get -y install amarok
sudo rm /usr/bin/amarok
sudo rm /usr/bin/amarokapp
sudo rm /usr/bin/amarokcollectionscanner
sudo ln /opt/kde3/bin/amarok /usr/bin/amarok
sudo ln /opt/kde3/bin/amarokapp /usr/bin/amarokapp
sudo ln /opt/kde3/bin/amarokcollectionscanner /usr/bin/amarokcollectionscanner

```or simply do
```

sudo rm /usr/bin/amarok

```and add /opt/kde3/bin to your $PATH

---

### Post by osc1882 on 2009-05-16
I don't understand. Will these instruction also let me install the old version of amarok?

---

### Post by petterdyrdahl on 2009-06-03
> **osc1882 said:**
> I don't understand. Will these instruction also let me install the old version of amarok?

I just used Carlees post and it worked for me! I am now back to using Amarok1.4. The new version crashed constantly, but that might be a problem with the new KDE as I am running Amarok on Gnome (yeaah, I know, there is rhythbox for gnome, I just happen to like amarok better :P )

Anyway, if you are unfamiliar with the console, it might look a bit daunting at first. And you would probably have to install the gpg keys between step 1 and 2:

```
gpg --keyserver subkeys.pgp.net --recv 079A381C44869960D
gpg --export --armor 079A381C44869960 | sudo apt-key add -

```
Where the actual key (079A381C44869960) is one that you get when you try to do the apt-get update:

```
Fetched 432kB in 3s (132kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 079A381C44869960
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 079A381C44869960
W: You may want to run apt-get update to correct these problems

```

Hope this helps you like it did to me. :)

---

