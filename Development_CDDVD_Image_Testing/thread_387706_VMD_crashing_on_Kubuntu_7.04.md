---
title: "VMD crashing on Kubuntu 7.04"
date: 2007-03-18
forum: Development CD/DVD Image Testing
---

### Post by pachequin on 2007-03-18
Hi everyone I'm testing Feisty (i made the upgrade from Edgy). I usuall work with molecular modelling software. VMD is one of this programs, when I made the upgrade I can't make it run, when it begins everything looks normal but when I close it all the machine freezes but until last Friday It crash and send me to the kdm initial page. After The last update of xorg, my computer freezes completly and I have to do a hard reboot. Does any one have any trouble like this? I'm using a toshiba A75-S209 with a ATI Radeon card 9000 using the ati driver from Xorg.

When I checked the Xorg.0.log nothing looks bad.

Any help will be appreciate.

Thank you.

Best regards

---

### Post by sayash on 2007-04-28
Could you point me to any site with instructions for installing VMD on ubuntu?

---

### Post by pachequin on 2007-04-28
Hi! I just do the following:

$> tar xvjz vmd-1.8.6.bin.LINUX.opengl.tar.gz
$> cd vmd-1.8.6/
$> ./configure            <- you can change the path, in case you want to install it at your home
$> cd src
$> make install 

Note: If you want to install it for everyone, you have to install it using sudo

The installation procedure is the same (I think) for every unix system.

Here is the vmd web page: 
[http://www.ks.uiuc.edu/Research/vmd/](http://www.ks.uiuc.edu/Research/vmd/)

Best Regards.

Final note: On the last Feisty upgrade, VMD runs perfectly.

---

### Post by omega_point on 2007-05-04
Hi. May be a bit off-topic, but this is my first post and well...
I have downloaded VMD, I installed it with checkinstall and everything went perfect, But when I try to run it, it looks like it starts up but quits immediately. I've been using kubuntu for a week or two, so, a detailed explanation would be welcome.

---

### Post by pachequin on 2007-05-04
I remember on some place that you must check first if you had an xterm installed, If this didn't help you check the vmd-user list for help on the same link that I post earlier

best regards.

---

### Post by ercxy on 2007-05-10
I had similar problem and found a solution.
I installed csh,tcl8.4,tcl8-3 and then checked that glxinfo does not show any error.
typed in a terminal:
vmd -dispdev text 

In my case it complained:
/usr/local/lib/vmd/vmd_LINUX: error while loading shared libraries: libstdc++.so                                      .5: cannot open shared object file: No such file or directory

libstdc5++ was not installed, so I installed it .
then fired up vmd . It worked.
It looks like vmd is compiled with gccc3.3 and requires listdc++5.

---

### Post by srs on 2007-06-05
Hi
I have noticed that if desktop effects are enabled, VMD won't start properly. When I turned off desktop effects (ubuntu 7.04), VMD worked well. Alternatively, you can start it by setting the display size explicitly, e.g.
```
vmd -size 600 600
```
Best wishes,
SRS

---

