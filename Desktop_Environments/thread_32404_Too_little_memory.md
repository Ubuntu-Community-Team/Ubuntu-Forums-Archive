---
title: "Too little memory?"
date: 2005-05-07
forum: Desktop Environments
---

### Post by Joedl on 2005-05-07
Hi there

My problem is immediately told: Since I use Kubuntu 5.04, (didn't have this issue with previous Linux-Distris or Win), I seem to have too little memory. Actually I have to 512MB-Bars in my machine, but the command 'top' says there is only that much: 906660k total. Thats 885 MB, which 139 MB too little. Im sure it is not a hardware failure.

Any ideas? Same problem out there?

Thanks in advance, 
Joedl

EDIT: I just read an thread below mine, where someone has a very similar problem. But I do have a i686 Installation of Kubuntu.

---

### Post by rusi_pathan on 2005-05-07
[http://www.ubuntuforums.org/showthread.php?t=32402](http://www.ubuntuforums.org/showthread.php?t=32402)

---

### Post by Ironi on 2005-05-07
You need a kernel with highmem (or the [1G lowmem patch](http://ck.kolivas.org/patches/2.6/2.6.12-rc3/patches/1g_lowmem1_i386.diff)) enabled. I'm not sure which kernels available via apt-get have it enabled since I build my own.

---

### Post by jeremy on 2005-05-08
If you say what processor you use, we can tell you which kernel you need.

---

### Post by Joedl on 2005-05-08
Thanks for your replys. I'm using a Amd Athlon 64, but in 32 bit mode.

---

### Post by jeremy on 2005-05-08
[QUOTE=Joedl]Thanks for your replys. I'm using a Amd Athlon 64, but in 32 bit mode.[/QUOTE]
 Well, I am not sure in your case, but I would try linux-image-2.6.10-5-k7-smp . Keep your existing kernel in case you need to go back to it.

---

### Post by Joedl on 2005-05-09
Thanks for the reply, but I'm not going to install a new kernel. Too much driver issues after this... ;)

---

### Post by az on 2005-05-09
[QUOTE=Joedl]Thanks for the reply, but I'm not going to install a new kernel. Too much driver issues after this... ;)[/QUOTE]

The same drivers are built for all versions.  These are binary packages.  You do not have to recompile anything.  Just go into synaptic and install a different kernel-image.  You get the option to boot your old kernels (unless you remove them in synaptic).  It is 100 percent safe.

---

### Post by Joedl on 2005-05-09
Well, then it seems to be worth a try...:)But I have made bad experiences with new kernels so far.

---

