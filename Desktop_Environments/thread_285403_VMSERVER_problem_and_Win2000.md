---
title: "VMSERVER problem and Win2000"
date: 2006-10-26
forum: Desktop Environments
---

### Post by matjaz_pirnovar on 2006-10-26
Hi,

When installing WIn2000 on vmserver I get WARNING that if I'm running OS that is incompatible with WIn2000, then current OS might be damaged or deleted if I continue. Something like that. Please see the screenshot.
Should I proceed with installation?

[IMG]http://static.flickr.com/108/280138632_27b2998655.jpg?v=0[/IMG]

---

### Post by matjaz_pirnovar on 2006-10-29
Any clues about that? Has anyone had negative experience with vmserver?

Matjaz

---

### Post by msmeyer on 2006-10-29
I think this is just the standard "your harddisk is not yet partitioned" message which can safely ignored. The Win2k installation routine talks about the virtual hard disk of your virtual machine, not your real one and doesn't even know it's running inside Ubuntu.

I have been using VMWare with Linux (Redhat, then Ubuntu) for 4 years or so and never had the slightest problem.

HTH
Markus

---

### Post by tzulberti on 2006-10-29
I agree with msmeyer... I have installed WinXp, and do not have any problem...

---

### Post by theplatypus on 2006-10-29
No problems here.

---

### Post by matjaz_pirnovar on 2006-10-30
Hi, Thanks for the tips.

I haven't partitioned my hard disk. I used full hard disk capacity, so no other partititions - 100% Ubuntu. That's why I'm a bit worried, seem to be no Escape exits if smth goes wrong.

Can you confirm me that you have looked at the screen shot I posted....it says more accurately what I mean.

If you're sure, then I'll do it. 

Thanks for helping out.
Matjaz


> **msmeyer said:**
> I think this is just the standard "your harddisk is not yet partitioned" message which can safely ignored. The Win2k installation routine talks about the virtual hard disk of your virtual machine, not your real one and doesn't even know it's running inside Ubuntu.

I have been using VMWare with Linux (Redhat, then Ubuntu) for 4 years or so and never had the slightest problem.

HTH
Markus

---

### Post by krismatth3 on 2006-10-30
Are you using a virtual disk for the virtual machine, or do you have it pointing to your main hard disk?

I can confirm that this is a normal Win2k/XP install screen when the hard disk is not partitioned (or partitioned in a manner that Win32 cannot deal with).

---

### Post by matjaz_pirnovar on 2006-10-30
Thanks for advices. 

I have proceeded with installation and it workwd without any problem. So, now installation is complete. phew :)

Few things I need to discover now...but hopefully will manage.

EXCEPT HOW DO YOU GET ACCESS TO UBUNTU AND OTHER FILES FROM VMWARE - WIN2000?
For example USB doesn't appear in Win2000 only on Ubuntu, when I plug in the USB key... How do you access USB and other software? Are there any shared folders?

Thanks, much love
M

---

### Post by matjaz_pirnovar on 2006-11-04
Hi,

On my WIn2000 on vmserver, windows don't recognize USB key when I plug it in (usb drive appears only in Ubuntu).
And I don't know how to install any programmes like word or Excell.

How do you work with Virtual OS without including Ubuntu? 

Thenks, M

---

### Post by krismatth3 on 2006-11-04
Not to be rude, but VMWare's help file is the best reference for your questions.

Regards,
Kris

---

### Post by matjaz_pirnovar on 2006-11-07
Thanks :)

Guys in other section I posted question also added that USB isn't possible on vmserver at the moment and some other things.

Matjaz

---

