---
title: "&quot;Graphic Card Does Not Work With Jaunty&quot;,,,,,,,,,, Why?"
date: 2009-04-18
forum: Desktop Environments
---

### Post by Naz_Farooq on 2009-04-18
Hi,
I have been using ubuntu 8.10 intrepid for last 4 months. There were some challenges that I have overcome after a hard effort and with the help of ubuntuforum.org well. Now I am trying to upgrade my 8.10 itrepid to Jaunty 9.04 Beta but it says that graphic drivers in jaunty will not support my visual card in laptop. I have IBM Thinkpad T43 (64MB ATI Mobility RADEON x300). This card is working very fine with intrepid 8.10 but I cannot resist my self for upgrading. I have anxiously waiting for 9.04 Jaunty.
Can anyone help me for this.
I would be appreciative for any help from my seniors.

---

### Post by Svensk023 on 2009-04-18
Are the free drivers not supported for your card or proprietary drivers?

I have ATI cards and usually they are the last thing to get taken care of because ATI/AMD wont let the linux community have rights to their drivers source code, so they take awhile to catch up. (that is just a clarification because many people tend to throw angry comments towards the Ubuntu teams and it's 100% out of their control)

---

### Post by Naz_Farooq on 2009-04-18
> **Svensk023 said:**
> Are the free drivers not supported for your card or proprietary drivers?

I have ATI cards and usually they are the last thing to get taken care of because ATI/AMD wont let the linux community have rights to their drivers source code, so they take awhile to catch up. (that is just a clarification because many people tend to throw angry comments towards the Ubuntu teams and it's 100% out of their control)

So what would be the best solution? Should we be working with intrepid? But it would be jealous for me if I do so.

---

### Post by Svensk023 on 2009-04-18
Just stay with Intrepid for now, a few weeks of patience will pay off, but a alternate solution is to look for the proprietary drivers independantly.

[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
just go there and look for you driver and download it.

to install follow these few steps.

after downloading you should just get a file that ends in .run an example is

ati-driver-installer-9.2-x86.x86_64.run

if not, then you need to extract it out of the folder you downloaded.

next you need to open up a terminal and put in

```
sudo sh [drag .run file here]
```

so an example would be

```
sudo sh run ati-driver-installer-9.2-x86.x86_64.run
```

click enter and enter your password and this should start the installation process. Be sure to choose "automatic" installation when given the choice between "automatic" and "manual"

-Good luck

---

### Post by babaum on 2009-04-24
I'm running a fresh Jaunty install on my thinkpad t43p (same ATI x300), used it as my workstation since yesterday non-stop, working flawlessly. The current ATI driver is not yet supported by Canonical, so it's not available for Jaunty yet. The new open ATI driver had some great performance improvements and you should consider using it if you don't need full 3d accel support (I'm using it now).

I'm against the installation of the ATI-provided drivers, since they overwrite system files without a warning, but I already used the method described by Svensk023 since Hardy and it *should* work. Be prepared, however, and backup your xorg.conf (the installer does it, but who knows). 

Also, according to the AMD/ATI driver site, the x300 chipset is now considered "legacy" and we are likely to face a lack of driver updates from now on. The current driver supports X 7.4 (included in Jaunty).

---

