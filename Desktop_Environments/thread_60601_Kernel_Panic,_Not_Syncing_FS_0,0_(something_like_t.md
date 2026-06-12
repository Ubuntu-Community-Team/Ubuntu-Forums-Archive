---
title: "Kernel Panic, Not Syncing FS 0,0 (something like that)"
date: 2005-08-28
forum: Desktop Environments
---

### Post by jlacroix on 2005-08-28
I recompiled the kernel using this guide:
[http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation)

After installing the deb file it creates, I get an error message during boot, saying something like "kernel panic not syncing VFS 0,0"  note that is not exactly what it says but is as much of the error as I can remember. It says this right after "uncompressing linux".

The kernel source is 2.6.12.5 from kernel.org. I've tried adding the initrd option, and I also (the second time I compiled it) made the ext3 file system Y in make xconfig. Those are the only two tips I could find.

I really wanted to do this but has anyone ever recompiled a kernel in Ubuntu? I'm starting to doubt if its even possible, as I have recompiled the kernel in several other distro's with less work and no problems.

PLEASE help :( :( :(

---

### Post by tseliot on 2005-08-28
Try my guide

[http://www.ubuntuforums.org/showthread.php?p=301048](http://www.ubuntuforums.org/showthread.php?p=301048)

Please follow every step.

---

### Post by jlacroix on 2005-08-28
I followed your guide perfectly, and the kernel is compiling in a terminal window right now. Will probably take a few hours. Pray for me.

---

### Post by jlacroix on 2005-08-28
All done. Same problem. I think Ubuntu is recompile-proof. As I said, I can recompile the kernel in any other distro no problem, but since Ubuntu remains my favorite distro I guess I have to deal with an out of date kernel.

---

### Post by tseliot on 2005-08-28
Are you sure the command you used for compiling was similar to this one?

sudo make-kpkg [COLOR=Red]--initrd[/COLOR] --append-to-version=-custom kernel_image kernel_headers

If you dint put --initrd it will give you a kernel panic

---

### Post by jlacroix on 2005-08-28
The first time I didn't use that command. Every subsequent time I did use that command, but I get a message saying that it won't do it or something, but the initrd image does exist and grub does point to it.

I'm starting over from scratch with your walkthrough. This time with 2.6.12.4. In fact, it's compiling right now, so I guess we'll see how it goes.

I'm wondering if 2.6.12.5 is just garbage or something.

---

### Post by jlacroix on 2005-08-28
Same problem, again. I did everything right this time, I know I did.

I don't know if this means anything but I noticed this output after compiling:

```
Setting up kernel-image-2.6.12.4-omega (10.00.Custom) ...
/initrd.img does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
/vmlinuz does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12.4-omega
Found kernel: /boot/vmlinuz-2.6.10-5-k7
Found kernel: /boot/vmlinuz-2.6.10-5-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

---

### Post by tseliot on 2005-08-29
I've never seen such an output:

/initrd.img does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
/vmlinuz does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.

Perhaps it's because I use Ubuntu Hoary instead of Warty. I really don't know. You can try asking in the thread of the first HOWTO you followed (luca_linux's). I fear this problem goes beyond my knowledge.

Maybe people like luca_linux, Skoal etc. can help you.

---

### Post by jlacroix on 2005-08-29
I don't know what to say either. Google is usually the most helpful thing in the world but it proves useless for this problem.

There should be a document with the true definition of this error message...

---

### Post by jlacroix on 2005-08-29
I might have found what I was looking for. Even though I did make oldconfig and followed the guide exactly, initrd support and ramdisk support were both turned off!! It may be a good idea to put that in your guide, to make sure its there.

The kernel is compiling now, I'll just let it run, and install it in the morning. I'm off to bed.

---

### Post by tseliot on 2005-08-29
Ok, thanks I'll add it to the guide. Perhaps in Warty they are not enabled by default (but in Hoary they are enabled).

---

### Post by jlacroix on 2005-08-29
FIXED!

The kernel now works, so that was definitely the problem. I am using Hoary, so as to why it wasn't enabled by default I have no idea.

Even though the kernel boots, I am getting a ton of error messages. The don't seem to effect anything though. Is there a way to post the boot messages, like a log file or something? Dmesg doesn't show it.

---

### Post by tseliot on 2005-08-29
Did you use vanilla kernel sources (from kernel.org)?

If yes, it's a normal thing: it has happened to me too (and the system worked fine)

---

### Post by jlacroix on 2005-08-29
Yeah, I always create custom vanilla kernels. Those types of kernels are what I was trained on in my Linux class, so recompiling the existing Ubuntu kernels is something I'm not comfortable with.

Anyway, Ironically enough 2.6.13 came out today so I compiled that one just now. It has a ton of error messages when booting up, although everything runs as it should when its running and it works very well, but those error messages I'd like to kill nonetheless.

When you are booting up, you see a list of things its starting, and shows [OK] when a service is started. It tries to start some services and fails. What log should I look at to post those errors here? That will be my last question for this thread and I really appreciate you, everything is working fine now save for those error messages that probably don't effect anything anyway, they're just eyesores.

---

