---
title: "Compiling kernel gave at end: &quot;Please manually create an initrd image&quot;"
date: 2009-02-09
forum: General Help
---

### Post by tarekeldeeb on 2009-02-09
Hello all,

I have ubuntu 8.10 on AMD64, and an unsupported dvb-s card, and a patch for the card against 2.6.27.10.

I downloaded the kernel >> applied patch >> configure >> compile.
I followed the official documentation [here]("https://help.ubuntu.com/community/Kernel/Compile")

finally, the deb packages are created ..

* linux-xenu-2.6.27.10_2.6.27.10-10.00.Custom_amd64.deb
* linux-headers-2.6.27.10_2.6.27.10-10.00.Custom_amd64.deb

I installed the "linux-xenu".. succeeded but it gave me:
"Please manually create an initrd image"

then I installed the "linux-headers" .. successfully.


Nothing was changed in my grub menulst, and of course , no initrd was created.

I googled but knew that I need: mkinitrd, which is not found through apt-get ..

Does any1 have a clue?

Thanks in advance,
Tarek

---

### Post by raptor2552 on 2009-02-09
I did find this by searching for initrd.img that may be of some use [http://kerneltrap.org/node/7019](http://kerneltrap.org/node/7019)

I haven't done anything like this since I gave up on Mandrake... a long, long time ago. Beyond this I cannot offer any more help.

---

### Post by tarekeldeeb on 2009-02-10
> **raptor2552 said:**
> I did find this by searching for initrd.img that may be of some use [http://kerneltrap.org/node/7019](http://kerneltrap.org/node/7019)

I haven't done anything like this since I gave up on Mandrake... a long, long time ago. Beyond this I cannot offer any more help.

thanks ... I shall try [this ]("http://kerneltrap.org/node/7019#comment-198782")one, instead of mkinitrd

---

### Post by tarekeldeeb on 2009-02-13
No, this did not do the trick !

---

### Post by sdennie on 2009-02-13
Try:

```

sudo mkinitramfs -c whatever-you-called-the-kernel

```

For example:

```

sudo mkinitramfs -c 2.6.27.10-custom

```

---

### Post by elliottb on 2009-06-02
Did this get solved?  I have exactly the same problem.  As I understand make-kpkg should make a binary that contains the initrd image, but mine doesn't seem to be doing this.   I far as know, I've gone through all the kernel building steps carefully, but I'm stuck here as well. 

Any advice on how this got solved would be awesome.

Thanks,

Elliott

---

### Post by realflash on 2009-12-01
In fact you also need the -o option to specify where you want to write the initrd image to. So:

```

sudo mkinitramfs -o /boot/initrd.img-2.6.27.10-custom -c 2.6.27.10-custom

```

You will also need to create a boot menu entry for it. Open */boot/grub/menu.lst* and head to the bottom. You can use one of the existing entries as a template. If you make it the first entry immediately after **## ## End Default Options ##** then it will get booted automatically. If you make a typo while creating the entry you will see

```

Error 15: File not found

```

When the machine boots.

---

### Post by cofficavic on 2009-12-01
Get problem solved yet?

Please update. Have quite the same problem.

---

