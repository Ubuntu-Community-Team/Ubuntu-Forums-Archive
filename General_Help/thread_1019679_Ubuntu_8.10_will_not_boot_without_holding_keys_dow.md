---
title: "Ubuntu 8.10 will not boot without holding keys down!"
date: 2008-12-23
forum: General Help
---

### Post by jmmy73 on 2008-12-23
I have a HP Pavillion DV9715nr . I have loved using my ubuntu since hardy. I waited awhile to upgrade to Ibex . Well GOOD NEWS my 3g Modem now works!!
Unfortunately My Wifi does not, Also I have to push a key down while it is booting. I would like to have my System boot properly (before I ditch Windows Entirely!!!) and I have to have Wifi at my house. My 3G modem only allows 5 gig of service a month and this is Killing me. Please Send all answers or you can even PM me. i do not Mind. I am on my computers all day long..

---

### Post by wykedengel on 2008-12-23
I also have an HP (in my sig) and after I installed Ubuntu, both wireless and boot problems seemed to fix themselves. I cannot explain it (I did a clean install of Ubuntu 8.10). But it worked.

---

### Post by decoherence on 2008-12-23
> Also I have to push a key down while it is booting.

I have seen this behavior, I think... basically, it'll boot a bit and then just stop until you press a button? Hit a key and it'll go a bit further, and so on and so on?

I would love to hear if anyone else has seen that problem. It's really annoying and I've never found a solution.

---

### Post by richf on 2008-12-23
I have the same problem on an HP DV6704NR laptop since upgrading to 8.10. 
I used startup manager to display the text during boot, and my system hangs on:
Waiting for root file system.....

If I hold down a key, the progress bar moves and then boots ok. 
This didn't happen in 8.04

So far, I haven't figured out how to fix it. I also dual-boot with Vista and used WUBI to install 8.10.
______________________________________________________________

Also, sleep and hibernation never come back. 
______________________________________________________________

I did get the Atheros WIFI to work after installing the 
linux-backports-modules-intrepid-generic and
linux-backports-modules-intrepid in Synaptic package manager.
Also, placed in /etc/modprobe.d/blacklist, these 2 lines:
blacklist ath_hal
blacklist ath_pci

Works good now.
Hope this helps.

P.S. This is a bit much to do for the average home user. Vista does work "out of the box"; after 3-4 minute boot time.

---

### Post by jmmy73 on 2008-12-23
> **richf said:**
> I have the same problem on an HP DV6704NR laptop since upgrading to 8.10. 
I used startup manager to display the text during boot, and my system hangs on:
Waiting for root file system.....

If I hold down a key, the progress bar moves and then boots ok. 
This didn't happen in 8.04

So far, I haven't figured out how to fix it. I also dual-boot with Vista and used WUBI to install 8.10.
______________________________________________________________

Also, sleep and hibernation never come back. 
______________________________________________________________

I did get the Atheros WIFI to work after installing the 
linux-backports-modules-intrepid-generic and
linux-backports-modules-intrepid in Synaptic package manager.
Also, placed in /etc/modprobe.d/blacklist, these 2 lines:
blacklist ath_hal
blacklist ath_pci

Works good now.
Hope this helps.

P.S. This is a bit much to do for the average home user. Vista does work "out of the box"; after 3-4 minute boot time.

I installed the items you suggested in the Synaptic Manager.. How do I do the Blacklist? I am not Familiar with this.

Thanks

---

### Post by richf on 2008-12-23
Hit <Alt> <F2>

then type:

gedit /etc/modprobe.d/blacklist  and hit Run

add the lines at the end, and save

then prob have to reboot

---

### Post by jmmy73 on 2008-12-23
> **richf said:**
> Hit <Alt> <F2>

then type:

gedit /etc/modprobe.d/blacklist  and hit Run

add the lines at the end, and save

then prob have to reboot

Sorry Rich I did as you instructed nothing happened. I will continue to follow advice.

1. I would like Ubuntu 8.10 to boot without holding down keys
2. I would like my WiFi to Work.

Please othre people feel free to come in the Discussion.

---

### Post by jmmy73 on 2008-12-24
Lets Try to work on this together. I have performed alot of searches regarding this matter. Lets all work together and find a solution. Thanks in advance

---

### Post by richf on 2008-12-26
Jimmy,

Did you install the 2 intrepid backports modules in Synaptic Package manager?

---

### Post by jmmy73 on 2008-12-26
yes rich i did exactly as you requested.. is there some kind of scan or a utility i can run that might help you out?

---

### Post by richf on 2008-12-26
I'm not aware of any scan. I am basically a windoze person. I got the wifi working by searching these forums.

In System/Administration/Hardware drivers.... is Support for 5xxx series for Atheros 8022.11 wireless LAN cards active? If not, hit Activate.

Actually, I am running out of things to try.

---

### Post by dishmanw on 2009-01-16
Richf,
   Did you ever get your WIFI and boot problem fixed?  I have an HP dv6704nr laptop also.  I dual boot XP/Ubuntu 8.10.  I just upgraded from Ubuntu 8.04 yesterday, and I'm having the same issues.

Also if you are interested in downgrading from Vista to XP (I consider it an upgrade), the business support section on the HP website has some detailed instructions.

[http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1232134412089+28353475&threadId=1204621](http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1232134412089+28353475&threadId=1204621)


Dish

---

### Post by avtolle on 2009-01-16
Take a look at [http://ubuntuforums.org/showthread.php?t=1037264](http://ubuntuforums.org/showthread.php?t=1037264) for the booting problem.

---

### Post by SoCalChris on 2009-01-16
The booting problem is a known bug in the 2.6.27 kernel that Interpid uses. It's been fixed in the Jaunty alphas, but the fix has not been backported to Intrepid yet.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

Also, using "acpi=noirq" is not a good fix, it disables other services that you will want. I'd suggest just holding down a button to boot until the fix is backported. If you don't want to hold a button down, you can simply press the power button once, and it will boot normally.

---

### Post by 67GTA on 2009-04-30
This is caused by a broken DSDT file in newer HP laptop BIOS's. I can fix them. This will cure the boot, temp, and suspend/hibernate problems. Follow my how to here to the point of getting your dsdt.dsl file, and email it to me. [http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt)

---

