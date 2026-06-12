---
title: "How to remove some OS boot options in Grub?"
date: 2005-11-23
forum: Desktop Environments
---

### Post by Darrin on 2005-11-23
I recently had some ubuntu updates so i installed them. Im dual booting Ubuntu/Winxp. Now on the boot selector screen that shows up upon restart there are extra choices for ubuntu that werent there before. Looks like a different version of ubuntu. Do I really need all these? Is there a way to remove them and if so how do I do this safely as to make sure I dont remove the wrong information?
Thanks

---

### Post by DJ Ubuntu on 2005-11-23
Put #
```
#title		Ubuntu, kernel 2.6.12-9-386 
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.12-9-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.12-9-386
#boot
```
Save & exit.

---

### Post by atrus325 on 2005-11-23
[QUOTE=Darrin]Do I really need all these?[/QUOTE]

They are actually pretty useful.  I'd keep them.  I myself had to use the recovery mode last night when dealing with my nvidia+tv issue, and the memtest is a great program.  If ever your computer starts acting funny, run memtest and make sure your RAM is still alright.

Seriously, they're a great addition, and you shouldn't get rid of them.

But if you insist, adjust your menu.lst file under /boot/grub in the manner mentioned above.

J.

---

### Post by DeathOnJuice on 2005-11-23
WAIT!!! Don't do that just yet. I just installed that update, and he's not talking about recovery mode and memtest being the extra options. Now GRUB has the following:

Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)
Ubuntu, memtest 86+

Obviously, he doesn't want to take away Ubuntu, kernel 2.6.12-10-386 and recovery mode, as those are the newest versions. I am curious why this kernel update didn't erase the reference to the old kernel in GRUB, though, because all of the ones before have.

---

### Post by Darrin on 2005-11-23
Correct deathonjuice. I need to know if its safe to delete:
Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)

Since I now show the following as you do.
Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)
Ubuntu, memtest 86+

I wasnt at my ubuntu machine at the time so was unable to post the exact details.

---

### Post by aysiu on 2005-11-23
Don't delete them. Just comment them out (put a # in front of each line you don't want).

---

### Post by daveisadork on 2005-11-23
If you remove those kernel images with Synaptic, it'll remove the boot options as well.

---

### Post by DeathOnJuice on 2005-11-23
So, should I uninstall the old kernel images, or simply comment them out in GRUB?

---

### Post by Darrin on 2005-11-23
[QUOTE=aysiu]Don't delete them. Just comment them out (put a # in front of each line you don't want).[/QUOTE]
Just to verify so I dont totally mess anything up here.

I put the # sign in front of the lines that are below (## ## End Default Options ##) text?

Since I dont want the following. Do I edit it as follows?:

```
#title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

#title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot
```

---

### Post by DeathOnJuice on 2005-11-23
No, you would have to comment out every line in the entry, not just the title. Also, we're still not sure whether to do that or uninstall the old kernel.

---

### Post by aysiu on 2005-11-23
Unless it's a hard drive space issue, I don't see any need for uninstalling the other kernel.

---

### Post by Darrin on 2005-11-23
Thanks. Ill just comment them out then. My wife logs into windows a lot on this pc. She doesnt like having to down arrow those extra few steps to get to windows. (She has to have her AOL :p )

---

### Post by DJ Ubuntu on 2005-11-23
My menu.lst:
```
## ## End Default Options ##

splashimage=(hd1,0)/boot/grub/splash.xpm.gz

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

#title		Ubuntu, kernel 2.6.12-9-386 
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.12-9-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.12-9-386
#boot
```
Simply.;) Only boot with the last kernel.

---

### Post by NeoChaosX on 2005-11-23
The entries *are* removed if you remove the old kernel images. I've done this  myslef, and it's amazing how cleanly upgade-grub gets rid of the references to the old kernels.

---

### Post by aysiu on 2005-11-23
[QUOTE=Darrin]Thanks. Ill just comment them out then. My wife logs into windows a lot on this pc. She doesnt like having to down arrow those extra few steps to get to windows. (She has to have her AOL :p )[/QUOTE] How about just making Windows the default, then?

---

### Post by Darrin on 2005-11-23
[QUOTE=aysiu]How about just making Windows the default, then?[/QUOTE]
Wouldnt work. Because I log into ubuntu more. So I win ;)

---

### Post by tomwell on 2005-11-23
Hey Guys,

I have just posted a new thread :[http://www.ubuntuforums.org/showthread.php?t=94335](http://www.ubuntuforums.org/showthread.php?t=94335) that may have something to do with this one but am really not sure... its kind of a different problem but also includes this problem...

Peace

Tom

---

### Post by Hacker?pcs on 2007-10-11
Hallo. I'm new in Linux and I just want to know if there is way to remove Windows Vista from Grub Boot Options. I had triple boot XP - Vista - Ubuntu 7.04 and I understood Vista is s**t ( ;) )and formated the Vista Partition. And now I want to know if there is a way to remove ONLY VISTA from boot options.

---

