---
title: "how to compile chromium (browser)?"
date: 2009-03-17
forum: General Help
---

### Post by Meow27 on 2009-03-17
installing chromium on ubuntu seems to be impossible to me....

i got the source, but i dont even know where to configure.

can some1 lend me a hand please?
[http://code.google.com/p/chromium/wiki/LinuxBuildInstructions](http://code.google.com/p/chromium/wiki/LinuxBuildInstructions)

---

### Post by Apexnc on 2009-03-18
Hi Meow27 I was able to load Chromium-browser, however, like many others I only have a white (blank) space in the content.  Did you find the public key to import to Authorization in Software Sources? Here it is, you will need to copy it and save in a text file, then import the saved file to Authorization tab in Software Sources. Hope this helps.

mI0ESaSPtAEEAK1nJtoDZ0ewpOOf0ET6Vp28LqO9mB4ubWjzXyRSbiha5pCvnnSIU1K+7Gzb
t3r0iUV9eKLUmf8pqfF/9kwsoqFqFSCjp+XjUzXsEChcGBWvyfGdTX8ClFfwNxSVLvGSqmdX
gZhs0F8tQB0lPWHGy3VvEt7wG/VHqpcOYpdNYRqxABEBAAG0IExhdW5jaHBhZCBQUEEgZm9y
IGNocm9taXVtLWRhaWx5iLYEEwECACAFAkmkj7QCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIX
gAAKCRBam/O7Tl4XtV/2BACs/RTpEWB/NUlluJmp1e6iFoyyfbT+HOD3hg35aQMzbdcmijsA
iY9MvIfZ0YKWyqNUdGpDj5n0bUNO0IcvKBBkOn5o4CiBsMp4DJHdrgJU4S00nAJK00E8I/yA
v+x4C9uOacW3yrzSHs7Hv/vG6Z1Jh+1JrabK13hdhwOL8+aY6Q==
=3GDx

---

### Post by Meow27 on 2009-03-18
can you elaborate please?

---

### Post by markharding557 on 2009-03-18
i belive the windows version runs on wine.

---

### Post by Chops II on 2009-03-18
> **markharding557 said:**
> i belive the windows version runs on wine.

Can you or someone else possibly provide more information about this, i just downloaded the Chrome installer for windows and it didn't work in wine.

"Google Update installation failed with error 0x80070032"

Thanks,

Chops II

---

### Post by fieroboom on 2009-03-18
```
root@paul-desktop:~# wget http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb
--2009-03-18 22:31:19--  http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb
Resolving media.codeweavers.com... 66.114.51.109
Connecting to media.codeweavers.com|66.114.51.109|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35743970 (34M) [application/x-debian-package]
Saving to: `cxchromium_0.9.0-1_i386.deb'

100%[=================================================================================================================================================================>] 35,743,970   658K/s   in 47s

2009-03-18 22:32:07 (736 KB/s) - `cxchromium_0.9.0-1_i386.deb' saved [35743970/35743970]


root@paul-desktop:~# dpkg -i cxchromium_0.9.0-1_i386.deb
Selecting previously deselected package cxchromium.
(Reading database ... 122318 files and directories currently installed.)
Unpacking cxchromium (from cxchromium_0.9.0-1_i386.deb) ...
Setting up cxchromium (0.9.0-1) ...
cxbottle:warning: The current character encoding (UTF-8) may not be compatible with the encoding of the bottle (ISO-8859-1). This may cause applications to not find their files and thus lead to malfunctions.
```

[img]http://southeastfieros.com/chromium.jpg[/img]

It seems pretty featureless and a little buggy, but from what I've read, they're still working on it.
:D
-Paul

---

### Post by Meow27 on 2009-03-19
thanks for the link

but 
1) its extremely slow (its crossover so its not native )
2) the question was with compiling it. i wanted to test the browser out because i heard that it actually runs fast in linux

---

### Post by hikaricore on 2009-03-19
Why compile?

[http://www.downloadsquad.com/2009/03/17/google-chrome-on-linux-progressing-screenshots-inside/](http://www.downloadsquad.com/2009/03/17/google-chrome-on-linux-progressing-screenshots-inside/)

---

### Post by Meow27 on 2009-03-19
THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU {gasp} THANK YOU THANK YOU THANK YOU vTHANK YOU





in other news, im am really surprised. chromium works amazingly fast compared to firefart. if people port firefox addons to work with chromium. im switching for good. 

thanks guys

thanks  hikaricore

---

