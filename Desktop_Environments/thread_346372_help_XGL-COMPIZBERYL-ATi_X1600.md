---
title: "help XGL-COMPIZ/BERYL-ATi X1600"
date: 2007-01-25
forum: Desktop Environments
---

### Post by immerohnegott on 2007-01-25
ok. I've been scouring this forum, and have found nothing. From what I gather the "radeon" driver doesn't yet support x1k series cards. Tried using fglrx, but fglrx doesn't support Composite and beryl won't start without composite (as far as I know). grr.
I've tried four different how-to's with no avail.

I DO have xgl running, at least.

Just wondering if anyone had gotten either Beryl or Compiz to run on an X1xxx radeon.

thanks a bunch.

---

### Post by immerohnegott on 2007-01-26
EDIT
got it working. finally. used SVN snapshots, and it's gorgeous. *cries*

---

### Post by Daergeth on 2007-01-28
How did you accomplish this? I also would like to get compiz working on my X1800 card.

---

### Post by harrycoal on 2007-04-21
I would also like to know how this is done, I'm using the ATI X1300.

---

### Post by immerohnegott on 2007-04-22
Apologies for not being more specific on how I fixed it.   What I ended up doing was installing fglrx (latest from ati.amd.com, not from the repo) and setting up an xgl session with the help of this thread:
[http://ubuntuforums.org/showthread.php?t=321766&highlight=how+to+xgl+session](http://ubuntuforums.org/showthread.php?t=321766&highlight=how+to+xgl+session)

once that was done, i restarted the machine and checked that xgl worked, logged out and back into reg'lar gnome and installed the bery-svn debs (these are experimental development files...I'm kind of a noob myself, so it's difficult for me to explain exactly...maybe pre-beta would cover it?)

they can be found at:

[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

i DID get it up and running, however I was unable to change the GTK themes on the windows (with xgl/beryl the only thing you can mess with would be Emerald window border).

Since that time however, I switched to an nvidia 7950, so I'm unsure of where fglrx is at right now. Since ATi has had at least two driver updates, there may be some significant linux driver updates (hopefully to the tune of AIGLX compatibility and composite being enabled).

good luck to you.

---

### Post by blamecanada on 2007-04-24
I was really looking forward to running Beryl on my desktop that has an 1800XT. Silly me thought that that would be cake compared to running it on my laptop w/ GMA945 graphics, oh how I was wrong. From what I've found the driver that supports composting doesn't support my card, and the driver that supports my card doesn't support composting. Has any progress been made in this area on AMD's part?

---

### Post by traffas on 2007-04-24
Beryl ran like a dream on my x1600 PCIe card on Edgy i386 - much, much better than my nVidia card.

I can't get fglrx to work with the x1600 under Feisty 64. Has anyone gotten an x1600 to work with Feisty 64-bit? I'm poking along with nVidia but it's frustrating.

---

