---
title: "Removing Ubuntu"
date: 2009-01-28
forum: General Help
---

### Post by Mister J on 2009-01-28
Hello. I'm very new to Ubuntu, and I did something stupid. I installed Ubuntu to dual-boot with vista without partitioning the drive, and I was told I could easily remove it if I choose from the add/remove programs utility. I installed it, but forgot my username. Since I was locked out, I figured I'd just uninstall it, then reinstall it. I went to the add/remove programs in Vista and removed Ubuntu, but I don't think it did what I want because it took only 8 seconds. I reinstalled Ubuntu from the disk, and now when I boot up I have 2 Ubuntu options and neither of them work. They fail immediately after I select them. 

My question is, can someone please explain to me how to completely remove Ubuntu (64bit edition) from within Vista? I want it wiped completely, or if possible, fixed so I can use Ubuntu again.  

Thank you so much for your time.

---

### Post by mb_webguy on 2009-01-28
How did you install Ubuntu?  I ask because none of what you said really seems to make sense to me, unless perhaps you installed Ubuntu using Wubi from inside Windows (with which I have no experience).

---

### Post by avtolle on 2009-01-28
It appears to me that you installed with Wubi. I've removed Ubuntu from Vista using the add/remove feature, which indeed took <10 seconds, successfully. My sugesstion is to go to the Wubi site and take a look at the Wubi guide which is linked there; there is a separate application that may be used to remove Ubuntu installed with Wubi from Vista.

Edit: Here's a link: [http://wubi-installer.org/faq.php#use](http://wubi-installer.org/faq.php#use)

---

### Post by Mister J on 2009-01-29
Yes, I did use Wubi. I uninstalled it, but when i boot up my computer it still prompts me whether I want to use Vista, Ubuntu or Ubuntu. I have 1 9gb partition in my hard drive. Is that normal on a computer that hasn't been changed at all from a factory setting? Should I try to get rid of that partition to uninstall Ubuntu? And how can I fix my situation to get Ubuntu back?

---

### Post by synapse13 on 2009-01-29
Not sure if you still want Ubuntu on there, but I had a similar problem after uninstalling Ubuntu through Wubi.  I'm running Vista 64 bit, and after uninstall I had not regained my lost hard drive space and Ubuntu still appeared on the boot loader screen.

Manually delete the Ubuntu folder on your C drive, then go download EasyBCD (free download) to modify bcdedit.exe for you (this is the boot loader program in Vista).  EasyBCD does it way easier, through graphical means.  Remove the Ubuntu listing and you'll be back to where you began.  EasyBCD link:
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by balaknair on 2009-01-29
Hello Mister J
"I have 1 9gb partition in my hard drive. Is that normal on a computer that hasn't been changed at all from a factory setting?"
That's probably the recovery partition put there by your manufacturer. Don't touch it till you know for sure what it is, it could void your warranty. Wubi does not make any changes to partitions, so it is unlikely to have anything to do with it.

 To remove Wubi:
The best option is to uninstall Wubi using the Add/remove programs applet in Vista. If you have errors after that try using the uninstaller within the Wbi Ubuntu folder(C:\ubuntu\Uninstall-Ubuntu.exe).

If this does not work either, you can use the Vista DVD to repair your Vista bootloader to remove the Ubuntu entry from the boot menu. Boot into the Vista DVD> You'll be asked to select language etc. and then you get an option to 'Repair your Computer'> Restart.
If you don't have a Vista DVD try EasyBCD( [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) ). This is probably a better/safer option in mu opinion.
Install EasyBCD(download link given above)> run the program> add/remove entries> Windows> remove one or both entries for Ubuntu.

You can now reinstall Ubuntu via Wubi. To avoid re-downloading the Ubuntu CD iso again when installing Wubi, just copy the iso file into the same folder as wubi.exe

---

### Post by Mister J on 2009-02-01
Oh my god. That program is like the Win button for Vista. I got Ubuntu all fixed and working again. Thank you so much.

---

