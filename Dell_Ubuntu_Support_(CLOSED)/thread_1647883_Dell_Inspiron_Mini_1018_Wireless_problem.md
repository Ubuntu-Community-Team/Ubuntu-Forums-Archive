---
title: "Dell Inspiron Mini 1018 Wireless problem"
date: 2010-12-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nactownag on 2010-12-18
I'm sure this is about the 50th thread on a similar subject and I apologize in advance. 

Can someone please give an ubuntu newbie some direction and instructions on how to enable wifi on this computer?

Everything about this is working just fine.  That's the only thing that's missing. 

I'm running Ubuntu Netbook Remix 10.10

I will be eternally grateful. 

nactownag at gmail dot com or reply here.  Thanks!

---

### Post by ugm6hr on 2010-12-18
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by JerreCope on 2011-01-25
The current Mini 1018 now uses Realtek drivers, so the broadcom fix will NOT work.

Found this fix on the Dell Community Forum:

[http://en.community.dell.com/support-forums/software-os/f/3525/t/19352306.aspx]("http://en.community.dell.com/support-forums/software-os/f/3525/t/19352306.aspx")

In summary:

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

---

### Post by Mbroadstone on 2011-02-06
I used the aforementioned commands to get the realtek driver and it worked well.  However, as soon as I update Ubuntu the Additional Drivers show that the driver is activated but not currently in use.  Help! its drivering me nuts!

---

### Post by yax51 on 2012-01-24
I don't know if this thread is still open or not, for a solution to this problem I just went to synaptics and searched for rtl8 and reinstalled the drivers and rebooted and it worked just great! Hope that helps someone!!

---

### Post by buzzpavan on 2012-01-24
Ohh!!! I had toggled my wifi switch in gnome 3 by mistake the day before and couldnt re activate it despite several efforts. trying the method listed didnt help at all. 

i went back to ubuntu 10.04 and the solution here worked just fine.

will keep this synaptic solution in mind.

mental note - never ever toggle the wireless switch to off in gnome! :(

---

