---
title: "[SOLVED] Need drivers after install for cdrom"
date: 2008-11-30
forum: Desktop Environments
---

### Post by jodi5549 on 2008-11-30
Hello, I'm am a newby and have intalled xubuntu on an old Compaq Presario desktop. My specs were fat32, x86 fam 5, model 8 stepping 12 AMD-K6-3D, 400 mhz, 4 gb harddrive 256mb ram. I download the .iso with Infra Recorder and check it with MD5
SUM. The xubuntu is running fine accept I cannot use the cdrom and floppy disk. I went into system, driver and states no propietary are in use on this system. How can I get my drivers back? I'm able to get online ok. The cdrom was a compaq CRD 8322B, I think it is Quantum Fireball cr4.3A or that might be my hard driveand sound card Ess1969 PCI Audiodrive (wdm)if that means anything. Is there any way I can get the driver to make this stuff work? Please help :confused:

---

### Post by inobe on 2008-11-30
hi and welcome 


if you click on places' your drives should be in there, simply click them to mount the drives .

---

### Post by jodi5549 on 2008-11-30
you've lost me there, very new to xubuntu, click "places". Were is that?

---

### Post by inobe on 2008-11-30
if i am not mistaken' its located on the panel/ task bar on the top left side.

edit: wait, that is wrong......

let me check, i forgot that xubuntu has a applications menu only.

---

### Post by jodi5549 on 2008-11-30
Ok, thank you, but I click place and only found floppy drive and clicked on it and says failed to mount floopy drive. No cd drive and everything did work before I installed xubuntu. I thought it would pick everything. What can I do now?

---

### Post by inobe on 2008-11-30
find terminal and copy this command then paste it in terminal.

```
ls -l /media/cdrom
```

copy the output and paste in on your next post.

---

### Post by jodi5549 on 2008-11-30
Im sure I got this right but here it is:

sherrie@office:~$ 1s -1/media/cdrom
bash: 1s: command not found
sherrie@office:~$

---

### Post by jodi5549 on 2008-11-30
inobe, are you still there? That command didn't work. Can you still help or anyone else? Thank You

---

### Post by ugm6hr on 2008-11-30
> **jodi5549 said:**
> inobe, are you still there? That command didn't work. Can you still help or anyone else? Thank You

Copy and paste the command.

You have tyoed it wrong.  They are small L's, not 1.  And get the spaces right too.

---

### Post by jodi5549 on 2008-11-30
Thank you so much for replying so quick ugm6hr, I'm new at this stuff so please bear with me. Here is what came up:

lrwxrwxrwx 1 root root 6 2008-11-28 17:23 /media/cdrom -> cdrom0

---

### Post by jodi5549 on 2008-11-30
After putting in the command above what do I do next? Should it not be able to play any music cd? It is not doing anything

---

### Post by jodi5549 on 2008-12-01
Please is there anyone that can help me with this stuff. I have read and read through the forums and help and don't see anything regarding me not being able to get the cdrom to read anything which I think I lost the drivers when I installed xubuntu. The floopy also states unable to mount "Floppy Drive" as I stated in above quote. I am very newby at this stuff putting in commands and I did as stated, but where do I go from there? I'm am so lost, please help me and stay with me on this. Thank You

---

