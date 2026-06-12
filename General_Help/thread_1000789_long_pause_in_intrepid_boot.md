---
title: "long pause in intrepid boot"
date: 2008-12-03
forum: General Help
---

### Post by dhmejia on 2008-12-03
I have problems in Ubuntu Intrepid 64-bit, after the grub stays in the text "Starting up ..." for a long time and then continue loading system.

The bootchart shows a waiting 17 seconds before boot.

I try changing the partition of Ubuntu hd1 to hd0 but there was no change, also added "profile" to the kernel line of grub.

System:
HP dv4-1125nr
2.00 GHz Intel Core 2 Duo Processor T5800
Intel Graphics Media Accelerator 4500MHD
HD: 250 GB (5400 rpm)
RAM: 4Gb

PD: Sorry, English isn't my language.

Thanks for your help.

---

### Post by iponeverything on 2008-12-03
It sounds like is probing for  something and timing out.  Try going to bios and disabling some of the controlers that are not in use.

ie. SATA or PATA, floppy etc.

---

### Post by philinux on 2008-12-03
Try unplugging any usb stuff like webcam and card readers etc.

---

### Post by Jorge_C on 2008-12-03
I think it is a buggy bios, just to make sure, attach the text file this will create:
```
dmesg > log
```
I have an hp dv7-1080es and this is a problem for me too, but it seems to have a solution. Let's see if we share the same problem

---

### Post by dhmejia on 2008-12-03
thanks for your response, 

The bios only allows me to disable booting from a floppy usb, Windows Vista also started normally, but already eliminated vista of my notebook.

The grub menu displays normally, the delay was introduced after selecting the operating system.

in dmesg log file I get error in these lines:

[1.925840] pci 0000:00:02.0: Boot video device
[9.924007] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[17.924007] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[17.924247] pcieport-driver 0000:00:1c.0: setting latency timer to 64

Thanks again,

Diego.

---

### Post by Jorge_C on 2008-12-03
Yeah, that's a buggy bios. Check you bios options and search for something like USB Device Legacy Support and disable it. If the bios doesn't have that setting, try upgrading the bios. Though, I upgraded mine with no luck.

If all that fails, the workaround involves compiling the kernel and changing the wait time to something much smaller. It may sound very difficult, but I hadn't done that before and managed to do it well. If you can't find the USB Device Legacy Support in you bios and the bios upgrade doesn't work either, I'll do my best helping you to compile the kernel, even if my experience is limited.

Regards

---

### Post by dhmejia on 2008-12-03
Thanks again,

To upgrade the bios I need to install Windows Vista again, or is there another method?

The bios will not let me change almost nothing.

In your case: Improved boot time when compiling the kernel? and I have to compile each new kernel version?

I'm interested in compiling the kernel, I will begin to read on the subject and your help is welcome.

Regards

---

### Post by Jorge_C on 2008-12-03
> **dhmejia said:**
> 
Thanks again,
You're welcome :)
> 
To upgrade the bios I need to install Windows Vista again, or is there another method?
Sorry, I forgot you had already deleted Windows. There might be a way to upgrade the bios from linux, but I'm not aware of it. Personally, I wouldn't mess with it unless I really knew it would work perfectly. Besides, after upgrading my bios the problem remained.
> 
The bios will not let me change almost nothing.
Sadly, that seems to be quite common.
> 
In your case: Improved boot time , when compiling the kernel? and I have to compile each new kernel version?
Sure, check yourself the two bootcharts attached, and my 17 seconds back ;). Though, I'm afraid you have to compile each new version (less than one hour for me).
> 
I'm interested in compiling the kernel, I will begin to read on the subject and your help is welcome.

Good, I'm quite busy know (exams and so on...) but I'll certainly try to help you. Basically, the extra step in you kernel compilation will be changing a wait time of 5000 to something smaller, like 50 or something; in a source file (/drivers/usb/host/pci-quirks.c) of the kernel before compiling. Read as much as you can about kernel compilation, and hopefully I'll try to post detailed instructions this weekend.

---

### Post by dhmejia on 2008-12-05
I compiled the kernel, time was reduced from 17 to 7 seconds but lost the wifi connection, I don't understand that it uses the same configuration of the kernel-generic, but to do so I had to disable the option "paravirtualized guest support", apparently is a bug in intrepid 64.

I see you also have a HP, are able to operate the remote infrared?

---

### Post by Jorge_C on 2008-12-10
Sorry for the delay, how come you still have to wait 7 seconds? What wait-time did you set? I don't know why you could lose your wifi :confused:
I also had to disable "paravirtualized guest support", else I got some errors but I assumed it was my lack of experience and not a bug.

Regarding the remote IR, well, I haven't tested it yet...I'll let you know in a couple of weeks if it works, since I don't have it with me now.

---

### Post by dhmejia on 2008-12-16
>  how come you still have to wait 7 seconds? What wait-time did you set?

I changed 5000 to 50 in /drivers/usb/host/pci-quirks.c

I did not do any other changes, just disable "paravirtualized guest support".

I am a little busy these days, by the time I'm with the generic kernel.

In a couple of weeks will return to the topic

Thanks again,

---

### Post by porksome on 2009-03-17
I am experienceing the BIOS handoff bug in jaunty. Is it possible to pass a parameter to the kernel via menu.lst to reduce the timeout?

I can compile my own kernel but this seems a little wasteful recompiling a working kernel just to change one timeout value.

When your time is stretched you can do without recompiling kernels everytime an update arrives.

Thanks in advance.

:-)

---

### Post by Jorge_C on 2009-03-18
Unfortunately, I'm not aware of any boot option that could reduce the timeout, and I really doubt it is possible without recompiling.

---

