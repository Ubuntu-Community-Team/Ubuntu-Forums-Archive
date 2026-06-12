---
title: "386 Vs 686 kernel"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Rondonjin on 2006-06-05
Sorry if this has been asked before:

The 386 kernel is installed by default but there is a 686 kernel image for PPro/Celeron/PII/PIII/PIV machines. Is there any value in changing it? For the record, I already have, but don't see any noticable difference.

Wayne

---

### Post by solarwind on 2006-06-05
I believe that the 686 kernel supports over 2 gB of system memory while the 386 does not recognize any system memory over 2 gB. There are probably more advantages to using a 686 kernel that I'm not aware of.

---

### Post by Rondonjin on 2006-06-05
[QUOTE=solarwind]I believe that the 686 kernel supports over 2 gB of system memory while the 386 does not recognize any system memory over 2 gB. There are probably more advantages to using a 686 kernel that I'm not aware of.[/QUOTE]

It boots reasonably quickly (faster than FC5 on the same machine) and works so I should just be happy :) 

Wayne

---

### Post by hezral on 2006-06-05
i think the 686 are optimized for PPro/Celeron/PII/PIII/PIV cpus. i use them too and it does makes a little different in performance. try it

---

### Post by Rondonjin on 2006-06-05
[QUOTE=hezral]i think the 686 are optimized for PPro/Celeron/PII/PIII/PIV cpus. i use them too and it does makes a little different in performance. try it[/QUOTE]

Thanks. As I said I am using it but my machine is only a Celeron Tualatin 1.4 with 512Mb memory so I probably wouldn't notice much difference :-)

My typing speed has also not improved :wink: 

Wayne

---

### Post by flip314 on 2006-06-06
When you install the second kernel, both will show up in the grub menu, so you can always easily go back to the old one if you have problems.

There have been many optimized instructions added since the 386 days, and it's kind of a waste not to take advantage of them.  i386 is the default only since it's the most compatible.

---

### Post by Rondonjin on 2006-06-06
[QUOTE=flip314]When you install the second kernel, both will show up in the grub menu, so you can always easily go back to the old one if you have problems.

There have been many optimized instructions added since the 386 days, and it's kind of a waste not to take advantage of them.  i386 is the default only since it's the most compatible.[/QUOTE]

It won't show up any more :grin: After a few days making sure a new kernel is fine the old one and it's supporting files get transferred to never-neverland :-D 

Wayne

---

### Post by mcduck on 2006-06-06
[QUOTE=solarwind]I believe that the 686 kernel supports over 2 gB of system memory while the 386 does not recognize any system memory over 2 gB. There are probably more advantages to using a 686 kernel that I'm not aware of.[/QUOTE]
Actually the RAM limit of 386 kernel is less than 1GB.. ;)

Also 686 kernel supports certain multimedia-related instructions, like MMX, SSE and SSE2, so it might improve performance with certain apps that need intensive floating-point calculations. But it sure won't make your web browser or text editor any faster.

edit: note, that 686 kernel also works for all AMD CPU's (Athlon & later), but if you have one, you might want the K7 kernel instead, as in addition to instructions supported by 686 kernel the K7 also supports 3DNow! and 3DNow2 instructions provided by AMD CPU's..

---

### Post by Rondonjin on 2006-06-06
[QUOTE=mcduck]Actually the RAM limit of 386 kernel is less than 1GB.. ;)

Also 686 kernel supports certain multimedia-related instructions, like MMX, SSE and SSE2, so it might improve performance with certain apps that need intensive floating-point calculations. But it sure won't make your web browser or text editor any faster.[/QUOTE]

That's good to know, I use this machine a lot to watch DVDs, etc, that I can't play on the home DVD/HDD/VHS recorder.

Pity the 686 kernel is unable to do beer runs and stock the fridge with my favourite cold beverages :-)

Wayne

---

### Post by FredB on 2006-06-06
I am running a PC with 1 Gb of ram and 386 kernel and no problem at all.

```

fred@fredo:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        975         35          0         32        545
-/+ buffers/cache:        397        614
Swap:         2965         18       2946

```

---

### Post by RAOF on 2006-06-06
[QUOTE=mcduck]...
Also 686 kernel supports certain multimedia-related instructions, like MMX, SSE and SSE2, so it might improve performance with certain apps that need intensive floating-point calculations. But it sure won't make your web browser or text editor any faster.
...[/QUOTE]
This is incorrect, and **always** seems to be raised when talking about these kernels.  Application support for the various extension sets (MMX, SSE, 3dNow, etc) is **independant** of the kernel used.  If a program uses those instructions on a -686 kernel, it'll use them on a -386 kernel.  If it doesn't use them on a -386 kernel, it won't use them on a -686 kernel.

---

### Post by nocloud on 2006-06-06
is there a way to switch from one kernel to another without a complete reformat/reinstall?

---

### Post by elemental666 on 2006-06-06
if you install your kernel from the repos, it should automagically make the necessary changes to GRUB to when you boot you'll see all the kernels you've installed.  The kernel themselves live under the /boot directry and are compressed by default.  To remove one from your system you have to go delete the kernel image and edit the menu.lst file for GRUB.

You can compile your own kernel and add the necessary lines to GRUB's menu.lst file to enable booting from your custom kernel.

---

