---
title: "&quot;Loading, please wait&quot; forever.. Ubuntu 8.10 -&gt; 9.04"
date: 2009-04-24
forum: General Help
---

### Post by amado_felipe on 2009-04-24
Hi, I tried to upgrade Ubuntu 8.10 to 9.04 but when it restarted... when I try to boot it doesn't work anymore, it appears "Loading, please wait..." and it stucks... 
So I tried to boot the repair mode, but that's what I get:
[http://img16.imageshack.us/img16/4295/sdc11069.jpg](http://img16.imageshack.us/img16/4295/sdc11069.jpg)

Somebody can help me please??

---

### Post by Vic Morgan on 2009-04-26
I had a similar problem. I mistakenly upgraded to X86 version when my computer was a higher spec. The X86 version doesn't run (as quoted) on virtually any computer, so I had the same outcome as you. Is your computer a dual core or similar? If so, use the AMD64 version of Ubuntu 9.04. That sorted my problem out.

---

### Post by Don1500 on 2009-04-26
I hope you downloaded the .iso and made a live disk. I, too, tried to upgrade from the manager. It took forever and when it finally completed it didn't work well (or at all most of the time.) But as it was "upgrading" I downloaded the ISO and made the live disk on another computer, then I installed Jaunty on my laptop with no problems. I then stopped trying to use the updated version on my desktop and started over with the CD. Jaunty is now running, but I'm not as confident with this install as I am with the laptop. Jaunty just doesn't feel as stable as Hardy. I'm sure I'll work the kinks out of my system but I really would have liked the online upgrade to work better.

---

### Post by Phat Phreddy on 2009-04-28
Just to echo this exact thing is happening to me. 

Ibex 8.10 was running fine (under wubi) I did the upgrade and the machine reboots and sits there (forever, or overnight anyway) with "Loading.. please wait". 

I was able to reboot earlier kernels in grub but the system seemed (increasingly) unstable.. I figured it might be a wubi issue as I was low on system space before the upgrade. My 'test' install of 8.10 had been running fine for so long I just never got round to doing a proper stand alone install.

Booted windows for the first time in months.. DL'ed a live CD i386 version.. Shifted some files and scrubbed an 80GB disc partition for install.. Reboot and boot the live CD, the ubuntu logo and menu comes up with options to boot to live CD, install, check discs for errors, and test mem.. Only test memory works all of the others just go to a loading please wait and flashing cursor or blank screen (check disks for errors). I have left them for 30+ mins without any changes. 

9.04 has been a real balls up for my system.. Having to type from windows.. Every reboot takes minutes.. Save me.. Please..

---

### Post by Phat Phreddy on 2009-04-28
BTW this is a P4 2.2, 2GB ram, 7300 nVidea.. Not really old and ran Ibex fine.

---

### Post by Phat Phreddy on 2009-04-28
More info.. 

Checked my live CD (desktop i386) download MD5 and its fine.. 

did a wubi install.. Exactly the same thing.. Installs fine then reboot, pick linux and "Loading, Please wait.." 

Ibex worked 100%.. Vista and XP both boot (I wont say work 100%).. But 9.04 is not going anywhere.

---

### Post by Phat Phreddy on 2009-04-28
Its some kind of power management BIOS conflict.. 

Once I try ACPI=OFF it isntalls.. 

I am still seeing a couple of flashed errors on boot about BIOS PnP fail but will look into solving them afetr I get my apps setup again.

---

### Post by kenfeyl on 2009-04-28
I had a similar issue: waiting forever on "Starting up..."

As Phat Phreddy suggested, turning off ACPI "fixed" it for me in the sense that Jaunty boots normally. Sadly, the fix comes at a cost, since under any sizable CPU load with ACPI off, the computer will quickly overheat and shut itself down.

The issue is a regression in Jaunty's 2.6.28 kernel. Since a high CPU load is a regular part of my usage, I downgraded my kernel to 2.6.27.18 to get ACPI to work again. Of course, this breaks other things in the system that worked great for the first time in 2.6.28 (e.g., my on-board microphone).

Sadly, I have tried the next few kernels -- 2.6.29, 2.6.29.1, 2.6.30-rc3 -- and all of them still have the ACPI issue.

---

### Post by eleison on 2009-04-28
I have a Dell Inspiron 2650 with the same problem. I did an upgrade install and could not get past "Loading, please wait." I checked the forums this morning and found that disabling ACPI allowed me to boot. However, I have not used the laptop enough to see if it overheats as kenfeyl is experiencing.

---

