---
title: "Slow to boot winxp after removing ubuntu"
date: 2006-08-26
forum: Desktop Environments
---

### Post by BoomerAus on 2006-08-26
I had 2 hard drives.
1. WinXP
2. Ubuntu
Grub used to come up and allow me to select which OS to boot from.
I have removed the 2nd drive with Ubuntu as i am selling my old pc and need to use that drive.
Now with only the main drive with WinXP it takes ages to boot.
I have gone into Bios and set the correct drive to boot with and done an F8 to select the correct drive but it still takes ages.
My thoughts are that Grub has left something on the 1st drive in some partition that it would have used when loading.

Can anyone point to a fix for this. I have tried Recovery console but it looks like "Danger Will Robinson".
It would be great to fix this without damaging my 1st drive.

---

### Post by neko18 on 2006-08-26
Did you replace GRUB with the Windows XP bootloader?

---

### Post by BoomerAus on 2006-08-26
No, i just removed the 2nd drive from my PC then rebooted.
Ok so i got to set the XP loader? hmmm.
Had a look in boot.ini and it all looks good there. No mention of Grub.

---

### Post by neko18 on 2006-08-26
You might want to get verification from someone else first, but I believe you boot to "Recovery Mode" using the Windows XP install disc, then type "fixmbr" in the console. I make no promise this will work though.

Edit: I should note that if it doesn't work, I don't know how to fix it.

---

### Post by orb9220 on 2006-08-26
It will that is the way to restore the xp mbr back to normal,

---

### Post by BoomerAus on 2006-08-26
Ok, i booted with my XP CD, (after enabling auto password for the recovery console), and typed fixmbr it came back saying it found an
invalid or nonstandard partition table signature. 

I read the blog from microsoft on this from here:

If you do not specify a device_name, a new master boot record will be written to the boot device, which is the drive on which your primary system is loaded.
•	

If an invalid or nonstandard partition table signature is detected, you will be prompted whether you want to continue. If you are not having problems accessing your drives, you should not continue. Writing a new master boot record to your system partition could damage your partition tables and cause your partitions to become inaccessible.  

So with the robot bleating warnings i typed y and it wrote a new mbr.

Luckily i still have my partition and can access everything, but it's still booting really slow. It gets to loading IDE drives, I have one IDE WD 250Gig and my primary SATA Seagate 250Gig.
So it takes too long to detect them then it sits there pondering for minutes then it will display the controller info, then starts booting very slowly into winXP.
Once it's booted it's fine, runs normally.
I guess i could just leave it on and never turn it off.
8-[

---

### Post by neko18 on 2006-08-26
Does it still boot slowly if you put it in hibernate from Windows?

---

### Post by BoomerAus on 2006-08-26
It's ok, i found the problem. I shut down and check all the cables and jumpers, the WDC 250gig doesn't need a master jumper if it is on it's own, a single drive. So removed that and it boots nice and fast now.

Thanks all for your assistance.

---

