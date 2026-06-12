---
title: "Eagle blank registration windows in Kubuntu Intrepid 8.10"
date: 2008-12-07
forum: General Help
---

### Post by paulhurleyuk on 2008-12-07
Hello,

I recently moved up, and got a laptop and installed Kubuntu Intrepid Ibex (8.10) on it.  Today I tried to install eagle from the repo's.

This popper up a registration window (titled EAGLE Product Registration, unfortunatley, the window is blank, and semi transparant.

Is this a Kubuntu issue, a QT-4 Issue or what ?/

Anyone else succesfully using Eagle on Kubuntu 8.10 ?

Here's the output from apt-get install eagle

> paul@b2buntu:~$ sudo apt-get install --reinstall eagle             
Reading package lists... Done                                      
Building dependency tree                                           
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libasound2-plugins
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/2894kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 169041 files and directories currently installed.)
Preparing to replace eagle 4.16r2-1 (using .../eagle_4.16r2-1_i386.deb) ...
Unpacking replacement eagle ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for man-db ...
Processing triggers for menu ...
Setting up eagle (4.16r2-1) ...


Thanks

Paul.

---

### Post by paulhurleyuk on 2008-12-09
:KS Solved it (kinda)

[Bug 222790]("https://bugs.launchpad.net/ubuntu/+source/eagle/+bug/222790")

Exporting this first worked;

> export XLIB_SKIP_ARGB_VISUALS=1
eagle

although, I had to jump through a few hoops to get a) it to work, b) let it write it's license file where only root will do and c) not write my home direcotry as root
> 
su konsole
export XLIB_SKIP_ARGB_VISUALS=1
eagle
#let it write it's license
rm eagle -r
rm .eaglerc
#remove the config files / dir (as they're owned root)
exit

export XLIB_SKIP_ARGB_VISUALS=1
eagle
#let it write the config files again !

---

### Post by kwacka on 2009-03-28
Sadly this didn't work for me, so I went to the Cadsoft page and downloaded version 5.4 (cf. v4.6 in the repository) - no problem installing locally from a .run file, no display problems.

---

