---
title: "Bios issue..."
date: 2009-04-21
forum: General Help
---

### Post by youknowwhat4q on 2009-04-21
So I almost feel like I'm asking Jews about Jesus, but I'm not a member of any windows forums so here goes.

It is my girlfriends grandfathers computer and I am attempting to reinstall windows because a virus wiped it out (before anyone says it, yes I have suggested linux and let him play around on a few live versions, but he want windows back).

I have already backed up all of his files and while trying to run a boot disk it tells me that the selected boot device is not available.  So I head in to the bios to correct this and ta-da it is password protected.

No one knows the password, so I attempt to clear it in all of the non-software related ways I know of (jumpers, battery removal), but the password just will not go away.  So I attempt all of the possible backdoor passwords I can find with no luck from any of them.

Any one who can shed some light on this situation would be a saint in my eyes.  Thanks for reading, specs below.


> Dell Dimension E310 (DV051)
Currently running- Windows XP Media Center Edition 2005

 Intel Pentium 4 521 / 2.8 GHz  (64 bit)

 Intel 915GV Express Motherboard

Phoenix Rom Bios Plus Version 1.10 A03 

[Full Specs]("http://reviews.cnet.com/desktops/dell-dimension-e310-pentium/4507-3118_7-31594474.html?tag=mncol;rnav")

---

### Post by sailthesea on 2009-04-21
"No one knows the password, so I attempt to clear it in all of the non-software related ways I know of (jumpers, battery removal), but the password just will not go away.  So I attempt all of the possible backdoor passwords I can find with no luck from any of them."

 Keep trying with the jumper/battery options I think . It should 
work eventually
 Other than that unless anyone here has specific insider info you'd best call Dell and blag it!

Edit : And check the post below I had a quick look and it's quite clear

---

### Post by fballem on 2009-04-21
> **youknowwhat4q said:**
> So I almost feel like I'm asking Jews about Jesus, but I'm not a member of any windows forums so here goes.

It is my girlfriends grandfathers computer and I am attempting to reinstall windows because a virus wiped it out (before anyone says it, yes I have suggested linux and let him play around on a few live versions, but he want windows back).

I have already backed up all of his files and while trying to run a boot disk it tells me that the selected boot device is not available.  So I head in to the bios to correct this and ta-da it is password protected.

No one knows the password, so I attempt to clear it in all of the non-software related ways I know of (jumpers, battery removal), but the password just will not go away.  So I attempt all of the possible backdoor passwords I can find with no luck from any of them.

Any one who can shed some light on this situation would be a saint in my eyes.  Thanks for reading, specs below.



[Full Specs]("http://reviews.cnet.com/desktops/dell-dimension-e310-pentium/4507-3118_7-31594474.html?tag=mncol;rnav")

I hope the information in this link will help: [http://www.tech-faq.com/reset-bios-password.shtml](http://www.tech-faq.com/reset-bios-password.shtml) Don't forget to read the whole article. You will probably be most interested in the hardware set at the bottom.

Regards,

---

### Post by youknowwhat4q on 2009-04-21
> **fballem said:**
> I hope the information in this link will help: [http://www.tech-faq.com/reset-bios-password.shtml](http://www.tech-faq.com/reset-bios-password.shtml) Don't forget to read the whole article. You will probably be most interested in the hardware set at the bottom.

Regards,

Thank you much it that is a good article.  Unfortunately I've tried most of those option, and have now retried them all, and attempted those that I had not attempted, with no luck.

---

### Post by youknowwhat4q on 2009-04-21
Good news and bad news...

The good news:
After repeatedly attempting to reset it via the jumper and battery I finally got a result.

The bad news:
Despite the fact that it verifies that the settings have been reset, the password is still not blank.

Perhaps it defaults to something...

Do I guess I forgot to post this so...

I called Dell and the solution that they tried to force down my throat was that the only way it could be fixed was by using their wonderful Dell Connect Application.  Despite the face that this computer no longer has an operating system.
haha

---

### Post by paradigm2 on 2009-04-21
> **youknowwhat4q said:**
> Good news and bad news...

The good news:
After repeatedly attempting to reset it via the jumper and battery I finally got a result.

The bad news:
Despite the fact that it verifies that the settings have been reset, the password is still not blank.

Perhaps it defaults to something...

Do I guess I forgot to post this so...

I called Dell and the solution that they tried to force down my throat was that the only way it could be fixed was by using their wonderful Dell Connect Application.  Despite the face that this computer no longer has an operating system.
haha

When you are using the jumpers and/or taking out the cmos battery, are you waiting at least ten minutes or so in between?

One person here: [http://en.community.dell.com/forums/p/19268865/19466005.aspx](http://en.community.dell.com/forums/p/19268865/19466005.aspx) suggests waiting 2 minutes, and failing that removing the memory and rebooting to force what he calls a "flash" (he must intend reset?).  I haven't heard of the later, but will pass it on to you just in case.

Also I would think if nothing else you could probably remove the actually bios chip physically and replace (likely requires soldering and de-soldering) it with a new one or a known non-password protected chip.

---

### Post by youknowwhat4q on 2009-04-21
> **paradigm2 said:**
> When you are using the jumpers and/or taking out the cmos battery, are you waiting at least ten minutes or so in between?

One person here: [http://en.community.dell.com/forums/p/19268865/19466005.aspx](http://en.community.dell.com/forums/p/19268865/19466005.aspx) suggests waiting 2 minutes, and failing that removing the memory and rebooting to force what he calls a "flash" (he must intend reset?).  I haven't heard of the later, but will pass it on to you just in case.

Also I would think if nothing else you could probably remove the actually bios chip physically and replace (likely requires soldering and de-soldering) it with a new one or a known non-password protected chip.

I've tried rather extended periods of time, and that is what helped (reset the clock and returned other setting to default).  I think I'm going to leave the battery out over night and sleep on it.  If no luck tomorrow then I'll just replace the bios chip.

Thank you all I'll keep you posted.

---

### Post by youknowwhat4q on 2009-04-22
...wow

I figured it out, on accident.  I left the password jumper to reset overnight, and in the morning when I turned it on, I was able to access the bios.
So I changed around the settings and got curious.

**I think** that they have the oddest system ever, where you have to have the jumper in the reset position while the computer is running in order to change/clear a password.

Hopefully this helps some one else in the future.

---

### Post by MVP86 on 2011-02-19
Sorry to resurrect a dead thread.

I found a site a few months ago that could  generate the master password for different BIOS (specifically Phoenix) from the lock-out code that is displayed after you fail to log in 3 times.  Unfortunately I forgot the site and lost the master password that I had written down.  My fiancee has been using Ubuntu for about a year and he suggested I ask around here as this community is very knowledgeable and helpful.  Do any of you know of a site that will list/generate such a password?

Thank you very much in advance!

---

