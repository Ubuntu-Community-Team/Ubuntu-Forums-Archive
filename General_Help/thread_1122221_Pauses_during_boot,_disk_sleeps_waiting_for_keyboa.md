---
title: "Pauses during boot, disk sleeps waiting for keyboard activity"
date: 2009-04-10
forum: General Help
---

### Post by jgpaiva on 2009-04-10
Hi guys. I'm having a problem with my laptop and ubuntu.

Even though ubuntu runs with now problems at all after it has booted, during boot I observe a strange behaviour.
Apparently, all disk activity ceases if I don't keep pressing some key, it looks like the disk goes to sleep.
I have attached to this post an example (taken with bootchart) of what happens if I don't press any key during boot. (notice that I did press twice, one at 165s and another at 270s, or it wouldn't boot at all).
If i do keep it from sleeping, however, it boots in a normal time.

For further help: This also happened during ubuntu install (i had to keep pressing keyboard keys for it to not stop installing), but it does not happen with WinVista install or boot (I dual-boot this machine).
It's a Compal laptop, with a T9300 core 2 duo, a seagate momentus 5400 PSD hybrid drive and 4Gb of mem.

I hope someone can help me with this as I have no idea what's causing it and it's very anoying to have to be around the computer everytime it boots :S

Thanks!

[edit] more details about the hdd here: [http://www.seagate.com/www/en-us/products/laptops/momentus/momentus_5400_psd_hybrid/](http://www.seagate.com/www/en-us/products/laptops/momentus/momentus_5400_psd_hybrid/) [/edit]

---

### Post by lavinog on 2009-04-10
It probibly has something to do with the hybrid drive. It might not be a supported technology for intrepid...You may want to see if jaunty has this problem.

---

### Post by lavinog on 2009-04-10
Also is there a bios update for you laptop?

---

### Post by lavinog on 2009-04-10
> **jgpaiva said:**
> 
[edit] more details about the hdd here: [http://www.seagatepromotion.com/au/model/714/st91608220as](http://www.seagatepromotion.com/au/model/714/st91608220as) [/edit]

That doesn't look like a hybrid drive

---

### Post by Yashiro on 2009-04-10
It's bios issue not your HD.

---

### Post by jgpaiva on 2009-04-11
lavinog: I updated the link, the other one wasn't from seagate.

Why do you think it's a bios issue? I've never seen this happen except with ubuntu (even suse installed without hickups).

I've just checked, looks like compal has no updates for my bios :(

---

### Post by Yashiro on 2009-04-11
Because there have been reports like yours on here, and on launchpad, many times.

Try looking into changing settings on your bios.

It wasn't an ubuntu only issue and was related to ram or iommu or something. Suse probably used an older kernel which didn't have this bug/issue.

---

### Post by lavinog on 2009-04-11
I noticed that the site only mentions Windows Vista. I see nothing about XP compatibility. Do you know if it works in XP?
Which version of Ubuntu are you using?
Have you tried Jaunty?

---

### Post by ftabor on 2009-04-12
I've had this same problem that started when I upgraded to Intrepid on my laptop, HP pavillion.  What worked for me was to edit Grub and add acpi=noirq to the end of the kernel line.

```
sudo cp /boot/grub/menu.lst menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```

If this doesn't help, then you can restore your backup.

---

### Post by jgpaiva on 2009-04-12
Well, after disabling AHCI in the BIOS, it all went away. The system is now booting way faster.
I'm not absolutely sure this was the best option, though.. Disabling a feature of the pc to get ubuntu to work better really isn't the way I'd like to solve this.

I think I'll try your solution, ftabor. Maybe that'll help.

lavinog: I've been using Intrepid. Hybrid drives aren't supported by either ubuntu or XP, in both they work as regular drives. Vista can do a better job by using the drive's specific characteristics. From my experience, I haven't noticed much advantage, though. (the fact that windows keeps accessing the disk even when the computer isn't on use annoys me a lot)

---

