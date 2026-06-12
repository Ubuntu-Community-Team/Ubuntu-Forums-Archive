---
title: "Downgrading Ubuntu"
date: 2006-02-21
forum: Desktop Environments
---

### Post by lean on 2006-02-21
Hello,
I have installed Dapper - which I thought would be fine for my tv server (vlc is _much_ faster). But unfortunately my tv card does not work in Dapper.

So now I am downgrading again, setting a higher pin for Breezy.

The problem is that Dapper has created a lot of packages that does not exist in Breezy, so Breezy can not downgrade these. This leaves conflicts with Breezy packages.

Is there any way to for ubuntu-desktop to install, and remove all programs that conflicts? At the moment I am removing the packages manually :/


The only packages I need for a functional Breezy system is the ubuntu-desktop package and a kernel, right?

---

### Post by newuser111 on 2006-02-21
are you trying apt-get dist-ugprade?

---

### Post by Kimm on 2006-02-21
if you want to try something realy drastic you could remove a package alot of other packages depend on (like glibc) and then apt-get ubuntu-desktop to install everything in the base system again.

```

sudo apt-get remove libglib2.0-0
sudo apt-get install ubuntu-desktop

```

The above command will generate a long list of applications to remove and if you feel the need, you can manually go through it.

There is no guarantee that it'll work.

PS.
If you decide to try: you probably want to do this from the commandline (CLI)

---

### Post by lean on 2006-02-21
newuser111:
Yes, I am doing an apt-get dist-upgrade. But with pinning, so it works like a downgrade (it actually says downgrading packages).

kimm:
That would be one solution. It would not be nice to loose ssh, since there is no screen or keyboard attached. I borrowed a screen and installed it with network boot. It would be a hazzle to go through that again ;)

---

