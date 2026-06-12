---
title: "Best way to use/install Budgie"
date: 2019-06-12
forum: Desktop Environments
---

### Post by arabian.gabe on 2019-06-12
I have been using Budgie for about 6 months now. I downloaded and installed vanilla/plain Ubuntu 18.04 from the Ubuntu website and then about 4 months later I switched to the Budgie Desktop environment by installing it from the command line using:

```
sudo apt install ubuntu-budgie-desktop
```

I see that there is now a complete Budgie distro ISO available for download from ubuntubudgie.org. I was just wondering if there is added benefit/stability in using this distro as opposed to continuing with the desktop environment (is it a shell?) as I have been doing.

---

### Post by deadflowr on 2019-06-12
Less cruft. That a benefit.
Ubuntu Budgie has it's own set of applications and Ubuntu(vanilla) has it's own set of applications.
Some overlap both and some don't.
Installing from the budgie iso will remove those applications that Ubuntu has but Budgie doesn't.
So less cruft.

Of course you can also always attempt the remove the cruft from Ubuntu (vanilla) manually.
But a quick iso download and reinstall is so easy to do.

I assume you've been making backups of your data.

---

### Post by Frogs Hair on 2019-06-12
By installing from the iso you eliminate the bloat associated with running two desktops. The newer versions of Budgie include the Nemo file manager which many prefer to Nautilus , but  Budgie 18.04 includes Nautilus. If all is running well you may find no reason to reinstall. I ran Budgie as you are with no problem until making the switch. If you don't reinstall I would suggest adding the following PPA.

  
[https://launchpad.net/~ubuntubudgie/+archive/ubuntu/backports](https://launchpad.net/~ubuntubudgie/+archive/ubuntu/backports)

---

### Post by cruzer001 on 2019-06-12
> **deadflowr said:**
> Less cruft. That a benefit.
Installing from the budgie iso will remove those applications that Ubuntu has but Budgie doesn't.

The ubuntu-budgie metapack is easy enough to find, but is there the same or similar list of packages for budgie?

---

### Post by cruzer001 on 2019-06-12
The latest budgie-desktop is 10.5 and used in ubuntu release 19.04.  If you want the latest you could upgrade.  I have budgie 18.04 running on a old computer and happy with it.  I wouldn't expect too much since your on the 10.4 desktop, but then I haven't tried it.

If I wanted it lighter, with less crud I would do a mini install and..
```
sudo apt install gnome budgie-desktop
```
Or take it down another notch with gnome-core package.  That package will boot out of the box without additional packages needed.
And what you now have is gnome-budgie-desktop
I have not tried this, but it does look good on paper :)

[https://packages.ubuntu.com/disco/ubuntu-budgie-desktop](https://packages.ubuntu.com/disco/ubuntu-budgie-desktop)

[https://packages.ubuntu.com/disco/budgie-desktop](https://packages.ubuntu.com/disco/budgie-desktop)

---

### Post by arabian.gabe on 2019-06-13
Thanks for the advice! I frequently back up everything (I'm a graduate student and panic that I will lose all my data someday haha) and enjoy keeping things fresh so I believe I will go ahead with the dedicated Budgie install since I have been noticing minor inconveniences lately...I get a system error message at almost every boot related to Budgie and now my Livepatch has started acting up. I'll see if these problems go away with a fresh install.

---

### Post by cruzer001 on 2019-06-13
A fresh install is a very nice way to start off.  Be sure to backup your data.

---

