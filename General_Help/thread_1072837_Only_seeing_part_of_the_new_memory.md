---
title: "Only seeing part of the new memory"
date: 2009-02-17
forum: General Help
---

### Post by triplenine on 2009-02-17
So I just dropped a 2GB stick into my Dell Mini 9. I can only see ~888MB of RAM. Do I need to do something to get it to see the whole thing or is there a way for me to diagnose a hardware problem?

---

### Post by handy on 2009-02-17
If your Ubuntu install disk doesn't have the menu option when booting the liveCD, to run Memtest, then you should go here & download a bootable memtest .iso & thoroughly test you new RAM:

*_[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)_*

---

### Post by Kain000 on 2009-02-18
> **triplenine said:**
> So I just dropped a 2GB stick into my Dell Mini 9. I can only see ~888MB of RAM. Do I need to do something to get it to see the whole thing or is there a way for me to diagnose a hardware problem?

If memtest says that your memory is a-ok then you might look up your dell's motherboard stats

specifically the memory controller and the max amount of RAM it can handle

---

### Post by CKDewey on 2009-02-18
I had a similar problem with an Optiplex 745 at work and a BIOS update fixed the problem. That box runs Vista but it could indicate Dell has frequent issues of this type...

BTW the only way to update the Dell BIOS is via Windows, AFAIK.

--
Tom

---

### Post by sdennie on 2009-02-18
What is the output of:

```

grep HIGHMEM /boot/config-`uname -r`

```

It could be that your kernel isn't setup to address more than 1G of RAM.

---

### Post by triplenine on 2009-02-18
The output for the himem is
CONFIG_NOHIGHMEM=y
# CONFIG_HIGHMEM4G is not set
# CONFIG_HIGHMEM64G is not set

---

### Post by triplenine on 2009-02-18
OK so... From what I interpret from the CONFIG... there may be a setting that I am missing or my kernel version doesn't support more than a gig of memory. Where to next? Kernel update or configuration/setting change?

---

### Post by dcstar on 2009-02-19
> **triplenine said:**
> OK so... From what I interpret from the CONFIG... there may be a setting that I am missing or my kernel version doesn't support more than a gig of memory. Where to next? Kernel update or configuration/setting change?

All repository 32 bit kernels support up to 3.5GB, all 64 bit kernels support far more.

Unless you have installed some dodgy custom kernel then that is **not** your problem.

---

### Post by handy on 2009-02-19
Have you tried swapping the memory with one of your other machines?

***[Edit:]** Oops, I just realised that I'm mixing you up with another person on the forum.  Sorry. :-)*

---

### Post by sdennie on 2009-02-19
> **dcstar said:**
> All repository 32 bit kernels support up to 3.5GB, all 64 bit kernels support far more.

Unless you have installed some dodgy custom kernel then that is **not** your problem.

That **is** the problem actually.  I think Dell ships it's Mini 9 with a kernel that has no high mem support.  If you look at the output, it's obviously the problem.  There has been discussion of this on the Dell subforum but I haven't followed it closely.

@triplenine:

What is the output of:

```

uname -a

```

---

### Post by handy on 2009-02-19
> **sdennie said:**
> That **is** the problem actually.  I think Dell ships it's Mini 9 with a kernel that has no high mem support.  If you look at the output, it's obviously the problem.  There has been discussion of this on the Dell subforum but I haven't followed it closely. 

So I was interpreting post_6 right then?

---

### Post by triplenine on 2009-02-19
> **sdennie said:**
> 
@triplenine:

What is the output of:

```

uname -a

```

it is:

```

Linux chris 2.6.24-19-lpia #1 SMP Tue Jul 29 14:02:05 UTC 2008 i686 GNU/Linux

```

---

### Post by triplenine on 2009-02-19
OK, I found this: 
[Dell memory bug at launchpad.net]("https://bugs.launchpad.net/ubuntu/+bug/286258")

I am still a bit confused since the last entry in that post shows the same version that I have yet it is showing the full 2gb. Grr. So should I figure out how to update the kernel or can one modify the HIGHMEM entries individually?

Just as an update as well I am showing 883MB instead of the 888 that I stated earlier.

---

### Post by CKDewey on 2009-02-20
You might want to try to update the kernel anyway; as so:

Open terminal and type the following commands:
```
$ sudo apt-get update
```Now search kernel version:
```
$ apt-cache search kernel-image
```Now install kernel by explicitly specifying version number:
```
$ sudo apt-get install linux-image-2.6.xx-yy-lpia
```Adpated from: [http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/](http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/)

---

