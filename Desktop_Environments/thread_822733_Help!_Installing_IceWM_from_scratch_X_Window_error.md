---
title: "Help! Installing IceWM from scratch: X Window error?"
date: 2008-06-08
forum: Desktop Environments
---

### Post by oleksus on 2008-06-08
Hi!

I have installed Hardy command line version, configured xorg, tried xstart (it works), but as I try to ./configure IceWM it says that

```

error: X Window System or development libraries not found. Make sure you have headers and libraries installed!

```

What do I have to install to make it work?

---

### Post by Happy_Man on 2008-06-08
I believe the package you need is libx11-dev.

---

### Post by oleksus on 2008-06-08
Aha, thanks.

How can I install it with all dependencies using only cdrom added to aptitude? (no internet at the moment)

I tried dpkg but it doesnt haul the dependencies.
Aptitude?
What's the command line for installing a library from, say a mounted directory?

Thanks again!

---

### Post by Happy_Man on 2008-06-08
Well, if you stick a livecd in, Ubuntu should automatically pick it up and ask whether you want to use it as a repository. I'm not sure whether libx11-dev is on there, though. Try it and see.

Also, are you trying to install it manually? Forgive me if you're not, but it is what your previous post is leading me to think. If you are, there is an easier way by means of ```
sudo apt-get install libx11-dev
```

---

### Post by urukrama on 2008-06-10
I've never had Ubuntu ask me automatically whether I wanted to add a cd to my repositories. Perhaps that is a Gnome thing?

If you have a command-line install, or would like to do it from the terminal, use the following command to add a cd to your repositories:

> sudo apt-cdrom add

It will ask you to insert the cdrom in your drive and press enter. The cd should then automatically be part of your repositories.

Do then:

> sudo aptitude update
sudo aptitude install *whatever package you need to install*

I don't think libx11-dev is on the install cd, though (I checked, but didn't see it). If you don't have internet access, you could try using [APTonCD]("http://aptoncd.sourceforge.net/") or [NoNetDebs]("http://nonetdebs.unixpod.com/"). I haven't tried either of them, but they should work.

---

