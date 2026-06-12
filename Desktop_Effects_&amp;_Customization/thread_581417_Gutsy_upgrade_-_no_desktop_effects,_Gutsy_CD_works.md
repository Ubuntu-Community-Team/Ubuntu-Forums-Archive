---
title: "Gutsy upgrade - no desktop effects, Gutsy CD works"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by wtw0Scoob on 2007-10-19
Hey guys,

I just upgraded from feisty to gutsy and found that desktop effects still don't work.  However, if I boot from the install CD and enable them, they will work, including wobbly windows and the whole deal.  I had used FGLRX in feisty, but seeing that the CD used the ATI driver, I tried to follow the wiki to remove fglrx and add ati (and mesaGL).  However, after all that, it still doesn't work.  I also tried to use Envy, which ended up not working either.  How do I revert to exactly what the install CD detected and get desktop effects working?  I'm on a mobility radeon x700.  I'm assuming the install CD did NOT use Xgl, is that correct?

Thanks

---

### Post by tombott on 2007-10-24
I have exactly the same problem.
Any ideas?

In the meantime I am going to look at my xserver config file from Feisty as this worked without any problems.

---

### Post by wtw0Scoob on 2007-10-24
I fixed this.  I went to restricted drivers manager and reticked, then unticked the ATI accelerated driver.  After a reboot, it showed up as 'not in use'.  Compiz then worked.

---

### Post by sajiv_k on 2007-10-30
I have a similar issue, upgraded from Fiesty to Gutsy and cant activate the desktop effetcs. 

Used to run Emerald on Fiesty without any hitches.

The video card is an on board one, on a 945 chipset.

---

