---
title: "Optiplex 330"
date: 2013-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jessepage1989 on 2013-01-23
Picked up a very cheap Dell optiplex 330 on ebay. It has a E7200 Core 2 duo processor with 2 gb ram 667mhz. It isn't top of the line but it is by all means a capable machine. Threw in a 6670 and a ssd drive i had laying around and installed ubuntu for everyday tasks. My issue is ubuntu 12.04 LTS 32bit is so slow. It is like retarded. This is a windows vista certified pc so this should be a super computer with linux. I don't kno what the issue may be perhaps i should try another distro? any thoughts? Getting 800mhz ram is out of the question. THe price is blasphemy for DDR2 ram.

---

### Post by papibe on 2013-01-23
Hi jessepage1989.

Ubuntu 12.04 is more demanding in graphics than previous versions.

Are you using the AMD proprietary driver? You should get better performance out the card with it. However, first, make sure the driver supports that model.

If you are not able to get the performance you are looking for, I'd recommend Xubuntu.

Let us know how it goes.
Regards.

---

### Post by jessepage1989 on 2013-01-23
I am using the proprietary driver. However I cannot use the updated proprietary driver. It keeps throwing me an error message saying see log. But the log is all greek to me

---

### Post by papibe on 2013-01-23
Could you post the result of this command?
```
/usr/lib/nux/unity_support_test -p  
```
Regards.

---

### Post by jessepage1989 on 2013-01-23
```
xxxxxx:~/Downloads$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6670
OpenGL version string:  4.2.11627 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
xxxxxx:~/Downloads$ 




```

---

### Post by papibe on 2013-01-23
It looks like, at least on terms of video capabilities, your card is supported.

Let's make sure the proprietary driver is loaded. Could you post the result of these 2 commands?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -i fglrx
```
Regards.

---

### Post by jessepage1989 on 2013-01-23
unfortunately i just broke it. tried installing the updated driver from amd website and now i have completely lost my gui. startx command no work either....looks as though i have to do a reinstall....

---

### Post by gifford on 2013-01-23
You might think about 64 bit install to see if performance will improve.

---

### Post by jessepage1989 on 2013-01-23
```
xxxxx-OptiPlex-330:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Turks [Radeon HD 6670] [1002:6758]
	Subsystem: XFX Pine Group Inc. Device [1682:3181]
	Kernel driver in use: fglrx_pci
xxxxx-OptiPlex-330:~$ lsmod | grep -i fglrx
fglrx                2909855  119 
xxxxx-OptiPlex-330:~$ 



```

---

### Post by jessepage1989 on 2013-01-24
So I guess I will try 64bit version and see if I have any luck

---

### Post by jessepage1989 on 2013-01-26
No luck with the 64bit version. After some research I am trying 10.04LTS. According to Ubunut 10.04lts is certified on the optiplex 330.

---

### Post by jessepage1989 on 2013-01-26
Got 10.04lts 32bit installed and all is well. Everything is lightning fast as expected and I successfully installed the updated drivers from amd's website for my 6670. I guess 12.04 is not that great for older hardware...

---

### Post by papibe on 2013-01-26
> **jessepage1989 said:**
> I guess 12.04 is not that great for older hardware...

That would be a fair assessment.

When you a chance, take a look at [Xubuntu]("http://xubuntu.org/"). It would be a 10.04-ish experience, although with an slightly different desktop, but with up-to-date repositories.

Best Regards.

---

### Post by jessepage1989 on 2013-01-27
Thanks for the reply and the help. I will be trying xubuntu 12.04 shortly

---

