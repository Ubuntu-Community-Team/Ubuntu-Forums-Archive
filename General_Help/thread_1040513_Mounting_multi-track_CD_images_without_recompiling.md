---
title: "Mounting multi-track CD images without recompiling kernel?"
date: 2009-01-15
forum: General Help
---

### Post by Anamon on 2009-01-15
I was looking for a way to mount a multi-track CD image into my filesystem. As 'mount' is only able to mount single-track ISO9660 images, I was looking for an application that would allow me to do it. In my particular case, it is a mixed-mode (1 data track, several audio tracks) image in MDF/MDS format.

Most tools, like AcetaneISO, also support only single-track images. The only one that seems to support multiple tracks is [CDemu](http://cdemu.sourceforge.net), but it requires a kernel module.

Now, I'm not really into kernel recompilation, and I think the effort is not really justified. So I wanted to ask whether I have missed a tool that could do what I want, or whether maybe it is impossible to achieve without a kernel module.

---

### Post by KeyserSoze93 on 2009-01-15
> **Anamon said:**
> I was looking for a way to mount a multi-track CD image into my filesystem. As 'mount' is only able to mount single-track ISO9660 images, I was looking for an application that would allow me to do it. In my particular case, it is a mixed-mode (1 data track, several audio tracks) image in MDF/MDS format.

Most tools, like AcetaneISO, also support only single-track images. The only one that seems to support multiple tracks is [CDemu](http://cdemu.sourceforge.net), but it requires a kernel module.

Now, I'm not really into kernel recompilation, and I think the effort is not really justified. So I wanted to ask whether I have missed a tool that could do what I want, or whether maybe it is impossible to achieve without a kernel module.

You should go with CD emu, it works fine and does not require compiling the kernel, only a kernel module, which can (and will, when you install) be done automatically without any messy config options. 

If you do install cd emu (preferably through its repository: deb [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) hardy main), it's really easy to use. Just run:

[SUDO]sudo cdemu -b system -d[/CODE] to load the daemon, and then: ```
cdemu -b system load 0 path/to/image.mdf
``` and you'll be set up.

The new device is created as /dev/scdX, where X is the next free device number.

When you want to unmount, run ```
cdemu -b system unload 0
```

It really is very easy to use, and the only tool I could fine for multi-track images (since it emulates the whole drive access mechanism, not just the file system)

---

### Post by Anamon on 2009-01-16
Wow, thank you so much!

For some reason I figured that "kernel module" meant that I would have to recompile the whole thing. But with that repository I had my virtual drive up and running in less than 5 minutes :cool:

You really saved me a lot of time there. Cheers!

---

### Post by elitenoobboy on 2009-03-06
I can see that cdemu has created a new virtual drive, after I did the "cdemu -b system load 0 path/to/image.mdf" command (which returned with no error), but how do I access the data that was just mounted to the virtual drive? Nothing shows up in /media/ and in Places>cd/dvdDrive clicking on the new VD does nothing; it's like it's blank. Did I do something wrong?

EDIT: Actually, I may have been using a bad image file that I burned from a scratched disk that had the same problem, IIRC. I'll have to try to good image file and try again.

---

