---
title: "No X Server after Kernel upgrade?"
date: 2006-01-12
forum: General Help
---

### Post by Protex on 2006-01-12
Hey there guys, it's me yet again.

I was interested in getting a performance boost by upgrading my kernel to the latest K7 build in the repositories. I did so everything seemed fine, but X won't start. I've tried redownloading the drivers, reinstalling, re-enabling, and still X fails.

The message it gives me goes something like:

[I](EE)Failure loading nVidia kernel module
(EE)
(EE)Screens found, but no suitable mode (or something)

No screens found!

X failed.[/I]

Something like that, any ideas? I am also using initNG but have the nVidia driver loaded into the initial.i (same configuration that allows me to boot normally under old kernel).

Thanks in advance.

---

### Post by Sepht on 2006-01-12
yeh it's a dead simple issue. (honostly if you need help with this, you shouldn't be using something as unstable and bad as initNG)

drivers work on a per-kernel basis and are compiled to run against it (look in /lib/modules) So whether it's nvidia drivers or ati drivers or wireless drivers: you need to rebuild the modules for the new kernel

---

### Post by Protex on 2006-01-12
[QUOTE=Sepht]yeh it's a dead simple issue. (honostly if you need help with this, you shouldn't be using something as unstable and bad as initNG)

drivers work on a per-kernel basis and are compiled to run against it (look in /lib/modules) So whether it's nvidia drivers or ati drivers or wireless drivers: you need to rebuild the modules for the new kernel[/QUOTE]

Well I am fairly new to Linux and still trying different things to try and broaden my knowledge.

Could you tell me how to rebuild the nVidia modules?

---

### Post by codejunkie on 2006-01-12
[QUOTE=Protex]Well I am fairly new to Linux and still trying different things to try and broaden my knowledge.

Could you tell me how to rebuild the nVidia modules?[/QUOTE]
first how did you install the nvidia driver, did you download the driver from [www.nvidia.com](www.nvidia.com) and manually install it or did you install it using synaptic?

---

### Post by Protex on 2006-01-12
[QUOTE=codejunkie]first how did you install the nvidia driver, did you download the driver from [www.nvidia.com](www.nvidia.com) and manually install it or did you install it using synaptic?[/QUOTE]

I used 'apt-get' from the command line.

---

### Post by Sepht on 2006-01-12
Download the drivers from nvidia.com and then when your in commandline(xserver can't be running) just execute the drivers and go through the install and it'll build you a new set for your kernel, then Xorg will boot fine

---

### Post by codejunkie on 2006-01-12
[QUOTE=Protex]I used 'apt-get' from the command line.[/QUOTE]
so you used apt-get install nvidia-glx package right? if so it should work just installing the restricted modules for your new kernel with
```
sudo apt-get install linux-restricted-modules-`uname -r`
```
see if that works and we'll go from there where your using initNG it might take a little tweaking.

---

### Post by Protex on 2006-01-12
That's really strange, I reinstalled the kernel and rebooted and this time it worked. Did not give me an X error.

Going to try initNG now, see if same result.

**edit**: Yes, all works well. Weird that it didn't work before, and I did nothing differently (that I know of).Oh well, thanks for the help!

---

