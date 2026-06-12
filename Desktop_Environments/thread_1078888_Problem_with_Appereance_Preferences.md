---
title: "Problem with Appereance Preferences"
date: 2009-02-23
forum: Desktop Environments
---

### Post by zgembo on 2009-02-23
When I go to System-> Preferences->Appearance and then to tab Visual Effects everything is grey and I can not change it. The one which is marked is "None".
How can I fix it?

---

### Post by mikewhatever on 2009-02-23
What's your graphics card?
sudo lshw -C display

---

### Post by zgembo on 2009-02-24
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by mikewhatever on 2009-02-26
You may need to edit your /etc/X11/xorg.conf according to the thread below.
[http://ubuntuforums.org/showthread.php?t=378060](http://ubuntuforums.org/showthread.php?t=378060)

---

### Post by zgembo on 2009-02-26
Thank you, I'll try.

---

