---
title: "Dell Latitude D830 Intel 3945ABG wireless card not recognized"
date: 2007-12-29
forum: Dell  Ubuntu Support
---

### Post by o_caudron on 2007-12-29
Hi,

I have Kubuntu Gutsy on a Dell Latitude D830. I have been googling for weeks and can't find a way to have my wireless card recognized (0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)), short of rebuilding the kernel with the drivers from Intel, which I'd rather like to avoid.

I see some issues with that card on the forums but I haven't seen anyone for which the card did not install automatically.

I have a MAC80211 module loaded, but no ipw3945. If I try to load the module, it says:

FATAL: Module ipw3945 not found.
2007-12-29 13:13:46: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

I assume this is the cause of the issue. There doesn't seem to be anything for a 3945 card in all the upgrade sources accessible through adept?

FWIW, the wireless switch is on (although this should not prevent the card from being detected).

Any help would be highly appreciated!

Thanks

Olivier Caudron.

---

### Post by edgefree on 2007-12-29
Hi,

Please try to download & install from [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) or [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/).

Hope it would help.

Steven

---

### Post by Nicolae on 2007-12-29
That's odd, the ipw3945 module is available out-of-the-box, iirc, I've even got on my desktop and server. Try to load the module iwl3945 instead, that's a different driver that'll work as well.

---

### Post by o_caudron on 2007-12-29
Hi,

Nicolae: iwl3945 is not recognized either: 

sudo modprobe iwl3945
FATAL: Module iwl3945 not found.

And I can't find anything related to 3945 in apt even with all install sources selected...

edgefree: I have downloaded the ipw3945 install from Intel (both sites you mentioned seem to point on the same package), but I seem to be missing some kernel sources for the install:

sudo make SHELL=/bin/bash
Kernel Makefile not found at '/lib/modules/2.6.22-14-386/source'
make: *** [compatible/kversion] Error 1

It's strange, I think I had to build another module before on this system (though I don't remember which one, it may just be my imagination). Can you point me on the sources to install to get this running?

Thank you both for the advice!

Olivier.

---

### Post by tturrisi on 2007-12-29
```
apt-get install build-essential linux-headers-`uname -r` 
```

---

### Post by o_caudron on 2007-12-30
Seems the latest version of this is already installed:

sudo apt-get install build-essential linux-headers-`uname -r`

Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.22-14-386 is already the newest version.
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But it still doesn't work:

sudo make SHELL=/bin/bash
Kernel Makefile not found at '/lib/modules/2.6.22-14-386/source'
make: *** [compatible/kversion] Error 1

???

---

### Post by tturrisi on 2007-12-30
try:
apt-get install firmware-iwlwifi
and look here:
[http://ubuntuforums.org/search.php?searchid=33827754](http://ubuntuforums.org/search.php?searchid=33827754)

---

### Post by o_caudron on 2007-12-30
The package can't be found:

sudo apt-get install firmware-iwlwifi

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package firmware-iwlwifi

All the software source repositories are selected in my config.

The reference to the forum you provide doesn't seem to be recognized:

vBulletin Message
Sorry - no matches. Please try some different terms.

---

### Post by Nicolae on 2007-12-30
EDIT: Try this first:

```
sudo apt-get install linux-ubuntu-modules-2.6.22-14-386
```

If you still can't modprobe the iwl or ipw module, then try this:

```
sudo apt-get install linux-image-generic
``` 

then reboot and select that image from grub (you may have to hit Esc to get the grub menu, if you're not dual-booting). See if you can load the module then.

---

### Post by o_caudron on 2007-12-30
The first option worked immediately and like a charm! Many thanks!!! 
(used: sudo modprobe ipw3945)

Do you have any idea what may have gone wrong there? Did some parts of the module logic not install correctly during the first install?

In any case, you have my gratitude! ;-) 

Olivier.

---

### Post by o_caudron on 2007-12-30
Hm. :confused: I just rebooted my system, and while the wireless still works like a charm, the sound system doesn't work anymore. It is an Intel 82801H (ICH8 family), I had some trouble making it work at first, I had to replace ALSA by a newer version that I had to install manually. But since them it has worked all fine. I assume the module install that fixed the wireless issue also reinstalled the original version of ALSA and it conflicts with the newer one...

I'm having some difficulty making it work again, I think I need to uninstall the default ALSA for the new one to work correctly (dmesg shows a lot of "unknown symbol" errors related to the sound card and reloading the module generates an error). I'll try this and I'll confirm if it works on this thread or... start a new one if I can't make it work again ;-) I just hope fixing the sound will not break the wireless again :-/

