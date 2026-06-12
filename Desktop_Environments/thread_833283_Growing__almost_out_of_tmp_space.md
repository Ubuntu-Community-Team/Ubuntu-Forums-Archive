---
title: "Growing / almost out of /tmp space"
date: 2008-06-18
forum: Desktop Environments
---

### Post by wordsmithereens on 2008-06-18
I'm trying to download a small file. I get this message:

"There is not enough room on the disk to save /tmp/F2OOgu26.deb.part.

Remove unnecessary files from the disk and try again, or try saving in a different location."

It seems that my "/" has grown to almost 30 gig in just a few weeks. 

Any suggestions as to where I can start looking to delete files in "/" to free up some space? 

"/" is 30 gig
/home is 60 gig.

Thanks!

---

### Post by playalpha on 2008-06-18
(I re-posted to new thread, didn't mean to hijack...)

I am experiencing a similar problem.

I had Hardy installed on a 70G partition for about a month when it ran out of space (which I found out when I couldn't download a small picture.)

I did install a lot of software that I didn't really need, so I tried removing unneeded apps and old kernel-images with synaptic. Nautilus still showed 0 bytes available.

I then used gparted to increase the main partition to 110G with a separate 20G home partition. Once I completed that I rebooted some time later, but WHAMO! new 110G system partition is full (after copying old 70G to it with gparted).

It appears that every time I make more room, the system expands to fill the empty space.

Any help is appreciated...

---

### Post by prshah on 2008-06-18
> **wordsmithereens said:**
> 
It seems that my "/" has grown to almost 30 gig in just a few weeks. 

Any suggestions as to where I can start looking to delete files in "/" to free up some space? 


```
sudo apt-get clean
``` will clear up a lot of space by deleting downloaded update packages. (Will not affect your computer in any other fashion).

You can also delete all files in your "/tmp" directory but it's better if you do this through a live CD or in recovery mode. You can also delete all files from your "/var/log" directory.

All said and done it's a bit strange that you're using 30Gb in "/"; I have no problems on a 10Gb "/" with 140gb "/home". Are you actually using 30Gb or have you just run out of inodes?```
df -i
``` will give you a clue.

---

### Post by wordsmithereens on 2008-06-18
I thought it was plenty of space too. Inodes are at 10%.  I'll try the other items a little later.

What bugs me is that it seems to be a sudden loss of a LOT of free space, and I'm new enough to Linux to not know for certain what is or isn't OK to delete.

Thanks for the direction. I'll post back results when I get them. 

wordsmithereens

---

### Post by VMC on 2008-06-18
> **wordsmithereens said:**
> I'm trying to download a small file. I get this message:

"There is not enough room on the disk to save /tmp/F2OOgu26.deb.part.

Remove unnecessary files from the disk and try again, or try saving in a different location."
!

Try deleting /tmp files. If a file is being used it will be locked out anyway. How much space does your /tmp comsume:

```
du -h /tmp
```

---

### Post by wordsmithereens on 2008-06-19
... not much at all. 6 meg in /tmp.

I've cleared /tmp and /var/log. That only totalled 150 meg or so. Which is what I'd expect. I think the usual suspects are out of the picture here. 

> **VMC said:**
> Try deleting /tmp files. If a file is being used it will be locked out anyway. How much space does your /tmp comsume:

```
du -h /tmp
```

---

### Post by prshah on 2008-06-19
> **wordsmithereens said:**
> ... not much at all. 6 meg in /tmp.

I've cleared /tmp and /var/log. That only totalled 150 meg or so. Which is what I'd expect. I think the usual suspects are out of the picture here.

Try```

du -h /var/cache/apt/
sudo apt-get clean
du -h /var/cache/apt/

```

Or "autoclean" instead of "clean" if you'd like to be other the safer side.

---

