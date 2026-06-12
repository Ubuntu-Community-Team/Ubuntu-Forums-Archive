---
title: "Wireless on Dell Inspiron 1545"
date: 2009-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rahul.v.kulkarni on 2009-08-15
i have anew dell inspiron 1545. i have installed ubuntu 8.04 lts on iot. it hasnt recognised my wireless card nor installed any compatible driver. can someone help.

---

### Post by mikewhatever on 2009-08-15
Do you have a Dell Wireless 1397 802.11g Mini-Card? I don't know if there is a driver for that in 8.04, there is a good chance it will work out of the box with 9.04. Any chance you want to use a newer version?

---

### Post by thychamp on 2009-08-15
I bought the Inspiron 1545n which was pre-installed with ubuntu 8.10.  The wireless card worked and when I upgraded to 9.04 it continued to work just fine.  I don't know if the Inspiron 1545 that Dell sells with Windows comes with a different wireless card, but I would try and upgrade to the latest version of Ubuntu 9.04 and see if that solves the problem.  That will probably be your easiest solution.

I have found that with every release of Ubuntu it comes with more support for drivers.

---

### Post by mluntz on 2009-08-17
> **thychamp said:**
> I bought the Inspiron 1545n which was pre-installed with ubuntu 8.10.  The wireless card worked and when I upgraded to 9.04 it continued to work just fine.  I don't know if the Inspiron 1545 that Dell sells with Windows comes with a different wireless card, but I would try and upgrade to the latest version of Ubuntu 9.04 and see if that solves the problem.  That will probably be your easiest solution.

I have found that with every release of Ubuntu it comes with more support for drivers.

Which version of the wireless card do you have on your 1545n? I am considering purchasing one of these machines with Windows on it and adding Ubuntu to the mix. But when I went to the store and tried a live USB boot of Fedora 10 (the only linux live OS I had) on the display machine the wireless did not work. I have seen conflicting data about whether or not the wireless cards on the Windows machines work in Ubuntu. Could it be that there is a different wireless card on the machines that come from Dell with Ubuntu preloaded?

The output of lspci -vnn on the display machine I looked at showed that the wireless card was a:

Broadcom Corporation BCM 4312 802.11 b/g [14e4:4315] (rev01)
   Subsystem: Dell Wireless 1397 Wireless Lan Mini Card [1028:000c]  

I would like to get the Windows machine because it is slightly cheaper than the Ubuntu machine from Dell and it gives me the option to dual boot if I choose.

Thanks,
Mike

---

### Post by thychamp on 2009-08-17
That is the same wireless card that is on my Inspiron 1545n that came preloaded with Ubuntu.  I would bet the reason it didn't work out of the box would be because you have to enable a proprietary driver for the wireless.  I attached the screen shot of what I am talking about.

---

### Post by mluntz on 2009-08-19
> **thychamp said:**
> That is the same wireless card that is on my Inspiron 1545n that came preloaded with Ubuntu.  I would bet the reason it didn't work out of the box would be because you have to enable a proprietary driver for the wireless.  I attached the screen shot of what I am talking about.

Thanks thychamp. I went ahead and purchased the machine and, as you predicted, everything seemed to work out of the box. I have only tried a 32 bit live CD because that is what I had laying around, but will download the 64 bit version today and give that a go.

---

### Post by thychamp on 2009-08-19
> **mluntz said:**
> Thanks thychamp. I went ahead and purchased the machine and, as you predicted, everything seemed to work out of the box. I have only tried a 32 bit live CD because that is what I had laying around, but will download the 64 bit version today and give that a go.

Let me know if the 64 bit version works out of the box as well.  If it does, does it seem to improve performance?

---

