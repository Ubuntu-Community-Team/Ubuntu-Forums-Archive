---
title: "Need Help Reinstalling BitPim"
date: 2009-05-28
forum: General Help
---

### Post by cforput on 2009-05-28
I installed BitPim in 7.04 and it worked but it could not detect my cell phone so I tried to delete it so I could reinstall. Don't ask me how I deleted it because it was a manual process I tried to use. Apparently I flubbed something up really bad because now when I try and reinstall BitPim, I get the following error. 

*********************************************
pops@pops-acer-laptop:~/Documents$ sudo dpkg --force-architecture -i bitpim_1.0.7.20081215_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 122114 files and directories currently installed.)
Preparing to replace bitpim 1.0.7.20081215 (using bitpim_1.0.7.20081215_i386.deb) ...
Unpacking replacement bitpim ...
Setting up bitpim (1.0.7.20081215) ...
cp: cannot stat `/usr/lib/BitPim-1.0.7.20081215/resources/60-bitpim.rules': No such file or directory
dpkg: error processing bitpim (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bitpim
pops@pops-acer-laptop:~/Documents$ 
**************************************************

Anyone have any ideas on how to fix my problem?

Thanks!
Pops

---

