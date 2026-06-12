---
title: "Need help troubleshooting segfault"
date: 2009-06-15
forum: General Help
---

### Post by modctek on 2009-06-15
Just recently, I've been getting a lot of segfaults, including the following every 5 minutes. I'm not certain when the errors started, as I've made many changes recently, both hardware and software updates:

```
Jun 14 06:05:01 northstar2 kernel: [16384.036201] php[14030]: segfault at 905a5c4 ip b7f22055 sp bfa333d0 error 4 in ld-2.8.90.so[b7f19000+1a000]
Jun 14 06:10:01 northstar2 kernel: [16684.134767] php[14111]: segfault at 905a5c4 ip b7f77055 sp bff88120 error 4 in ld-2.8.90.so[b7f6e000+1a000]
```

hald-runner is also segfaulting with a similar error:

```
Jun 14 01:35:01 northstar2 kernel: [  184.717326] hald-runner[7487]: segfault at 400048 ip b7e440a0 sp bfe407d8 error 4 in libc-2.8.90.so[b7da7000+158000]
Jun 14 01:39:01 northstar2 kernel: [  424.724467] hald-runner[7498]: segfault at 400048 ip b7e440a0 sp bfe407d8 error 4 in libc-2.8.90.so[b7da7000+158000]
```

Can someone point me in the right direction to start troubleshooting this problem?

---

### Post by modctek on 2009-06-15
Digging through my logs it looks like that same "ld-2.8.90.so" is connected to several other segfaults:

```
Jun 14 01:10:43 northstar2 kernel: [   60.805855] polkit-read-aut[6863]: segfault at b7d028d8 ip b7f7c4a5 sp bf8887a8 error 4 in ld-2.8.90.so[b7f6f000+1a000]
Jun 14 01:10:43 northstar2 kernel: [   60.946402] polkit-read-aut[6870]: segfault at c0f8a034 ip b7f7c383 sp bfb88f84 error 5 in ld-2.8.90.so[b7f6e000+1a000]
```

and:

```
Jun 14 01:10:54 northstar2 kernel: [   72.432688] gnome-settings-[7189]: segfault at 8b000000 ip b80f7740 sp bfffdde4 error 4 in ld-2.8.90.so[b80e2000+1a000]
Jun 14 01:10:54 northstar2 kernel: [   72.451549] gnome-settings-[7191]: segfault at e800024e ip b80c2765 sp bfcd7d2c error 5 in ld-2.8.90.so[b80bd000+1a000]
```

If I remember my newb training, isn't an ".so" file a source file? Perhaps this is part of a library that has become corrupt?

---

### Post by Psyphre on 2009-07-10
im getting segfaults too, how did u manage to get that info? I want to check mine and see if maybe we have the same source causing issues.

---

### Post by modctek on 2009-07-10
Unfortunately, the segfaults got so bad I had to wipe out and reinstall the OS. I tried reinstalling various libraries and packages, but the root cause seemed too multi-layered to figure out.

I took the opportunity to upgrade to Jaunty at the same time, and have not seen any segfaults since.

---

### Post by Psyphre on 2009-07-10
the problems stared shortly after i installed jaunty from a clean install. I wonder if one of the updates did it.

Anyway if its working for you then thats good.

---

### Post by credobyte on 2009-07-10
> **Psyphre said:**
> im getting segfaults too, how did u manage to get that info? I want to check mine and see if maybe we have the same source causing issues.

```
System -> Administration -> Log File viewer
```
Otherwise, go to [COLOR=Blue]/var/log[/COLOR] - all files are there ;)

---

### Post by t4thfavor on 2009-07-10
> **modctek said:**
> 
If I remember my newb training, isn't an ".so" file a source file? Perhaps this is part of a library that has become corrupt?


No its a kernel module. Which is binary, and without machine code knowledge or knowledge of the kernel debugger, I'm afraid your sunk.

I would start by testing your memory for at least 10 hours and see what memtest comes up with. Next try checking the temperature of your PC. If its not something alot of people are experiencing, then its probably local to your hardware, and you should start there.

---

### Post by iponeverything on 2009-07-10
> **t4thfavor said:**
> No its a kernel module. Which is binary, and without machine code knowledge or knowledge of the kernel debugger, I'm afraid your sunk.

I would start by testing your memory for at least 10 hours and see what memtest comes up with. Next try checking the temperature of your PC. If its not something alot of people are experiencing, then its probably local to your hardware, and you should start there.

Its not a kernel module, its a dynamic link library.

---

### Post by Psyphre on 2009-07-10
I have solved the problem.

What caused it was Global Menu. When disabled i get no errors and no segfaults.

---

