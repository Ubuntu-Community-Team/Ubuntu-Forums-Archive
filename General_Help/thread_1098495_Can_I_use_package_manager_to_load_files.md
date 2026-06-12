---
title: "Can I use package manager to load files?"
date: 2009-03-17
forum: General Help
---

### Post by Scooter1962 on 2009-03-17
I need to download madwifi and nsdiswrapper so I can get my wireless connection up and running.
Naturally I can't download them, because my wireless connection (and wired connection) will not work.

I've downloaded the files onto a usb stick AND a cd, but cannot get the package manager to see either, despite checking various permission boxes and so on.

Any clues on how to load programs without an internet connection?

A comment at this point - the problems with wireless connectivity in Linux seems to be widespread and common - is there a global fix?

---

### Post by Berserker v7 on 2009-03-17
If you haave downloaded the .deb files(with all the dependencies) corresponding to the version pointed to by apt, then you can copy all those files to /var/cache/apt/archives and execute sudo apt-get install ndiswrapper from the terminal...

---

### Post by 3rdalbum on 2009-03-17
> **Berserker v7 said:**
> If you haave downloaded the .deb files(with all the dependencies) corresponding to the version pointed to by apt, then you can copy all those files to /var/cache/apt/archives and execute sudo apt-get install ndiswrapper from the terminal...

Or, you know, just double-click them :-P

Ubuntu has a kind of off-line package installer program which should be triggered whenever you double-click a package file. I say "kind of" because it will try to download dependencies from the Internet, if any are needed. The installer is called "gdebi", so if it isn't the default handler for .deb packages, you will find it in your right-click>Open With list.

If you double-click the "ndis-gtk" package or whatever it's called, it will probably say that it requires one other package or a few other packages. If you click "Details", it tells you what other packages it needs. Close the window and double-click one of those packages in your file browser (if you don't have it, you need to download it and transfer to your Ubuntu computer), and it will probably tell you that this package can be installed. So install it, and install all the packages that the main package depends on.

Once all the dependencies are installed, you can install the main package.

As for your other question, there is no problem with Linux's ability to use a wireless connection. Some wireless cards are not supported yet, and some have official drivers that are truly terrible (I'm looking at you, Broadcom...). Many, even most, wireless cards are supported out-of-the-box or with a simple driver install on Ubuntu.

The reason why it looks like there's a widespread problem is because nobody posts to a support forum and says "Help! My wireless is working!". :-)

---

### Post by Scooter1962 on 2009-03-17
thanks for the tips folks.  I'll reload ubuntu and take another run at it.

I agree about the lack of 'wow my wireless is working' posts, and I must say, the help files in ubunu are excellent - I just keep hitting a bump in the road that slows me down. 
I'll let you know how I go.

again - thankyou

---

