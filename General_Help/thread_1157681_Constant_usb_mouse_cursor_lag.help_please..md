---
title: "Constant usb mouse cursor lag.help please."
date: 2009-05-12
forum: General Help
---

### Post by eageruser on 2009-05-12
Hi all,
 
I began my journey into ubunto this evening. I have searched the forum and net for a fix to my specific problem. I have not found any. Over all I am exited to be doing the migration I have wanted to do for years. 
 
The problem is my mouse, a Logitech M-UAE96 optical usb, is lagging like the cpu is doing some serious proccessing in the background. System monitor shows no problem there, though. It is constant, and I have rebooted, unplugged, and replugged. This is a good learning experience though. Let me know if this belongs in absolute beginers forum, because I am , just thought this may be a little technical.
 
 
Thank you in advance for any help,
Eageruser

---

### Post by geraldvillorente on 2009-05-13
Kindly post your specs here. Tnx

---

### Post by eageruser on 2009-05-13
Thank you,
 
ubuntu 32-bit
Amd 2.2 ghz single-core athalon
2.5g ram
4350 radeon 512ram
1tb segate drive 
pinnacle pci tv card
sb audigy

---

### Post by geraldvillorente on 2009-05-13
Ok, open your terminal and fire up this command:
```

top

```
then look for the system processes if who among them uses a very big amount of resources

EDIT: sorry for my bad english

---

### Post by eageruser on 2009-05-13
Only resources beign used are for "top" and the terminal, but both are intermittant and only use about 0.3% of the cpu each. The only constant is "init" which shows 0% cpu, 3884 for virt, 1884 for res, and 564 for shr. Everthing else is all zeros.

---

### Post by geraldvillorente on 2009-05-13
Kindly go to System-->Preferences-->Mouse and change the accelaration speed

---

### Post by eageruser on 2009-05-13
I tried different variation of the sliders but no luck

---

### Post by anoxia on 2010-05-22
I am having the same exact problem, but may  I also add that when doing a file transfer via USB, the mouse will work perfectly. I feel as though that the USB is being throttled.

---

