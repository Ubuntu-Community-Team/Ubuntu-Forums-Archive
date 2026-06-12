---
title: "Setting up flashplugin-nonfree"
date: 2006-05-31
forum: Desktop Environments
---

### Post by mempf on 2006-05-31
I am having problems with the package flashplugin-nonfree on my laptop.

Whether or not I install it from syaptic, apt-get command or from automatix for dapper it all hangs at "Setting up flashplugin-nonfree"

Can anyone help me out with this?

(Note I know of the alternate install methods like the tar.gz from their site but it is important I get flashplugin-nonfree working)

Thanks

---

### Post by an.echte.trilingue on 2006-05-31
Click on the "show details" button.  There is a license agreement you have to agree to.

I find it is easier to install it from the command line:

```
sudo apt-get flashplugin-nonfree
```

---

### Post by missmoondog on 2006-05-31
i installed it through the breezy repository's. it just updated itself within the past couple days also.

---

### Post by Sef on 2006-05-31
Did you add the repositories?  If not, [click here.]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by aurelieng on 2006-05-31
Be careful, as [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/35942](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/35942) :(

---

### Post by stubby on 2006-06-01
When it says it's "setting up"
it's actually downloading the file. So depending on the speed of your internet connection it might take a while. Patience.

---

### Post by mempf on 2006-06-01
New devolopment, it seems even trying to download the tar version for adobes site is ultra slow.

Which maskes it seem to be some weird netowrk problem with my ubuntu. On my windows system i can download the linux tar just fine.

Just the ubuntu machines have the problem.

What could cause this to be occuring?

---

### Post by Ian Clark on 2008-05-25
I would highly recommend using **gnash** instead.  I use youtube a lot and using gnash fixed all of my flash problems.  I'm running Ubuntu 8.04 with FF3.0b5.

Go to system > synaptic > search.  Search "flash".  Find the two entries flashplugin-nonfree and libflashsupport and slate them for complete removal.  Click "apply".

Open up the terminal.  Run
> sudo apt-get install gnash
:guitar:

---

