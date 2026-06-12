---
title: "Dual Boot &amp; NTLDR is Missing?"
date: 2009-01-17
forum: General Help
---

### Post by tomsubt on 2009-01-17
Hello:  I recently had a problem when booting my xp home edition (NTLDR is missing) and had to do a recovery.
My question is, if I had a Dual Boot set up e.g. dual boot with xp home and Ubuntu, would I have been able to boot into (ubuntu) the other partition? Thanks

---

### Post by caljohnsmith on 2009-01-17
> **tomsubt said:**
> Hello:  I recently had a problem when booting my xp home edition (NTLDR is missing) and had to do a recovery.
My question is, if I had a Dual Boot set up e.g. dual boot with xp home and Ubuntu, would I have been able to boot into (ubuntu) the other partition? Thanks
Yes, you should be able to boot into Ubuntu on a dual boot system with Windows even if something happens to the Windows partition. That assumes that you use Ubuntu's default boot loader Grub and not Windows boot loader to boot Ubuntu.

---

### Post by tomsubt on 2009-01-17
I did not install the dual boot yet, but wont there be an option as to which I want to boot to (either windows or Ubuntu)when I first start up the pc?
Or is this option gone if I get the NTLDR is missing? Thanks

---

### Post by caljohnsmith on 2009-01-17
> **tomsubt said:**
> I did not install the dual boot yet, but wont there be an option as to which I want to boot to (either windows or Ubuntu)when I first start up the pc?
Or is this option gone if I get the NTLDR is missing? Thanks
If you are still getting a NTLDR missing error, then Ubuntu may not detect your Windows partition, and thus Windows may not be added to your Grub menu as a boot option. But if Windows is booting OK again, then Ubuntu will most likely be able to detect it and add it to your Grub menu so you can boot it. Once it is on your Grub menu, it will always be there unless you change your Grub's menu.lst file, so even if you get a "NTLDR missing" error again, Windows will still be in your Grub menu.

---

### Post by c45tr0l on 2009-01-18
> **tomsubt said:**
> Hello:  I recently had a problem when booting my xp home edition (NTLDR is missing) and had to do a recovery.
My question is, if I had a Dual Boot set up e.g. dual boot with xp home and Ubuntu, would I have been able to boot into (ubuntu) the other partition? Thanks

If the only problem is your XP Home Edition NTLDR file is missing, it's easy to resolved. Just find a file from internet called fixntldr.exe, boot from bootable CD/diskette/usb then run it from DOS. I think it would be the same thing for your dual boot OS. Just give it a try. :)

---

### Post by tomsubt on 2009-01-18
Ok, When I install the dual boot I will put it in the Grub menu, Thank you!

I tried that fixntldr.exe but it did not work. But I dont have the problem now anyway, I did a recovery, i just want to be prepared for a future NTLDR is missing. Thanks

---

### Post by x33a on 2009-01-18
i use a dual boot and have had this error message a couple of times. for me a simple reboot has fixed the error!! 

anyway, this error comes after you get past the bootloader, at least when you dualboot. so, you can still boot ubuntu if windows shows problems.

---

### Post by tomsubt on 2009-01-19
Ok, Thanks to all for the replies.

---

