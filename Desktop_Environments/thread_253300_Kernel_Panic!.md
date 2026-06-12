---
title: "Kernel Panic!"
date: 2006-09-08
forum: Desktop Environments
---

### Post by lwr on 2006-09-08
Right, somehow I've messed up the kernel on my default boot. I just get some error messages about running out of ram memory and not being able to mount the harddrive or something along those lines. I can't tell you exactly because obviously I can't copy and paste, and it would take ages to write out. 

So, I pressed Esc while loading to give me a few options. I'm presented with 3 identical kernel options, with their 3 accompanying recovery modes. Recovery mode for the first one does the same as above. However, the second option (although seemingly identical) works fine.

My question - how do I get the machine to boot the second kernel option by default, which would seem to be the simplest solution to this problem.

Thanks

---

### Post by Ramses de Norre on 2006-09-08
The second kernel wont be the same, there will be differences in the numbers at the end of the line.
To set that kernel as default: ```
sudo gedit /boot/grub/menu.lst
```
And search for the line which now will say ```
default 0
``` You need to change the 0 to the number of the kernel you want to boot, starting at the first kernel with value 0. So for you probably 3.

---

### Post by lwr on 2006-09-08
Thank you very much for your help. Everything is sorted and working beautifully.
Oh, and take a look at this:

<picture removed>

Strange I know, but they're definitely the same. I even went to edit them, and they appear exactly the same.

Oh well, thanks again. Kernel panic over.

---

### Post by Ramses de Norre on 2006-09-08
Take a look very close:
```
2.6.15-**26**-386
2.6.15-**25**-386
```
They do differ ;)

---

### Post by lwr on 2006-09-08
Double post

---

### Post by lwr on 2006-09-08
Sincere appologies for being blind! I was too busy looking at the end of the line, but I guess that just refers to the system architecture. Am I at any disadvantage booting an older kernel version? I guess when the next kernel update comes out, I can just use that right?

---

### Post by Ramses de Norre on 2006-09-08
Absolutely, and it's not a big disadvantage as everything works in the older one. I've needed to do this allready a couple of times too due to some kernels not working here.
You'll still receive all upgrades and the newer kernel will be automatically default I think.

---

### Post by lwr on 2006-09-08
Thanks very much for all your help. I can't get over how I missed the differences in kernel numbers - so obvious now. Anyway, thanks again.

---

