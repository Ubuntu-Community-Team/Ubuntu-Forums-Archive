---
title: "Remove Xubuntu"
date: 2010-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maxkam on 2010-05-08
Has anyone loaded Xubuntu or Ubuntu using the "dual boot" option on the Lucid Lynx installer disc?  I installed Xubuntu 10.04 on my Dell Studio 17 running Win7 Home Premium and would like to replace it with the full version of Ubuntu 10.04 (Lynx).  It did not make its own partition and gives no options to remove.  Need some help.  
 
BTW Both verions are phenomenol.  Kudos to Ubuntu Development Team.  I hope you give Microsoft a run for their money.
 
Pentium Dual Core T4200 @ 2.00 GHz 2.00 GHz
3.00 GB RAM
32-Bit Operating System

---

### Post by aysiu on 2010-05-08
It sounds to me as if you used Wubi to install Xubuntu. You're right. It doesn't repartition your hard drive. It creates a large file on your Windows partition as a virtual partition and then modifies the Windows boot loader to include an entry to boot off the virtual partition.

Apart from removing Xubuntu (Start Menu > Control Panel > Programs > Uninstall Ubuntu) and then setting up Ubuntu the same way you did Xubuntu, you can also just install Ubuntu and then remove Xubuntu (this requires a broadband network connection):

Step 1: Reboot into Xubuntu

Step 2: Go to Applications > Ubuntu Software Center

Step 3: Install <i>ubuntu-desktop</i>

Step 4: Log out

Step 5: At the login screen, select Gnome from the bottom panel

Step 6: Log back in again

Step 7: Follow [these instructions](http://www.psychocats.net/ubuntu/puregnome) to remove Xfce.

---

### Post by maxkam on 2010-05-08
Thanks,
 
I will try this tonight and keep you posted.

---

### Post by maxkam on 2010-05-09
I feel stupid how easy it was.  Thank you.

---

### Post by steve-o1983 on 2010-08-15
> **maxkam said:**
> I feel stupid how easy it was.  Thank you.

I agree, I have been trying to figure out what to do for a while now.  I had already installed ubuntu-desktop but couldn't figure out how to get it to work.  Thanks aysiu!

---

### Post by thecolorifix on 2011-09-15
I was testing different lightweight interfaces for my Acer Aspire One and i think i finally settled on Lubuntu, so i wanted to remove some clutter. 

Just wanted to say thanks, this was one of the top Google results and it worked perfectly.

---

