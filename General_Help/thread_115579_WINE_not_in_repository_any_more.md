---
title: "WINE not in repository any more?"
date: 2006-01-10
forum: General Help
---

### Post by Timokl on 2006-01-10
I tried to install Wine on my Ubuntu Breezy 64Bit installation. I added the wine repositories into Synaptic as described on [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb). Then I updated the repository listing with

```
sudo apt-get update
```

Then I tried to install it with

```
sudo apt-get wine
```

But it seems, that the wine package is not in the repository any more. I get the following response:

```
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/universe Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/multiverse Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate
```

Where do I find a the installation file.

Thank you!
Timo

---

### Post by aysiu on 2006-01-10
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by BoyOfDestiny on 2006-01-10
The command is wrong, isn't it? It's 

sudo apt-get install wine.

Although I guess you would have gotten an error about it... Oh well...

Anyway, sudo gedit /etc/apt/sources.list

Comment out the cdrom with #

then uncomment the lines (by removing #) where you see breezy main restricted multiverse universe etc etc

Err... I noticed you mentioned amd64, I think you have to try to force installing it, and it should work through emulation libs... But that's another matter I guess... Good luck! (I'm on dapper amd64, but I haven't tried running wine)

In that case, try downloading the .deb file from wine's site. Then type sudo dpkg --force-all -i nameofthedeb.deb
see if that works... If not check the forums for a great how-to for chroot

---

### Post by o_fortuna on 2006-01-10
Hmm... I didn't think that Wine worked in Breezy64, as in, no one could compile it?

Definitely comment out the cdrom though, since half of the packages are out of date (because of security updates), so it's not really that useful anyway. Then run sudo apt-get update and try again. Like I said, though, I don't know if this would work since Wine doesn't officially run on 64-bit systems (to the best of my knowledge.

---

### Post by mztriz on 2006-01-10
```
sudo apt-get install wine
```

---

