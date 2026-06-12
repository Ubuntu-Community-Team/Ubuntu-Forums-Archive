---
title: "Mint 7 (Gloria) menu style and options on Ubuntu Jaunty"
date: 2009-07-20
forum: Desktop Environments
---

### Post by ramnarayan on 2009-07-20
Hi

recently i had Linux Mint 7 Gloria (based on Jaunty) installed for a few days. I really loved it the color themes and especially the way the menu was organized. I uninstalled it because i could not get the touchpad working.

Now i want to have the Mint way the menu is organized ?? and possibly the really nice cool mint theme 

any idea how to do it

is it possible to have Mint repos accessible on Ubuntu Jaunty

thanks

---

### Post by ibutho on 2009-07-20
One option could be to setup the Mint 7 apt repos in /etc/apt/sources.list and then do
```
sudo apt-get update
sudo apt-get install mintmenu

```

The repos are
```

deb http://packages.linuxmint.com/ gloria main upstream import
deb http://packages.linuxmint.com/ gloria backport
deb http://packages.linuxmint.com/ gloria community
deb http://packages.linuxmint.com/ gloria romeo
```

---

### Post by ramnarayan on 2009-07-20
i need the gpg public key ??
any idea where that is ??

EDIT:
one of the repos seems to be failing after trying apt-get update

---

### Post by ramnarayan on 2009-07-20
this the error i get
> Fetched 8067B in 5s (1416B/s)
Reading package lists... Done
W: GPG error: [http://packages.linuxmint.com](http://packages.linuxmint.com) gloria Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EE67F3D0FF405B2
W: You may want to run apt-get update to correct these problems
ram@ram-laptop:~$ 


tried apt-get update and get the same error


However it seems i have been able to install the theme and even mintdesktop, from the remaining working repos.

The next question is : which asked me to uninstall ubuntu-desktop 

so my machine is still on, not rebooted so am wondering should i undo the install and reinstall ubuntu-desktop i don't want to break this system

---

### Post by ibutho on 2009-07-20
ubuntu-desktop is just a metapackage that you can reinstall later if you decide you do not want the mintdesktop stuff.

---

### Post by ramnarayan on 2009-07-20
thanks

**
want to say

ooooh, i have mint themes - so cool and nice in this hot dry indian summer and jaunty at the back veru nice

---

### Post by ibutho on 2009-07-20
I'm glad you got it to work. ;)

---

### Post by ramnarayan on 2009-07-20
yep, thanks

---

