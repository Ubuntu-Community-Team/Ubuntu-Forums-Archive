---
title: "NVIDIA drivers installed, but nomodeset still necessary"
date: 2012-05-08
forum: Desktop Environments
---

### Post by Overv on 2012-05-08
Hi,

I just installed Ubuntu 12.04 LTS (64 bit) on my PC with the following specs:

NVIDIA GeForce 570 GTX
Intel Core i5 2500K @ 3.30 Ghz
8 GB DDR3 RAM @ 667 Mhz

I installed the latest NVIDIA drivers by downloading them from their official site, because the other drivers application didn't find anything. I installed them by booting to the root shell from recovery mode from the .run file.

I just tried out 'glxgears' and it's reporting an FPS over 5 seconds of about 17000, so it looks to me like the graphics card successfully installed itself. My display is 1920x1080 and it seems to have no trouble running at that resolution until...

I disable the `nomodeset` boot option. When I do that, Nouveau suddenly kicks in and reports i2c errors or I get a scrambled purple screen. What could be the cause of that?

---

### Post by bogan on 2012-05-08
Hi!, **overv,**

Have you blacklisted 'nouveau'?  In theory, running the NVIDIA....run file will do so, but not always successfully.

Was the version you downloaded 295.49 ? and was it the 32 or 64 bit version?? ```
cat /sys/module/nvidia/version
``` will confirm what is installed.

Running 12.04 LTS on a not very high spec machine, with a GT 7650 video card, GLXgears gives me 2,500 -6000 frames depending on how I log in. So yours is doing pretty well.

The need to use 'nomodset' is likely to be more controlled by the video card/Monitor combination than any single issue.

Chao!, **bogan**.

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html")

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

      	Code:
 	nvidia-installer --latest 
 now returns: v295.53 and the currently installed version, without altering anything.
     

      	Code:
 	nvidia-installer -f 
 will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

