---
title: "stuck at 640x480"
date: 2007-03-10
forum: Desktop Environments
---

### Post by exigent on 2007-03-10
Not sure what happened, but I'm now stuck at this ridiculous resolution! System settings doesn't show any other resolution than 640x480, I've restarted X and still the same deal. I've tried reinstalling the nvidia drivers but that did nothing. 

Another error I was getting (not sure if it's related) was from synaptic package manager. It said there was a malformed line in /etc/apt/sources.list, the line was

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy
```

Even though I didn't change anything in the file at all. I just commented it out and it managed to fix it. Any thoughts? Is there a fallback or should I post a config file of mine?

---

### Post by CrazyGenie on 2007-03-10
> **exigent said:**
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy

Here is the sources.list to refer to:

# Main repository
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

# Update repository
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

# Security-updates repository
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

You may edit the entries in your sources.list as mentioned above and run;
apt-get update
apt-get -f dist-upgrade
apt-get -f install
(repeat the last two commands, untill you find no more upgrades)

Then run;
apt-get install ubuntu-desktop (if you want Gnome desktop environment)
apt-get install kubuntu-desktop ( if you want KDE)
apt-get install xubuntu-desktop (if you want XFCE)

---

### Post by exigent on 2007-03-10
no new updates, nothing changed. still stuck at 640x480


i did get 


```

W: GPG error: http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

```

---

### Post by exigent on 2007-03-10
finally fixed it i just had to do

**sudo dpkg-reconfigure xserver-xorg**

and select the resolutions

thanks though

---

