---
title: "2 things:"
date: 2006-01-08
forum: Desktop Environments
---

### Post by tht00 on 2006-01-08
Alright- I'm trying to work through an issue with an nvidia driver (yes, I've been through the how-to's multiple times and have two processes pretty well memorized, both freezing while loading X/gnome).

Anyways, I've been over on the nvidia linux forum trying to work through this, and netllama gave me a list of things to try- [http://www.nvnews.net/vbulletin/showpost.php?p=787047&postcount=98](http://www.nvnews.net/vbulletin/showpost.php?p=787047&postcount=98)

I've tried the first one, with no success, so on to the rest, which I have a question about 2 of them.

[QUOTE=netllama]1) Does this problem go away if you remove the vesafb kernel module from loading?[/QUOTE]

Ok... a searched around on this forum and the nvidia forum without uncovering much.  Not sure where to start.

[quote=netllama]2) Does this problem go away if you upgrade to more recent kernel, such as 2.6.14.5 ?[/quote]

Is that this? [http://www.ubuntuforums.org/showthread.php?t=84174](http://www.ubuntuforums.org/showthread.php?t=84174)

Is it likely that I'll have problems after upgrading, or is it fairly painless (I have no idea what to expect).

I think thats all for now.

---

### Post by Ubluntu on 2006-01-08
This probably isn't going to help, but what kernel are you running and what type of pc do you have. I had a hard time getting certain kernels to work with certain video cards. If you have a P4 or something never like that you should try the 686 kernel or the 686 smp if you have hyperthread. I don't believe there is much harm trying different kernels because you can always restart and use the one that worked(or didn't work in your case)

I had problems with the 386 kernel when I installed a package, so I tried 686-smp because I have a hyperthread, the smp kernel would lock up half way, and the 686  worked great.

---

### Post by Azriphale on 2006-01-08
Are you trying to install the driver from the official NVIDIA-xxxxxxxx.run file downloaded from nvidia?

If so, see if this works

before trying to install it, get into X using the "nv" driver (does that work...?), open up Synaptic and remove:
nvidia-glx
nvidia-settings
linux-restricted-modules

make sure you have the following installed: 
build-essential
gcc-3.4
linux-headers (the ones that refer to the kernel you have installed. i.e. I have linux-headers-686-smp)

then close everything, hit ctrl+alt+backspace
hit ctrl+alt+F1 to get to a virtual console.

go to where your NVIDIA driver package is and run the following:
```
sudo /etc/init.d/gdm stop
CC=gcc-3.4 sudo ./NVIDIA-Linux-x86-1.0-8178-pkg1.run
```
or whatever driver you are trying to install
change your xorg.conf to the nvidia driver and start X.

---

### Post by tht00 on 2006-01-08
[QUOTE=Ubluntu]This probably isn't going to help, but what kernel are you running and what type of pc do you have. I had a hard time getting certain kernels to work with certain video cards. If you have a P4 or something never like that you should try the 686 kernel or the 686 smp if you have hyperthread. I don't believe there is much harm trying different kernels because you can always restart and use the one that worked(or didn't work in your case)

I had problems with the 386 kernel when I installed a package, so I tried 686-smp because I have a hyperthread, the smp kernel would lock up half way, and the 686  worked great.[/QUOTE]

I have a 64-amd.  I believe it is a 64 bit Athlon 3300+ on an ASUS K8S-LA Salmon MB.  Its an HP, and the MB, as far as I can tell, is pretty much on only HP computers (yay :-| ).  I've updated the BIOS to the newest as well.

Anyway, 'uname -r' give me
2.6.12-10-386

So... what is the different than in the 686 kernel and whatnot?

Also, if I get a kernel installed that doesn't work, where do I need to go to change it back?

Keep in mind that I'm fairly new to the unix/linux architecture and trying to figure this out as I go.  Any resources that go into depth on this would be great.

[QUOTE=Azriphale]Are you trying to install the driver from the official NVIDIA-xxxxxxxx.run file downloaded from nvidia?[/QUOTE]

As of now, yes.  I've tried the nvidia-glx driver from synaptic, and also the official drivers (.run) from nvidia with older versions (6xxx) and the top 2 newest ones.  I had the problem way back on 5.04 when I first started on Linux, then got frustrated and left it for a while, and I'm back with 5.10.  Anyway, whenever I get *any* driver installed properly, with a properly configured xorg.conf, it does a hard lockup (blackscreen) when it boots X, just before it should show the nvidia splash.

I have gotten it to boot by setting NvAGP to 0 in the xorg.conf file, but then its also a lot slower than it should really be.

(just saw your edit- been there, done that- plenty of times)

---

### Post by Azriphale on 2006-01-08
For installing a different kernel, simply install one in synaptic..
but DO NOT remove the old one!!!

the 686 kernels are for new-ish Intels. For your AMD, try the linux-image-k7

You will notice the next time you boot that there are a few more boot options in grub. The top one will be the new kernel you just installed, and a couple down you will see your previous kernel. 

If the new kernel does not boot, you are still able to go back and try the old one.

---

### Post by Thirsteh on 2006-01-08
*Nod* you shouldn't install the *86 kernels for an AMD cpu usually, however, if you're having compability problems, this could actually be the fix to it.

Until then, use k7-k8 or whatever version they're at now.

---

### Post by Azriphale on 2006-01-08
the difference between all these kernels is that they are compiled for specific architectures. This means that they are able to use processor-specific extensions, rather than only the old 386 instructions, which are supported by all x86 compatible processors today. Running the 386 kernel gives the most compatability, running a k7 kernel in your case shoud give slight performance benefits.

I have a P4 hyperthreading, which is, essentially 2 logical CPUs. If I use the 386 kernel, I can only use one. If I use the 686-smp kernel, I gain access to both.

---

### Post by tht00 on 2006-01-08
[QUOTE=Azriphale]For installing a different kernel, simply install one in synaptic..
but DO NOT remove the old one!!!

the 686 kernels are for new-ish Intels. For your AMD, try the linux-image-k7

You will notice the next time you boot that there are a few more boot options in grub. The top one will be the new kernel you just installed, and a couple down you will see your previous kernel. 

If the new kernel does not boot, you are still able to go back and try the old one.[/QUOTE]
[QUOTE=Thirsteh]*Nod* you shouldn't install the *86 kernels for an AMD cpu usually, however, if you're having compability problems, this could actually be the fix to it.

Until then, use k7-k8 or whatever version they're at now.[/QUOTE]

Alright- thank you both.  I wasn't aware of the kernel differences.  I'm going to try that tomorrow, as it is getting very late/early/whatever here (4am).

I'll let you know what I come up with. :)

---

### Post by tht00 on 2006-01-08
Ok- when I run the k7 kernel X crashes and I get:

```
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

```
(entire log attached)

So... do I need to compile the nvidia driver *for* the k7 kernel?  How would I go about doing that?  It seems to default to the x86 one.

---

### Post by Azriphale on 2006-01-08
you do need a specific kernel module for different kernels, yes.

What you should perhaps try is reinstalling nvidia-glx and nvidia-settings, or (what I would do) is try reinstalling the official nvidia driver. 

I believe you've been through it a good few times already.

---

### Post by tht00 on 2006-01-08
Still the same results with the k7 kernel.  I tried the nvidia-glx through synaptic- no change, and even ran an agrument to ensure that its compiling for the k7 when installing the official:

sudo sh NVIDIA-Linux-x86-1.0-8178-pkg1.run --kernel-source-path=/lib/modules/2.6.12-10-k7/build

Same hang unless NvAGP is disabled in xorg.

---

### Post by Azriphale on 2006-01-08
Sorry, I think I'm at my limit for now. Lets see if there is anybody else out there that can help you..

Anybody?

---

### Post by tht00 on 2006-01-08
Alright- thanks for trying.

[quote=netllama]1) Does this problem go away if you remove the vesafb kernel module from loading?[/quote]

How about back to the first post- anyone have any ideas on how I would go about this?

---

### Post by handy on 2006-01-08
Yes the AMD64 is completely 32bit compatible.  I've run it on 64bit Breezy & now on 32bit Breezy (where I'm happier at the moment).

[**EDIT:]** The compatability statement is not based on my experience, it is the architectural foundation of the AMD64 CPU's.

I know it is possibly a long shot, but, I've installed my nVidia (c) drivers both times - 64 then 32bit - using **Automatix**, smooth as glass, any dependencies & all that are taken care of.

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

It might work for you.  I know I that also might be missing the whole point!  I am new at Ubuntu (linux). 

All the best. 

handy

---

### Post by Azriphale on 2006-01-09
I don't have much time for a reply now -- get to get to work...

To unload a module on the fly, run the command:
```
sudo rmmod <module-name>
```

I'm not certain exactly how to stop that one from loading, and I can't check now...

---

### Post by tht00 on 2006-01-10
handy, thanks for that, but the problem doesn't seem to be with the *installation* of the driver.  I did download and install Automatix, and it looks like a useful tool.

[QUOTE=Azriphale]I don't have much time for a reply now -- get to get to work...

To unload a module on the fly, run the command:
```
sudo rmmod <module-name>
```

I'm not certain exactly how to stop that one from loading, and I can't check now...[/QUOTE]

Yeah, that probably won't help me, as it crashes on boot-up...  unless I can boot up in recovery mode, unload the module, and then start the GUI?  Might try that later, as I've got homework to do and class to go to.

---

### Post by Azriphale on 2006-01-10
after it crashes, does it dump you to a console? If so, then you could do it there, then startx again. little bit irritating to do every time you boot tho.

---

