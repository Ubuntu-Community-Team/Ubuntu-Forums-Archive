---
title: "SNES9X no longer after upgrade to 13.10"
date: 2013-10-20
forum: Emulators
---

### Post by mcse2000ca on 2013-10-20
was working fine in 13.04 but after the upgrade i can open it but after i go into preferences and press ok or try choosing a ROM it will go to a greyish black screen and can only close it by right clicking and forcing to quit the program.
I have downloaded zsnes and it works fine just a personal preference towards snes9x, (find the sound engine superior in it)

---

### Post by techzilla2 on 2013-11-03
I also prefer snes9x to zsnes, for multiple reasons, but the most underated is it's portability!.  They should have never removed the package, soon after lucid's release.

I'll post back with the a working build link soon as I get one,
May have to get one on my own ppa built if none is appropriate, but I'm on the job!

---

### Post by techzilla2 on 2013-11-03
I've concluded that a snes9x 13.10 package doesn't exist, Brandon's [PPA]("https://launchpad.net/~bearoso/+archive/ppa") packages are missing a 13.10 build. Continuing to build with GTK 2 felt ridiculous, as GTK 3 support is relatively ready for usage, so porting his last 13.04 package was far from ideal.

I've taken a fresh git clone, from what I believe is [upstream]("https://github.com/snes9xgit/snes9x"), and verified it would compile --with-gtk3.  I'm now in the process of uploading my quickly assembled package, for building on my ppa.  I've encountered a couple errors, but I believe I should have this done in a couple hours (assuming I get a reasonable launchpad buildwait)

---

### Post by techzilla2 on 2013-11-03
My fresh packages are listed as '**Pending publication'**, but I assume that means they'll be ready shortly.  I downloaded my amd64 build, and manually installed it with 'dpkg -i', and it appears to be working as expected.  So, to get the ball rolling I thought I'd just provide my link now, and just keep in mind they may not be available in apt if you found this message moments after I posted.

My PPA is, 
[https://launchpad.net/~techzilla/+archive/misc](https://launchpad.net/~techzilla/+archive/misc)

Or for your convenience, ```

sudo add-apt-repository ppa:techzilla/misc

```

After my ppa has been added to your sources,

```

sudo apt-get update
sudo apt-get install snes9x-gtk

```

---

### Post by Drake.Tempestos on 2013-11-05
> **techzilla2 said:**
> My fresh packages are listed as '**Pending publication'**, but I assume that means they'll be ready shortly.  I downloaded my amd64 build, and manually installed it with 'dpkg -i', and it appears to be working as expected.  So, to get the ball rolling I thought I'd just provide my link now, and just keep in mind they may not be available in apt if you found this message moments after I posted.

My PPA is, 
[https://launchpad.net/~techzilla/+archive/misc](https://launchpad.net/~techzilla/+archive/misc)

Or for your convenience, ```

sudo add-apt-repository ppa:techzilla/misc

```

After my ppa has been added to your sources,

```

sudo apt-get update
sudo apt-get install snes9x-gtk

```

Using Xubuntu 13.10 (x86, fresh install)

Crashed on the first rom load, then worked on the second try. Only a few  settings (like the FPS limit) were strange, but I've adjusted it.

Thank you very much!

---

### Post by techzilla2 on 2013-11-05
> **Drake.Tempestos said:**
> Using Xubuntu 13.10 (x86, fresh install)

Crashed on the first rom load, then worked on the second try. Only a few  settings (like the FPS limit) were strange, but I've adjusted it.

Thank you very much!


I'm very happy to hear it's working as expected, I also tested a few ROMs and thankfully it picked up my previous gamepad settings.

---

### Post by mcse2000ca on 2013-11-06
Appreciate the attempt not working in Unity gnome however hehe funny how games from 20 years ago still captivate us isnt it hehe

---

