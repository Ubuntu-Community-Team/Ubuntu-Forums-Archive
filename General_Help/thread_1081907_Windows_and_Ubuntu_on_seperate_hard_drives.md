---
title: "Windows and Ubuntu on seperate hard drives"
date: 2009-02-27
forum: General Help
---

### Post by Admiral Yi on 2009-02-27
Hello

Im about to upgrade my computer. At the moment i've just got an 80gb partition with indows xp installed and Ubuntu running on Wubi.
When I upgrade the computer im going to install a 1TB hard drive which I want to use Ubuntu on. If I were to leave windows xp on the 80Gb one and install Ubuntu on the new 1TB one, would switching between the two be as simple as pressing DEL (or whatever) at BIOS and changing temporary boot order? Or would it be more complicated then that? 

Also, does it mater which way round I install the harddrives? If I want the Ubuntu one to be the primary, do I install it on top of the other one?

---

### Post by albandy on 2009-02-27
you can install ubuntu directly in the second disk and it will  create a boot menu in the first disk allowing you to start Linux or Windows

---

### Post by Admiral Yi on 2009-02-27
But where will Ubuntu actually be installed with this method? I want Ubuntu in the 1TB disk. This will be the main one I use and boot into every day. Windows will be there for playing games etc (I've tried WINE, but it crashes too often and has limited compatibility). The windows disk will only have 80GB, so I want to keep all of that free for games and not have any of it taken up with Ubuntu like it is at the moment.

---

### Post by albandy on 2009-02-27
when you boot with the ubuntu CD you can select where to install ubuntu. So you don't need to switch your drives, simply add the second disk to your second sata channel.
Boot with the ubuntu CD and when prompted select the second disk.

At the end of the installation, ubuntu will create a boot menu where you can select to boot windows from the first hard disk or linux from the second.

---

### Post by jwbrase on 2009-02-27
> **albandy said:**
> when you boot with the ubuntu CD you can select where to install ubuntu. So you don't need to switch your drives, simply add the second disk to your second sata channel.
Boot with the ubuntu CD and when prompted select the second disk.

At the end of the installation, ubuntu will create a boot menu where you can select to boot windows from the first hard disk or linux from the second.

He may not have a CD. He installed via Wubi. I also made my install via Wubi, and have never touched an Ubuntu CD.

@Admiral Yi: You can use LVPM to make your transfer. It will copy your install over to the new hard drive. 

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Once it's transferred, you may need to mess with Grub (the bootloader) a bit to get things how you want them. (And indeed, in my case, I had to mess with Grub a bit just to get Ubuntu to boot from the dedicated disk. It still booted from Wubi's virtual disk until I got everything working and uninstalled the Wubi install, though)

But, in general, it shouldn't be too much of a problem to get things set up how you want them. It's pretty much how I have my computer set up.

---

### Post by Admiral Yi on 2009-02-27
Ah I see. I do have an Ubuntu CD, just didn't understand the first time. 

If I was to use LVPM would it keep the same settings as in my Wubi install or would it be completely fresh?

---

### Post by wolfen69 on 2009-02-27
or you could just temporarily unplug the xp drive, then install ubuntu on the other.

when booting up, all you will have to do is hit (usually) F12 to choose which drive to boot to. no need to install grub on the xp drive.

---

### Post by Fenris_rising on 2009-02-27
In my first foray with an ubuntu install I wiped windows due to my lack of understanding with the partitioner. No great loss it turned out but I did do as Wolfen69 suggests which worked perfectly. Within 2 weeks I removed windows for good though :D .

regards

Fenris

---

### Post by ryan.nabinger on 2009-02-27
Unless you reall know how an OS install will go, get in the habit of unplugging all drives except the one you are installing on.  In this way you will not risk losing the MBR on a drive.

---

### Post by jwbrase on 2009-02-27
> **Admiral Yi said:**
> Ah I see. I do have an Ubuntu CD, just didn't understand the first time. 

If I was to use LVPM would it keep the same settings as in my Wubi install or would it be completely fresh?

Yes, LVPM will copy over the settings and everything of your Wubi install (although if you do make any more settings changes under the Wubi install after you copy it over and before you remove it, those changes will not be copied).

The methods the others are recommending, as far as I know, will not copy over your settings. They may be a bit safer and a bit less hassle, however. As far as safety, make sure that you know exactly what you're doing when you set up your partitions on the new drive, and the LVPM method should be fine. As far as hassle, it was a bit of a hassle for me, but I didn't mind that too much (I learned a few things), and as long as you don't have any more problems than I did, I should be able to help.

---

