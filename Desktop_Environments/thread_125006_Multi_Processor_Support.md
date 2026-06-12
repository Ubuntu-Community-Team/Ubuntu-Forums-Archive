---
title: "Multi Processor Support"
date: 2006-02-02
forum: Desktop Environments
---

### Post by finalzero on 2006-02-02
Hi,

I am new to Ubuntu and so far impressed with the quality of the product, a grown up version of Debian (formally a Debian 3.1 fan).

I have noticed the installer does not cater for multi processor support and neither does the update process (which only found the lates i386 kernel, not i686-smp as I expected).

Do I have to manually download the SMP kernel and related headers + source or is there a way of configuring Ununtu so that it will recognise the additional processor and download the relevant updates?

Thanks,

Fz

---

### Post by Leif on 2006-02-02
sudo apt-get install linux-686-smp (may be without the hyphens, so search synaptic for linux)

---

### Post by finalzero on 2006-02-02
Hi,

Thanks for the info, I have had success with the kernel.  I wasn't sure how much Debian was still left in Ubuntu ;) 

I don't like gui's so I just fired up a terminal session:

log out
Press: Ctrl+Alt+F1  to switch to the console window
Log in with your normal account

Then I did the following:
```

sudo apt-get update
sudo apt-cache search linux-kernel-2.6.12

```
This brought back a list of linux images, I found the one I wanted and then downloaded the package, headers and source:
```

sudo apt-get install linux-image-2.6.12-10-686-smp
sudo apt-get install linux-headers-2.6.12-10-686-smp
sudo apt-get install linux-source-2.6.12

```
After that lot finished I rebooted and hey presto, I have dual proc's (four if you count the two virtual processors as well) so I am a happy man.

Now I just need to get the nVidia Installer working and I am all set for dual screen heaven.

Adios,

Fz

---

### Post by RAOF on 2006-02-02
You really want to install one of the linux-foo metapackages.  In your case, linux-686-smp.  That will always depend upon the latest 686-smp kernel image (so updates will happen) and the corresponding -restricted-modules package (important if you want to use the nvida-glx pagage).

---

