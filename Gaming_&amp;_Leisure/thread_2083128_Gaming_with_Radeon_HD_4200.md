---
title: "Gaming with Radeon HD 4200"
date: 2012-11-11
forum: Gaming &amp; Leisure
---

### Post by samsom63 on 2012-11-11
Hi all,

I'd very much like to play Bastion. I run Ubuntu 12.10 on a laptop (Compaq cq61) and, although my system meets the minimal requirements, I fear the graphic card (radeon HD 4200) will not be up to the task. I used to play Dragon Age origins or AC1 on this machine, back when my OS was win7 and things were fine. 

But what about a more contemporary game? And what about this graphic card under Linux? 

Anyone with a good or bad gaming experience with this hardware under Linux who'd like to share?

PS: I use the ATI open source drivers 
PPS: I don't have a windows partition at all anymore on this machine

Thanks.

---

### Post by Dlambert on 2012-11-11
I believe you will need the proprietary AMD drivers in order to have any chance of that.

---

### Post by samsom63 on 2012-11-11
> **Dlambert said:**
> I believe you will need the proprietary AMD drivers in order to have any chance of that.

Ok, thanks to confirm what I feared...I tried to install the legacy proprietary drivers on ubuntu 12.10 but it did not work. I guess I'll have to either downgrade to 12.04 or stick to console gaming for the time being.

---

### Post by Dlambert on 2012-11-11
Did you install your headers?

---

### Post by samsom63 on 2012-11-11
> **Dlambert said:**
> Did you install your headers?

No, I did not come across these yet...Could that explain why the installation of the legacy drivers did not work at all?

---

### Post by Dlambert on 2012-11-11
> **samsom63 said:**
> No, I did not come across these yet...Could that explain why the installation of the legacy drivers did not work at all?


> Latest proprietary AMD Catalyst driver version 12.9 cannot be used with  Ubuntu 12.10 If you have a AMD Radeon HD 2xxx-4xxx series card. Drivers  for these cards are now available in a separate branch called legacy  series. Unfortunately these legacy drivers (version 12.6) have not been  updated to work with Ubuntu 12.10. Ubuntu 12.10 comes with xorg 1.13  while these drivers have support for older xorg 1.12.

Downgrading seems to be the only option at this moment.

---

### Post by Dlambert on 2012-11-11
You can try to downgrade the x-server via: [http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/](http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/)

---

### Post by holastickboy on 2012-11-12
Recommend staying with 12.04, its much nicer for those who dont want to perform magic just to get drivers working.  The 12.04 definitely supports the Catalyst legacy drivers that you want, without any modification.  A great deal of us have issues with 12.10, even after following the guides, as well as with AMD/Nvidia hardware.

---

### Post by samsom63 on 2012-11-12
> **holastickboy said:**
> Recommend staying with 12.04, its much nicer for those who dont want to perform magic just to get drivers working.  The 12.04 definitely supports the Catalyst legacy drivers that you want, without any modification.  A great deal of us have issues with 12.10, even after following the guides, as well as with AMD/Nvidia hardware.

That makes a lot of sense. I picked up in different threads that many experienced people got problems to get legacy drivers working on 12.10 so I will definitively consider downgrading to 12.04.

---

### Post by samsom63 on 2012-11-12
> **Dlambert said:**
> You can try to downgrade the x-server via: [http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/](http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/)

Installing the legacy driver package also downgrades the x-server (I checked that) but still it did not work...

---

