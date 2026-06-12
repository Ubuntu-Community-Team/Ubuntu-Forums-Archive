---
title: "Kernel upgrade"
date: 2009-02-08
forum: General Help
---

### Post by MaindotC on 2009-02-08
If I follow [this link](http://www.howtoforge.com/kernel_compilation_ubuntu) or any other to install a new kernel, how would you anticipate it will affect operation of my desktop?  For example, if I enable the Ibex or Jaunty repos, then Update Manager will prompt me to download and install a bunch of packages.  I like my Hardy just the way it is but I want to put in a later kernel than the 2.6.24-22-generic that is currently installed.  Could I do this or would you forsee stuff breaking?

---

### Post by personjerry on 2009-02-08
why not upgrade to intrepid ibex?

---

### Post by igknighted on 2009-02-08
You could install the new kernel from jaunty or intrepid, and then change the repo's back.  If there are any security updates that come through for the new kernel you wont get them, but it should work.  You could also compile the latest kernel from source, this is a fairly easy and completely risk free procedure, so it can't hurt to try.

The real question is... why?  What do you hope to gain by trying a later kernel?

EDIT: They let you install Ubuntu on your thinkpads over there at morrisville?  I thought they locked those babies down 100%...

---

### Post by Sorivenul on 2009-02-09
Is there something particular you wish to gain from using a newer kernel? If not, there is nothing wrong with 2.6.24, and accepting the upgrades as they come from the main Ubuntu repositories is likely to cause less damage than manually compiling if you are unfamiliar with the process.

If you proceed, it is generally good practice to use the existing kernel configuration provided by Ubuntu, and is also good to keep a backup kernel that you know works. As always, be sure to backup your data.

EDIT:
As a note, Ubuntu has been the most "picky" system about custom kernels that I have used, which is probably just another "your mileage may vary" issue. Possibly helpful, nonetheless.

---

### Post by MaindotC on 2009-02-09
> **personjerry said:**
> why not upgrade to intrepid ibex?

I just don't have any reason to upgrade to Ibex or Jaunty.  I don't know if you want to get into this but the reason I want the new kernel is because I just got the [WiBee XS-2204S](http://www.amazon.com/Wireless-802-11g-Adapter-2-4ghz-Output/dp/B000ZK2V48) which uses the rtl8187 chipset which, [according to Realtek's website](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true) is fully supported by kernel 2.6 and above (or somewhere around that number).  I plugged it in and found via lsmod that the rtl8187 driver was being used, but still couldn't connect to the access point.  I did a google for getting it to install and work and have seen others running into problems like the [syslog filling up with unnecessary messages](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/261098) or [the NIC wouldn't connect and I didn't see any of the threads marked solved](http://www.google.com/search?q=rtl8187+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) and I got four of these WiBee's so I want to see if I can get them to work.

The launchpad url hinted at trying to use it under the Ibex kernel, so that's why I was wondering and again, I REALLY don't want to upgrade to Ibex or Jaunty - happy with things working.  My F5D7050 card listed in my sig only gets 24 mb/s and has trouble connecting to my AP if I put WPA2 on it.  For some reason it connected to the school's WPA2 when I lived on campus but right now we're running an open AP w/ MAC filtering until I get WPA2 working.

---

### Post by MaindotC on 2009-02-09
> **igknighted said:**
> 
EDIT: They let you install Ubuntu on your thinkpads over there at morrisville?  I thought they locked those babies down 100%...

The best they could do w/ the T60 is put a password on the BIOS and that is recoverable w/ a few wires & a 7-segment register.  Aside from that, I just use partimage to make a copy of the school's XP image (now it's Vista), put Ubuntu on the T60, and then put the XP image in a VM in case I need Outlook or some other proprietary garbage.  I've not re-imaged in over a year whereas XP users are re-imaging at least once every 3 months.

---

### Post by MaindotC on 2009-02-23
bump

---

### Post by dcstar on 2009-02-23
> **strAlan said:**
> I just don't have any reason to upgrade to Ibex or Jaunty.  I don't know if you want to get into this but the reason I want the new kernel is because I just got the [WiBee XS-2204S](http://www.amazon.com/Wireless-802-11g-Adapter-2-4ghz-Output/dp/B000ZK2V48) which uses the rtl8187 chipset which, [according to Realtek's website](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true) is fully supported by kernel 2.6 and above (or somewhere around that number).  I plugged it in and found via lsmod that the rtl8187 driver was being used, but still couldn't connect to the access point.  I did a google for getting it to install and work and have seen others running into problems like the [syslog filling up with unnecessary messages](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/261098) or [the NIC wouldn't connect and I didn't see any of the threads marked solved](http://www.google.com/search?q=rtl8187+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) and I got four of these WiBee's so I want to see if I can get them to work.

The launchpad url hinted at trying to use it under the Ibex kernel, so that's why I was wondering and again, I REALLY don't want to upgrade to Ibex or Jaunty - happy with things working.  My F5D7050 card listed in my sig only gets 24 mb/s and has trouble connecting to my AP if I put WPA2 on it.  For some reason it connected to the school's WPA2 when I lived on campus but right now we're running an open AP w/ MAC filtering until I get WPA2 working.

Look here:

[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

---

### Post by MaindotC on 2009-03-06
Thanks!  I don't see any packages, though - just lists of packages.  Same thing for source.

---

### Post by loomsen on 2009-03-11
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by MaindotC on 2009-03-11
THanks loomsen!  You're a better googler than I am.  Now hopefully I can get this wireless card working and it won't fill up my syslog with RxPower messages.

---

