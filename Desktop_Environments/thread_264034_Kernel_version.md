---
title: "Kernel version ???"
date: 2006-09-24
forum: Desktop Environments
---

### Post by JKoder on 2006-09-24
Hello
Can anyone tell me what kernel version is ubuntu using right now ?

i know that on my last update it was 2.6.15... what is it now ???

---

### Post by wieman01 on 2006-09-24
2.6.15-27 in Dapper Drake (6.06).

---

### Post by JKoder on 2006-09-24
> **wieman01 said:**
> 2.6.15-27 in Dapper Drake (6.06).

:( Thank you. This isn't righ for me because is causes m pc to work really slow.

Thank you !

---

### Post by kyozo on 2006-09-24
Is there anyway to see this in Ubuntu?

Also I have discovered that in my device manager, my cpu is listed as unknown. I have an AMD Athlon 1700. I found that Ubuntu was really slow when extracting compressed files, and I thought that was becuase i used the standard i386 kernel, not the one compiled for the AMD cpu.

I found this line sudo apt-get install kernel-k7 which should be optimized for all AMD kernels, but is it enabled by default, or am I still using the standard i386 version?

Should I somehow update the properties in the device manager, to reflect that I have an AMD Athlon kernel? If yes, then how?

Thanks in advance

Kyozo

---

### Post by veloct on 2006-09-24
Open a terminal and type:

```
 uname -a 
```

---

### Post by kyozo on 2006-09-24
> **veloct said:**
> Open a terminal and type:

```
 uname -a 
```

Thanks, looks like I'm running the K7 kernel now :)

Don't know if it's faster though, still think it's slow compared to windows and winrar, but that might be because winrar is better than the standard package manager? Although my cpu usage is only about 66%. Might be a slow disk or something?.

when i run ```
uname -p
``` it says unknown, does that matter?

Thanks, 

Kyozo

---

