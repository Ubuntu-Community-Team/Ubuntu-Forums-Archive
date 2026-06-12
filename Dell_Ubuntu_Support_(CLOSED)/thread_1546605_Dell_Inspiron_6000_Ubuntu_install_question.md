---
title: "Dell Inspiron 6000 Ubuntu install question"
date: 2010-08-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jcolyn on 2010-08-05
Anybody install Ubuntu on this model?

I'll be picking up one tomorrow which currently has XP Pro installed and was wondering if there are any issues I should be aware of before install.

This one will be replacing my Dell Inspiron 600m which has Ubuntu installed and running without any issues. The 6000 has a wider panel and will make working with my images easier..

---

### Post by Dennis N on 2010-08-06
I have a Dell 6000 laptop which is running Ubuntu Intrepid (8.10) (dual boot with XP) so this may be of limited value. Everything works fine with Intrepid, which is the only version of Ubuntu I have installed on it. As I recall, it installed and worked from the start without needing any fixes. 

This laptop has a Pentium M 730 processor, Intel Integrated Media Accelerator 9000. Intel Pro Wireless 2915. If you have different components of course the results may vary.

Sorry I cannot comment on what will happen with 10.04.

---

### Post by anthony2010 on 2010-08-07
My young son has a Dell Inspiron D600. Now, its an older model so this may not apply but here goes..

When we installed the second beta of ubuntu 10.10 we found that the wireless wasn't working.

In fact other distros after ubuntu 8.04 (including those built on ubuntu such as mint) also failed to fire up the wireless. The newer kernel either doesnt include the drivers for broadcom (installed in Dell D600s) or the drivers for broadcom in their entirety are not there. However, I tried to install them from Synaptic and had no joy. It failed to retreive certain packages.

So heres how I solved it  - and I note there may be simpler ways but this worked:

Download a copy of Ubuntu 8.04.

Install the Ubuntu you want (say 10.10 for example.)

Run the internet on an ethernet cable and update Synaptic Package manager.

From Synaptic install 'wicd' (Its much simpler to get on the net wirelessly with this)

Insert old version of Ubuntu.

Navigate the disk to: pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb

Right click on that and install.

Youre now done with the broadcom wireless issue thats simply down to a newer kernel.

Thats it!

Its the only issue I encountered.

Good luck!

Anthony.

---

### Post by jcolyn on 2010-08-07
A clean install of Ubuntu 10.04 on the Dell Inspiron 6000 I just picked up went without a hitch. My older 600m has been working fine also.

---

### Post by mörgæs on 2010-08-11
Sounds good. Do you guys feel like updating
[http://ubuntuhcl.org/browse/product+dell-inspiron-6000?id=119](http://ubuntuhcl.org/browse/product+dell-inspiron-6000?id=119)
?

Dennis, are you aware that 8.10 is unsupported?

---

