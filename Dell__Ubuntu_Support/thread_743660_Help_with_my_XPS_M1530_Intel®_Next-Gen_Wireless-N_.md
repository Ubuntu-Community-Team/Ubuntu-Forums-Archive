---
title: "Help with my XPS M1530 Intel® Next-Gen Wireless-N Mini-PCI Card"
date: 2008-04-02
forum: Dell  Ubuntu Support
---

### Post by kramdish on 2008-04-02
Hi I have a Dell XPS M1530 with a Intel® Next-Gen Wireless-N Mini-PCI Card. I don't know much about it and I've been reading a bit in this section of the forums.

I would like to know if you could tell me what chipset does the afforsaid wireless card have?

Does it work out of the box with Ubuntu 7.04 (Feisty Fawn)?
Is it posible to put in monitor mode and use injection to offensive securrity WEP and WPA networks?

I hope you can help.Thanks.

---

### Post by jespdj on 2008-04-04
Chipset: Intel 4965 AGN.

I don't know if it will work out of the box with Ubuntu 7.04.
On my XPS M1330 it works out of the box with Ubuntu 7.10 and 8.04 beta.

Yes, you can use stuff like WEP, WPA and WPA2.

---

### Post by drsaamah on 2008-04-04
I can second that it definitely works out of the box with Gutsy.  Is there a reason you specifically want feisty?

---

### Post by kramdish on 2008-04-06
> **drsaamah said:**
> I can second that it definitely works out of the box with Gutsy.  Is there a reason you specifically want feisty?

Well, the first time I tried Gusty, my notebook overheated extremely!! I read in google that gusty overheats notebook. 
Is it still the same?

Thanks for the info of the chipset.

To do offensive security do I need to patch something ??

---

### Post by sdennie on 2008-04-06
Gutsy shouldn't cause any overheating problems for an m1330.  I think that the open source nvidia driver doesn't know how to control the fan of the nvidia 8400M GS card but, if you install the latest closed source drivers from nvidia, the machine should stay quite cool.  If you have the nvidia 8400M GS card, I would look into envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)) to grab the latest version of the driver (the one in Ubuntu 7.10 is a bit old).

---

