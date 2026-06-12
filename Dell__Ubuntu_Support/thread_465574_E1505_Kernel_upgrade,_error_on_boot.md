---
title: "E1505: Kernel upgrade, error on boot"
date: 2007-06-05
forum: Dell  Ubuntu Support
---

### Post by Suthern on 2007-06-05
Everything is going fine, so I do a complete update which includes a kernel update to 2.6.20-16

And the next reboot, it gives me "Error 17: Cannot mount selected partition".

So, I try editing the grub boot "root (hd0,0)" line to hd0,1 and hd1,1 and hd1,0, but nothing works.

Come on, this is going to kill ubuntu DELL sales.

So here's my request. Could someone who has a WORKING e1505N restart and push 'e' at the grub line and tell me what theirs looks like? Perhaps that'll help...

Thanks!

-Suthern

---

### Post by oylenshpeegul on 2007-06-05
> **Suthern said:**
> Everything is going fine, so I do a complete update which includes a kernel update to 2.6.20-16

And the next reboot, it gives me "Error 17: Cannot mount selected partition".


Try hd0,2 :) 

Dell's write up is at

  [http://linux.dell.com/wiki/index.php/GRUB_error_17_after_kernel_update](http://linux.dell.com/wiki/index.php/GRUB_error_17_after_kernel_update)

---

### Post by Suthern on 2007-06-06
Yup, that worked. I also edited menu.lst to reflect the changes.

Thanks!
-Suthern

---

### Post by mumble02 on 2007-06-10
Ok... I'm having a similar problem, cause it said the same thing right after I updated. But I do have a couple different situations... one mines a E1505 no "n" at the end (dont know if that really matters, but the other problem is after looking at the link I found out that it already said hd0,2. So I tried hd0,4 and hd0,3... but nothing. 

Any ideas on how to fix it?

---

### Post by hasimir44 on 2007-06-10
> So here's my request. Could someone who has a WORKING e1505N restart and push 'e' at the grub line and tell me what theirs looks like? Perhaps that'll help...

Good idea. Anyone? (I just ordered one, but it won't arrive for a while..)

> So I tried hd0,4 and hd0,3... but nothing. 

you can try incrementing your hard drive number:

hd1,0 ... hd1,1 ... hd1,2   

> Come on, this is going to kill ubuntu DELL sales.

True. Imagine your aunt/uncle/mom/etc.. trying to do this fix - not gonna happen. I can see it already - "it worked good for about 20 minutes, then it broke! these laptops suck!"

I'm wondering if this happens because Synaptic is set to *update* (overwrite) the configuration files  by default (nothing in settings for this)?

I remember doing upgrades through apt-get (command line) and it would ask if you'd like to overwrite config files.. Has anyone tried this?

---

### Post by hasimir44 on 2007-06-10
just got an idea... what if you perform Dell's *system recovery* or whatever it's called - then check:

```
grub -e
```

then do the updates.. then edit grub back to what it was?

---

### Post by Suthern on 2007-06-11
The correct one is 0,2

and yes, it's a pain to do it after every kernel update.

---

### Post by Dennis N on 2007-06-12
A technician at Dell wrote that "once the fix is applied, further kernel upgrades will not cause this issue. The only time after you apply the fix that the issue will reoccur is when the OS is restored to the factory defaults."

This is from one of the Dell mailing lists.

Dennis N.

---

### Post by HotShotDJ on 2007-06-12
> **hasimir44 said:**
> True. Imagine your aunt/uncle/mom/etc.. trying to do this fix - not gonna happen. I can see it already - "it worked good for about 20 minutes, then it broke! these laptops suck!"Right.  But your aunt/uncle/mom/etc. are perfectly capable of taking care of the myriad of problems that present themselves when working with a Windows system.:roll:  Yeah... right!

A minor, well documented hiccup in the first set of machines Dell has shipped with Ubuntu is no big deal.  If we applied this same logic to Windows, Microsoft should have gone out of business 20 years ago.

---

