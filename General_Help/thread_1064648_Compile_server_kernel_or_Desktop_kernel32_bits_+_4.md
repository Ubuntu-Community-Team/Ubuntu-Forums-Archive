---
title: "Compile server kernel or Desktop kernel?32 bits + 4 GB RAM"
date: 2009-02-09
forum: General Help
---

### Post by primolarry on 2009-02-09
Hi there,

My new PC has 4 Gb RAM, and googling I found out that most people prefer to use the server kernel to recognize it instead of using the 64 bit version of ubuntu, so I did that.

The memory is correctly recognized now, but I have some minor problems.

-My card reader won't work, but it does with a desktop kernel.

-As starting ubuntu, my external hard drive won't appear mounted. However, if I swith it off and back on, it does appear correctly. As before, this doesn't happen with a desktop kernel.

I think (otherwise please correct me) that the solution should be compile either the server kernel with the usb and sd missing modules, or compile the desktop kernel with the RAM missing module.

My question is, which one do you guys think I sould compile, and if anyone knows where are the modules that I should mark in both cases, that would be appreciated too.

Thanks a lot, regards

PD: I think these post belongs more to "General Help" rather than the "Server platforms" one, but if the admins disagree, please move it.

---

### Post by blazemore on 2009-02-09
I'd use the 64 bit desktop kernel, unless you have a reason not to (Which it doesn't look like you do )

The good thing about compiling is you can strip out the stuff you don't want, making for faster operation and boot times.

---

### Post by primolarry on 2009-02-09
Hi blazemore,

Thanks for your answer, but I don't have to choose anymore. I solved the SD card problem by modprobing "mmc_block" and the usb problem happens as well in Windows, so it must be a hardware problem. I will contact the motherboard manufacturer for that one.

Thanks anyway, regards

---

### Post by primolarry on 2009-02-09
By the way, where's the "mark as solved" button?

---

### Post by blazemore on 2009-02-10
Under Thread Tools

---

