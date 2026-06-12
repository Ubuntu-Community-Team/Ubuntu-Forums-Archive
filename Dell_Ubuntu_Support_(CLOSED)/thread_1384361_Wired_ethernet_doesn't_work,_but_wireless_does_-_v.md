---
title: "Wired ethernet doesn't work, but wireless does - very weird"
date: 2010-01-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by autonomouse on 2010-01-18
Okay folks, this is a bit random so any help offered will be greatly appreciated. Long story short: My wired ethernet doesn't work, but wireless does - very weird.

Long story long: I've invested in a Dell mini 10v and have put Ubuntu Netbook Remix (9.10) on it. Initially, everything on it worked great with the exception of the wireless. So I downloaded the restricted wireless drivers and all was good...

...Until I got to work and found that it didn't connect to the wireless network there. It detects it, but just won't connect (I quadruple checked the connection settings, so I haven't got my poassword wrong or anything). Very odd, methinks, so I fall back to wired and plug in the ethernet cable from the back of my work PC (dual booting windows xp and kubuntu 9.10), and now I find that the autoeth0 doesn't connect either.

This is the cable happily supplying internet to my other linux box, so there's got to be a bug in UNR somewhere surely? The thing is it was working before and I'm reluctant to uninstall the proprietry wireless drivers as I might then lose wireless as well (and I don't want to reinstall everything).

I checked googly and found ( [http://www.ubuntumini.com/2009/03/ubuntu-810-kernel-update-has-broken.html](http://www.ubuntumini.com/2009/03/ubuntu-810-kernel-update-has-broken.html) )that there was some kernel problem with 2.6.27.11 and the advice was to wait for 2.6.27.13. Thing is, that I'm on 2.6.31.17 now!

So, erm... now what? Any ideas folks?

Thanks,
Darren/Autonomouse

---

### Post by bobcollard on 2010-01-19
> **autonomouse said:**
> Okay folks, this is a bit random so any help offered will be greatly appreciated. Long story short: My wired ethernet doesn't work, but wireless does - very weird.

Long story long: I've invested in a Dell mini 10v and have put Ubuntu Netbook Remix (9.10) on it. Initially, everything on it worked great with the exception of the wireless. So I downloaded the restricted wireless drivers and all was good...

...Until I got to work and found that it didn't connect to the wireless network there. It detects it, but just won't connect (I quadruple checked the connection settings, so I haven't got my poassword wrong or anything). Very odd, methinks, so I fall back to wired and plug in the ethernet cable from the back of my work PC (dual booting windows xp and kubuntu 9.10), and now I find that the autoeth0 doesn't connect either.

This is the cable happily supplying internet to my other linux box, so there's got to be a bug in UNR somewhere surely? The thing is it was working before and I'm reluctant to uninstall the proprietry wireless drivers as I might then lose wireless as well (and I don't want to reinstall everything).

I checked googly and found ( [http://www.ubuntumini.com/2009/03/ubuntu-810-kernel-update-has-broken.html](http://www.ubuntumini.com/2009/03/ubuntu-810-kernel-update-has-broken.html) )that there was some kernel problem with 2.6.27.11 and the advice was to wait for 2.6.27.13. Thing is, that I'm on 2.6.31.17 now!

So, erm... now what? Any ideas folks?

Thanks,
Darren/Autonomouse
I don't have a netbook, but, I do have a laptop.  If you check your specs you may find you have a different card for Ethernet than wireless, at least, I do.  That means two different drivers.  I have Marvel card for Ethernet and a Broadcom card for Wireless.  If the wired card worked before you changed the wireless driver it should still work.  Have you tried it at home on your local area network with the same cable?  Cables do go bad.  Connectors fail to contact etc.

---

