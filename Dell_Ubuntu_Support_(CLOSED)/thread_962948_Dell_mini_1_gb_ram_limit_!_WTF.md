---
title: "Dell mini 1 gb ram limit ! WTF?"
date: 2008-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ali_Taimur on 2008-10-29
I just installed 2 gig of ram in my dell mini but ubuntu is showing it as 1 GB. After some research i found out that DELL has put an artificial limit of 1 gig on ubuntu dell mini through some kernel flag however no such limit exist on XP Systems. This is extremely disappointing and i feel cheated for buying dell mini now. Does anyone know how i can remove that artifival 1 gig ram limit? 

> he Ubuntu kernel that dell ships with Ubuntu versions of the notebook however has been modified by dell to to have a maximum memory limit of 1GB [http://www.agaricdesign.com/note/dell-mini-9-an-upgrade-odyssey](http://www.agaricdesign.com/note/dell-mini-9-an-upgrade-odyssey)

---

### Post by notwen on 2008-10-29
A fix looks to be in the works.  Check the bug [here]("https://bugs.launchpad.net/ubuntu/+bug/286258") on launchpad for more details.  =]

---

### Post by 2damncommon on 2008-10-29
> **Ali_Taimur said:**
> ...After some research i found out that DELL has put an artificial limit of 1 gig on ubuntu dell mini through some kernel flag...
I'd love to see the documentation about Dell and the artificial limit.

What I found researching it was that there is a "large memory" support option when building the kernel. The "large memory" options are "OFF", "4GB", and "64GB". I understood that the "OFF" option provided about 128MB short on 1024MB RAM. I saw discussion about it being wise or not to enable the "4GB" option if you only had 1GB. To be able to use 2GB of RAM the "4GB" option needs to be chosen.

The provided kernel is arguably the correct kernel to use on 512MB and 1GB computers. 

I am glad to see Dell will provide a kernel with "large memory" support.

Simply recompiling the kernel with that option should be possible but I had problems doing that on the Mini 9. The Mini 9 complained about architecture and subarchitecture types and I could not find the needed fix.

---

### Post by jazz1 on 2008-10-29
O.K. assuming Dell sees the error of their ways will there be an easy fix for Ubuntu newbies?

---

### Post by 2damncommon on 2008-10-29
> **jazz1 said:**
> O.K. assuming Dell sees the error of their ways will there be an easy fix for Ubuntu newbies?
See above:
> **notwen said:**
> A fix looks to be in the works.  Check the bug [here]("https://bugs.launchpad.net/ubuntu/+bug/286258") on launchpad for more details.  =]
Click the "here" link.

---

### Post by ets2006 on 2008-10-30
that shows how smart dell are.. they've even got their own support category?
my dell dimension 8100 (very old) does not like grub :-(

- do yourself a favour, buy yourself an IBM!

---

### Post by anjilslaire on 2008-10-30
```

         \|||/       
         (o o)       
,----ooO--(_)-------.
| Please            |
|   don't feed the  |
|     TROLL's !     |
'--------------Ooo--'
        |__|__|      
         || ||       
        ooO Ooo      

```

---

