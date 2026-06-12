---
title: "UGS NX8 - Ubuntu 64bits 10.04LTS"
date: 2012-02-27
forum: Education &amp; Science
---

### Post by goliveira on 2012-02-27
HI!

I have install NX8 on Ubuntu 10.04, and i was perfect with nVidia Quadro  FX-380 and driver 2.90.10.. this was fine until i install some Ubuntu  updates, and the nVidia driver 2.95.20.

Now i have the ugraf, metacity and Xorg process "eating" my cpu, NX hang, and this message in my dmesg:
 
   ```
   CE: hpet increasing min_delta_ns 
```So, what could it be? The nVidia's driver update, the Ubuntu's updates?

Some bad configuration, some i missed?

---

### Post by goliveira on 2012-02-27
> **goliveira said:**
> HI!

I have install NX8 on Ubuntu 10.04, and i was perfect with nVidia Quadro  FX-380 and driver 2.90.10.. this was fine until i install some Ubuntu  updates, and the nVidia driver 2.95.20.

Now i have the ugraf, metacity and Xorg process "eating" my cpu, NX hang, and this message in my dmesg:
 
   ```
   CE: hpet increasing min_delta_ns 
```So, what could it be? The nVidia's driver update, the Ubuntu's updates?

Some bad configuration, some i missed?

I reinstalled the nVidia Driver, make sure nouveau was nos working, and until now everything is fine...
But when i try to add a printer,  File->Utilities->Pinter Administration, every fine ultil here,  after i choose the nxplot/printer file and click ok. Then, nothing, just  an error:

```
/usr/ugs080/nxplot/bin/sdiPrintAdmin_static:error while loading shared libraries: libMrm.so.3: wrong ELF class: ELFCLASS64 		 		  		  		 		  		  		  		 
```

---

### Post by goliveira on 2012-03-01
I was wrong, it was not over...

I could fix the hpet message by disable hyper threading in the BIOS and in the grub with "hpet=disable".

Now, when i execute NX it just does not finish to load, i can not see any error message in dmesg or log, and the swap is not even use, so every time i have to "kill" the ugraf, because ugraf, metacity and Xorg are "eating" the CPU.

I have an:
HP Z200 Wokstation
nVidia Quadro FX380 (driver 295.20)
kernel: 2.6.32-38-generic x86_64
RAM: 8GB

I do not know what could be wrong ¿?

---

### Post by goliveira on 2012-03-05
Hi!

I reinstall the NX8 and the upgrade, and everything works fine until i set and export the UGS_LICENSE_BUNDLE in the ugii file.... apparently ugraf start hang the CPU when i do that.

---

### Post by Joril on 2012-07-04
> **goliveira said:**
> 
But when i try to add a printer,  File->Utilities->Pinter Administration, every fine ultil here,  after i choose the nxplot/printer file and click ok. Then, nothing, just  an error:

```
/usr/ugs080/nxplot/bin/sdiPrintAdmin_static:error while loading shared libraries: libMrm.so.3: wrong ELF class: ELFCLASS64 		 		  		  		 		  		  		  		 
```

This is because NX ships with the 32bit version of the printing binaries... You have to install the 32bit version of libmotif3. I used getlibs for that: ```
getlibs -p libmotif3
```
Anyway that's not enough, the printing dialog will crash with a "buffer overflow detected" :(

---

