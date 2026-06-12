---
title: "Wireless in XPS M1530 (need to use 'noapic' kernel boot param)"
date: 2008-02-10
forum: Dell  Ubuntu Support
---

### Post by ricpelo on 2008-02-10
Hi:

I recently bought a Dell XPS M1530 (with preinstalled Vista). This
laptop has a Intel(R) PRO/Wireless 3945 mini card.

I installed Ubuntu 7.10 on it, but the wireless card didn't work.
Executing the command:

dmesg | grep -i 3945

I'd got the following messages:

ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux,
1.2.2mp.ubuntu1
ipw3945: Copyright(c) 2003-2006 Intel Corporation
ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
ipw3945: MAC is in deep sleep!
ipw3945: Unable to int nic

The only way to get wireless card working on Ubuntu is to add the
'noapic' parameter to the kernel during boot (changing
the /boot/grub/menu.lst file).

It seems, therefore, that the laptop has a buggy APIC implementation, so
I think Dell must release a BIOS upgrade to solve this problem.

For reference, my BIOS version is A06.

Has anybody any other workaround to this problem?

Thanks in advance,

Ricardo.

---

### Post by gnelson on 2008-02-10
Don't feel like this is an oddity.  HP laptops are notorious for this.  Mine won't even boot without changing the APIC boot options.

---

### Post by the_sorrow on 2008-02-10
Did you guys try to use a program call ndiswrapper? it does everything for you.

---

### Post by inyoka on 2008-02-11
FYI, this is an old post and Wireless in the current M1530 with Gutsy works without any problems.  Infact the only thing that I havn't got working is the finger-print reader, and there seems to be trouble reading some memory cards such as XD but SD and MMC works fine.  

More information can be found at [http://linux.dell.com/](http://linux.dell.com/) and [http://www.dellcommunity.com/supportforums/](http://www.dellcommunity.com/supportforums/) or [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330?highlight=(m1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330?highlight=(m1330))

---

### Post by ricpelo on 2008-02-11
> **inyoka said:**
> FYI, this is an old post and Wireless in the current M1530 with Gutsy works without any problems.  Infact the only thing that I havn't got working is the finger-print reader, and there seems to be trouble reading some memory cards such as XD but SD and MMC works fine.  

More information can be found at [http://linux.dell.com/](http://linux.dell.com/) and [http://www.dellcommunity.com/supportforums/](http://www.dellcommunity.com/supportforums/) or [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330?highlight=(m1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330?highlight=(m1330))

My M1530 is a NEW one. I bought it last week and I received it last wednesday (5 days ago). I'm not the only one with the same problem. See, for example:

[http://www.galmarino.com/wordpress/?p=31](http://www.galmarino.com/wordpress/?p=31)

I've posted the issue in dellcommunity.com and launchpad, but without luck for now...

---

### Post by jdelaros1 on 2008-02-11
Try using the driver iwl3945 instead.  Here are the instructions on how to do it:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

I'm running Hardy alpha 4 with latest updates and wireless works just fine, but it is using the iwl3945 (which Hardy uses by default):

[   23.615798] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   23.615802] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   23.766295] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   25.289112] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   25.302604] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

---

### Post by ricpelo on 2008-02-11
> **jdelaros1 said:**
> Try using the driver iwl3945 instead.  Here are the instructions on how to do it:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

I'm running Hardy alpha 4 with latest updates and wireless works just fine, but it is using the iwl3945 (which Hardy uses by default):

[   23.615798] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   23.615802] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   23.766295] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   25.289112] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   25.302604] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

Thanks for the advice. I already tried it, but without luck. The iwl3945 module don't load when you don't use the 'noapic' at boot.

---

### Post by thomasbechtold on 2008-02-12
Hi,

I have the same problem with the same laptop-model. Can you tell me if you find a workaround?
Have you send a Mail to dell?

---

### Post by 91004 on 2008-02-12
In reference to the wireless problems:

I have found that the following website works for most Dell Laptops, not just the Dell 1501

[http://www.ubuntu1501.com](http://www.ubuntu1501.com)

Check it out I believe it will solve almost all of your problems with your laptop!!!

---

