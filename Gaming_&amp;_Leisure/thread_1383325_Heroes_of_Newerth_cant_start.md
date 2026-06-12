---
title: "Heroes of Newerth cant start"
date: 2010-01-17
forum: Gaming &amp; Leisure
---

### Post by Huntix on 2010-01-17
Hello to everyone i download HoN for linux I installed and when i try to start my screen going black for a sec and then nothing i tryed from the command prompt still not work  it says > warning: The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: ARB_vertex_buffer_object not available.

---

### Post by Perfect Storm on 2010-01-17
Which video card do you have?

---

### Post by Huntix on 2010-01-17
Nvidia GeForce 9500

---

### Post by Funnnny on 2010-01-17
What driver you are using ?
What version of HoN you are trying to install ?

---

### Post by Huntix on 2010-01-17
I didnt install the driver bec it giving me an error

---

### Post by Perfect Storm on 2010-01-17
> **Huntix said:**
> I didnt install the driver bec it giving me an error

You can't run HoN without the driver for your card. You need to solve your driver problem first.

---

### Post by Huntix on 2010-01-17
I dont know how to fix it :(

---

### Post by Perfect Storm on 2010-01-17
Try search and/or make a thread about your driver issue in our hardware forum: [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

---

### Post by mk00436 on 2012-02-18
i got the same problem when i start heroes i got:
warning: The VAD has been replaced by a hack pending a complete rewrite
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Value in failed request:  0xa00
  Serial number of failed request:  71
  Current serial number in output stream:  72
my graphics card is : ati radeon HD 4800 series 
driver VESA: RV770

---

### Post by donkyhotay on 2012-02-19
> **mk00436 said:**
> i got the same problem when i start heroes i got:
warning: The VAD has been replaced by a hack pending a complete rewrite
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Value in failed request:  0xa00
  Serial number of failed request:  71
  Current serial number in output stream:  72
my graphics card is : ati radeon HD 4800 series 
driver VESA: RV770

The VESA driver is a 'default' driver meaning you don't have a 3D graphics driver. You need to install a radeon driver, try installing from hardware drivers in the administration menu and if that fails download/install from the [radeon website](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English). Might want to double check the details of that download. I think it's the right one based off what you posted but I could be wrong.

---