---

### Post by Nicolae on 2007-12-30
Try this:

```
sudo apt-get install linux-backports-modules-2.6.22-14-386
```

---

### Post by tturrisi on 2007-12-31
> **o_caudron said:**
> Hm. :confused: I just rebooted my system, and while the wireless still works like a charm, the sound system doesn't work anymore. It is an Intel 82801H (ICH8 family), I had some trouble making it work at first, I had to replace ALSA by a newer version that I had to install manually. But since them it has worked all fine. I assume the module install that fixed the wireless issue also reinstalled the original version of ALSA and it conflicts with the newer one...

I'm having some difficulty making it work again, I think I need to uninstall the default ALSA for the new one to work correctly (dmesg shows a lot of "unknown symbol" errors related to the sound card and reloading the module generates an error). I'll try this and I'll confirm if it works on this thread or... start a new one if I can't make it work again ;-) I just hope fixing the sound will not break the wireless again :-/
re: ALSA & Audio Sigmatel (hda-intel)
See my Dell d830 guide here:
[http://members.cox.net/tonyt/d830](http://members.cox.net/tonyt/d830)

---

### Post by o_caudron on 2007-12-31
I have tried all this (with version 20071123 of ALSA, which worked previous to installing the wireless). All seems to work fine, but alsaconf can't be found:

alsaconf
bash: alsaconf: command not found

Where does this come from? I have all ALSA tools and utils installed as far as I can tell

---

### Post by o_caudron on 2007-12-31
After rebooting, I get this set of errors from dmesg:

dmesg | grep -i snd
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   15.324000] snd_hda_intel: Unknown symbol snd_ctl_add
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_new
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   15.324000] snd_hda_intel: Unknown symbol snd_card_register
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   15.324000] snd_hda_intel: Unknown symbol snd_card_free
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   15.324000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   15.324000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   15.324000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   15.324000] snd_hda_intel: Unknown symbol snd_component_add
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   15.324000] snd_hda_intel: Unknown symbol snd_card_new
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   15.324000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   15.324000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   15.324000] snd_hda_intel: Unknown symbol snd_device_new
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   15.324000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   15.324000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   15.324000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step

Before running through the manual install, I had no "disagreement" but only unknown symbols.

Any idea how to solve this?

---

### Post by o_caudron on 2007-12-31
Nicolae, Just to let you know I tried "sudo apt-get install linux-backports-modules-2.6.22-14-386", it didn't help.

---

### Post by Nicolae on 2007-12-31
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Try the solutions there. Method "G" seems to be the best bet, but that's what I just told you to do (ooops, I forgot to tell you to add that option to your /etc/modprobe.d/alsa-base, sorry-- read that page for more info)

The problem is that ALSA 1.0.14 (which is what gutsy has ) does not properly support the sound on this laptop, and upgrading to 1.0.15 _should_ fix that. 

You may want to try Method B from the wiki, but be sure to grab 1.0.15 final from [the official site](http://www.alsa-project.org/main/index.php/Main_Page) and not the rc1 linked to from the wiki.

---

### Post by o_caudron on 2008-01-01
I've done all this (methods B and G, using ALSA 1.0.15 final) but I still have those unresolved and/or conflicting symbols. I suppose some libraries should have to be cleaned up from my system before reinstalling ALSA, but I haven't found out how to do it. I have run "make uninstall" on the version "alsa-driver-hg20071123" I had installed previously, but it didn't seem to help much (deleted some directories). I have tried to uninstall ALSA from apt but either I did not select enough elements to uninstall and it didn't help, or I selected one too many and it suddenly decided to uninstall most of my system, probably because it detected that some (sound?) libraries required by most apps were missing (I had to restore a recent backup to get my system going again).

Is there a way to make sure to start clean with the install of ALSA?

Also, for the record, I noticed that the "family" of my sound card (ICH8 ) is not listed in the supported cards/chipsets of ALSA v1.0.15. ???

---

