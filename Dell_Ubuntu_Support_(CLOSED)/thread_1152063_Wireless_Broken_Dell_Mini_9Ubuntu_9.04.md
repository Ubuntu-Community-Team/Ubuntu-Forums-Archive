---
title: "Wireless Broken Dell Mini 9/Ubuntu 9.04"
date: 2009-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yeayea911 on 2009-05-07
Hi,

I just upgraded to the .12 linux kernal that was advertised in software update this morning. The install went fine, however, my wireless gorked now. It was using a restricted driver. I cannot even see my built in wireless card that came with my mini 9.

Please not I am using a broadcom wireless card that came built in with the mini 9. In the "Hardware drivers" section in preferences, it does nto show ANYTHING under that panel.

Any help please?

Thanks

---

### Post by gavinfoxx on 2009-05-07
I am having this exact problem as well.  Does anyone have any advice for making sure I have all the relevant drivers and then installing them? Some exact terminal commands would help very much. Thanks!

---

### Post by double0negative on 2009-05-07
I have the same situation as well.](*,)

---

### Post by kulight on 2009-05-07
i think it may be related to this bug:
[https://bugs.launchpad.net/bugs/372876](https://bugs.launchpad.net/bugs/372876)

---

### Post by snowpine on 2009-05-07
Easiest solution: Boot into the old kernel from your Grub boot menu, until the problem is fixed upstream.

---

### Post by s9032g@comcast.net on 2009-05-07
Do a clean install of 8.10 or 9.04 and move on. Unless you enjoy messing around with the details.

---

### Post by snowpine on 2009-05-07
> **s9032g@comcast.net said:**
> Do a clean install of 8.10 or 9.04 and move on. Unless you enjoy messing around with the details.

That's just silly; you'll never learn anything if you completely reinstall every time a minor problem comes up. :)

---

### Post by anjilslaire on 2009-05-07
I feel for everyone, but appreciate the information. I'm going to hold off any updates to my Mini related to the kernel until this clears up.

Keep us posted, please.

---

### Post by Brandon Williams on 2009-05-08
I'm sorry you guys are having trouble with the proposed kernel.

That said, I generally recommend against enabling the proposed repositories, where this particular kernel resides at the moment. The jaunty-proposed repository is essential a "testing" repository, and although most of the packages that make it into the proposed repo are good, these kinds of problems occur periodically and are to be expected.

For people who are ready to take the risk in order to help out with testing, thank you! Please just make sure that you examine each individual package carefully before performing updates so that you are aware of which packages are coming from proposed, and whether the proposed updates look reasonable and complete.

And for folks who haven't experienced this problem ... you probably don't have jaunty-proposed enabled (it's not enabled by default) and you are unlikely to encountered these kinds of problems. I won't say never, but it's quite rare.

---

### Post by anjilslaire on 2009-05-08
Indeed.

And it appears the bug on Launchpad has been fixed, with an update released, or the repo's updated, according to the email thread on the bug ID.

---

### Post by gavinfoxx on 2009-05-12
So I just have to plug into wired and run update manager?  Are there any terminal commands to make sure I have the wireless drivers installed and running and such?

---

