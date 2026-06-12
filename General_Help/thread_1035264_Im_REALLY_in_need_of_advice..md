---
title: "Im REALLY in need of advice."
date: 2009-01-09
forum: General Help
---

### Post by Soludus on 2009-01-09
Hello,

First off, im pretty new to Ubuntu. But I was duped on a forum to open 5 terminals and run a dd command in all of them. I was tricked into destroying my laptop. Now when I try to boot up, it says OS not installed anjd is not recognizing discs. I think maybe he tricked me into frying my harddisc/ram. I was told the command he gave me set my ram and harddisc speed to a random number? Im confused, and need advice or im going to have to send it in to HP... and you know how that goes, no laptop for like 2 weeks.

---

### Post by jsroth on 2009-01-09
Do you know which "dd commands" you ran?

---

### Post by Soludus on 2009-01-09
something to do with the harddisc, {hd parm -i} I know that was one of them, having trouble remembering exactly what the others were, my laptop started heating up right after i did it, he said to open 5 run it for around 2 minutes, and the restart. Once i did that, it killed it.

---

### Post by timcredible on 2009-01-09
why would you have to send it to hp?  can't you re-install ubuntu from cd?

---

### Post by DeMus on 2009-01-09
> **Soludus said:**
> Hello,

First off, im pretty new to Ubuntu. But I was duped on a forum to open 5 terminals and run a dd command in all of them. I was tricked into destroying my laptop. Now when I try to boot up, it says OS not installed anjd is not recognizing discs. I think maybe he tricked me into frying my harddisc/ram. I was told the command he gave me set my ram and harddisc speed to a random number? Im confused, and need advice or im going to have to send it in to HP... and you know how that goes, no laptop for like 2 weeks.

That shows again to never trust somebody who tells you to do this or that. Whenever you are told to try something, look-up the command first to see what it does before doing it. It can save you for a lot of trouble.

DeMus

---

### Post by Soludus on 2009-01-09
Yes, I was very tired. Otherwise I would have looked it up, he said it would unlock my wireless card for higher download speeds, he was very convincing.

---

### Post by Soludus on 2009-01-09
can't reinstall Ubuntu, says boot device not recognized.

---

### Post by BrandonBan6 on 2009-01-09
Do you still have your Ubuntu CD? Can you boot to it? 

If you didn't have any real data on there, just re-install it, maybe the easiest starting point. 

If re-install is not an option, from the live cd open terminal type fdisk -l

I know you are probably nervous listening to someone tell you to type in the terminal again, but that command should return a list of your hard drives. Could be a good starting point to see what is mounted already.

---

### Post by jsroth on 2009-01-09
> **Soludus said:**
> can't reinstall Ubuntu, says boot device not recognized.

Are you sure your BIOS is set to boot from the CD before trying to boot from the HDD? And are you sure the CD is working allright? 

And fdisk really is a good command which will tell us all which devices are recognized by your computer. (and -l is just making it list the devices)

---

### Post by oldos2er on 2009-01-09
> **Soludus said:**
> can't reinstall Ubuntu, says boot device not recognized.

 Did you set your BIOS to boot from CD? Assuming you're wanting to boot from the Ubuntu LiveCD.

---

### Post by BrandonBan6 on 2009-01-09
> **Soludus said:**
> can't reinstall Ubuntu, says boot device not recognized.

Sorry I missed this post!

---

### Post by Yellow Pasque on 2009-01-09
You've probably destroyed the partition table (and other data) on your hard disk, but you should still be able to boot with a LiveCD and use gparted to delete all of the partitions.

I can't think of any dd command that would physically damage your hardware or permanently alter your BIOS, but just to make sure, I would go into the BIOS/system setup and reload the defaults. Also, as mentioned, make sure the CD is set to boot before the hard disk.

---

### Post by Soludus on 2009-01-09
works, thanks guys.

---

