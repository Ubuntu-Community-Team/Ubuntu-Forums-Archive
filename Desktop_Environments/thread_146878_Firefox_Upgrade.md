---
title: "Firefox Upgrade"
date: 2006-03-19
forum: Desktop Environments
---

### Post by randal on 2006-03-19
I'm still using the Firefox that came out-of-the-box with my Ubuntu install, which is the 1.0.7 version. I've been waiting for it to detect updates but until now, it doesn't report anything. I don't know how to make it detect updates. So I downloaded the latest version from mozilla.com. I tar'red it, then from the directory, I ran it. It's fine. But I want it to be a "system-wide" updgrade so that, when I refer to Firefox on my system, I would mean the 1.5 version. 

How do I do this?

By the way, I tried to "mak for upgrade" my Firefox on synaptic but it's not available (the menu item is gray). I guess I don't have the reference to the repository that contains the update.

---

### Post by dermotti on 2006-03-19
Hmm

try from command line.


sudo apt-get update
sudo apt-get install firefox

---

### Post by 5-HT on 2006-03-19
FireFox 1.5 will not be available in the breezy repos (just part of the Ubuntu philosophy, and goes for all programs released after a version release).

If one wants a nice .deb of newer apps, backports is usually the best way to go (that or compiling and crossing your fingers).

Unfortunately, this is not possible with the new FireFox as a system-wide install would cause lots of problems for a bunch of apps relying on the old 1.0.7.

Best thing to do would be, as you have done, to grab the precompiled tarball from the mozilla site.

If you want to make a quasi-system-wide install you can just follow the section in this wiki page around 1/3 of the way down starting with
[quote=FirefoxNewVersion from ubuntuwiki] To ensure it is used as the default **version**, modify the symbolic link in /usr/bin...
[/quote] 
[https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion") 

HTH

---

