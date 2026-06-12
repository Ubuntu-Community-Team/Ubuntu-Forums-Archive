---
title: "[SOLVED] Hardy Heron slow/ screen resolution refresh rate low"
date: 2008-08-23
forum: Desktop Environments
---

### Post by confused1 on 2008-08-23
help, I installed Hardy Heron and it is a lot slower than Gutsy and I can't adjust the refresh rate to 70-75Hz. It only gives me one choice 60Hz.
I have a 19" Iiyama CRT with a X-700 ATI graphics card.
I tried runnng the following command with the following result:
 
sudo aticonfig --initial --input=/etc/X11/xorg.conf
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
aticonfig: Parsing the configuration file failed.
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option
to generate a new configuration file.:confused:

---

### Post by confused1 on 2008-08-23
problem solved::popcorn:

I went to system>Administration>Hardware Drivers 
and installed ATI 3D drivers. working fine so far

---

