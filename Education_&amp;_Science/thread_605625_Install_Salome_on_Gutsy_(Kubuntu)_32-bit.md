---
title: "Install Salome on Gutsy (Kubuntu) 32-bit"
date: 2007-11-07
forum: Education &amp; Science
---

### Post by Jagermeister on 2007-11-07
For those interested, here's how:

I assume you've already downloaded the complete DebianSarge tarball from the salome-platform website (you have to register), it's a big mother at 534 MB; it's named 'InstallWizard_3.2.6_DebianSarge.tar.gz'

1) In a shell (console):
Unpack the tarball (somewhere in your home directory), run the install script (it's named 'runInstall') and follow the instructions. The script will prompt with a message about gcc, just say ok and continue. Also, install everything as binaries (note: gcc will be a 'native' install because of 'ok' above).

2) Once the install GUI has finished, and there's no errors, press the Launch button in the GUI (lower left corner) to check if it runs.

3) If (2) worked out for you, create an entry in your menu and link to the command '/some/where/salome_appli_3.2.6/runAppli'. For info: the 'salome_appli_3.2.6' directory lives next to the 'salome_3.2.6' directory.

4) If you want, add the following icon: /some/where/salome_3.2.6/GUI_3.2.6/share/salome/resources/gui/icon_default.png

5) Voila. Worked 'out of the box' even though I struggle to see points that I create in the geometry module. It may be my rubbish onboard graphics.

6) Tut's here: [www.caelinux.com](www.caelinux.com)

7) If you have time and are so inclined, create some tutorials and post them somewhere (perhaps at (6) above). It's OS, give something back...

I attach a screenshot showing the About window and a STEP model I imported from VariCAD.

Cheers,

Jagermeister
--
Microsoft: Binary opium for the masses.

---

### Post by Jagermeister on 2007-11-07
OK, it seems (well, I had to anyway) that one needs to change your /etc/hosts file, otherwise Salome doesn't launch. The install I did above was at work, so my hosts file there looks a little different, but here at home I had to change it as follows, yours will look similar:

127.0.0.1       name.local name

# Here I have another IP and name of a machine at home, removed it for this post

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

NOTE: 'name' above is your machine's name, so set it to the relevant name... localhost *might* work if that's your machine's name, but I didn't check.

---

### Post by touf on 2007-11-07
it worked perfectly for mine 7.10
Thanks a lots

---

### Post by yekbinglee on 2008-02-01
Hi, I have just tried to install Salome on Gutsy on my machine and did as Jagermeister suggested, ie gcc to click 'yes' and it will install as native application and to install the binaries and not the sources.  But in my log I get errors "python: error while loading shared libraries: libstdc++.so.5:cannot open shared object file: No such file or directory"   Should this not be solved by installing the GCC as native? or am I confused?  Or have I missed a step somewhere?

Hope someone can help :(

bing

---

### Post by in_flu_ence on 2008-02-03
Salome installs like a gem for me in all my computers that I owned. May need a slight tweak for 64bit though.

---

### Post by yekbinglee on 2008-02-11
Ok finally found out that I needed to install libstdc++5 package as well and it installs smoothly :) at last!

---

### Post by jmb365 on 2008-09-16
> **in_flu_ence said:**
> Salome installs like a gem for me in all my computers that I owned. May need a slight tweak for 64bit though.

Hi,

Could you please in detail what the tweaks are?  I am running into trouble trying to install Salome 3.2.6 in Hardy 64bit.

When I try to start Salome I get "Import error: No module named omniORB"

Thanks
JMB

---

### Post by in_flu_ence on 2008-09-18
Try this. Maybe...
[http://ubuntuforums.org/showthread.php?t=369959&highlight=salome](http://ubuntuforums.org/showthread.php?t=369959&highlight=salome)
[http://salome-platform.org/forum/?groupid=10&forumid=9&thread=1990](http://salome-platform.org/forum/?groupid=10&forumid=9&thread=1990)
[http://ubuntuforums.org/showthread.php?t=457031&highlight=salome](http://ubuntuforums.org/showthread.php?t=457031&highlight=salome)

I managed to make that work on Hardy some time ago but I have since then not using that too often so can't give you more help other than those post above.

You may also try google about omniORB which may give you more ideas.

Good Luck

---

