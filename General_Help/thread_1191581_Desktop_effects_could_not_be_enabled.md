---
title: "Desktop effects could not be enabled"
date: 2009-06-19
forum: General Help
---

### Post by jsprz8382 on 2009-06-19
Whenever I try to enable visual effects I get an error.
I click normal or extra it says it is checking for drivers and it finishes and then a message comes up saying that "Desktop effects could not be enabled" thank you in advance.

---

### Post by jsprz8382 on 2009-06-19
bump
here is my graphics card info.
 Intel Corporation 82865G Integrated Graphics Controller

---

### Post by mikewhatever on 2009-06-19
Wow, bumping after 12 minutes, that's not cool.

Go to System->Admin->Hardware Drivers and enable the 3d capable driver if available.

---

### Post by jsprz8382 on 2009-06-19
it says that no proprietary drivers are in use on this system.

---

### Post by mikewhatever on 2009-06-19
If that's the case, and none are available, the system thinks your hardware is not capable of running 3d effects. Do you know your graphics card specs? If not, post the output of the following command from Applications->Accessories->Terminal: **sudo lshw -C display**.

---

### Post by jsprz8382 on 2009-06-19
This is what I get

*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0

---

### Post by raymondh on 2009-06-19
Maybe this can help, or offer more clues.

see this thread starting at post #3

[http://ubuntuforums.org/showthread.php?t=1139346](http://ubuntuforums.org/showthread.php?t=1139346)

If that does not work, you have the option of reverting your driver.  See, same thread, post 8.

Back up files whenever before editing anything.  That way, if X collapses on you, you can reconsider install options knowing you have your files safe someplace.

Good luck.

---

### Post by jsprz8382 on 2009-06-19
thanks for the help I did try some of the steps that raymond linked me to and I no longer get the error but still no luck I will keep trying.

---

### Post by raymondh on 2009-06-19
> **jsprz8382 said:**
> thanks for the help I did try some of the steps that raymond linked me to and I no longer get the error but still no luck I will keep trying.

I would consider running compiz check

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

It may give you alternatives ... or at the very least, an  added understanding of why you could not enable desktop effects.

Good luck.

---

### Post by kendrick on 2009-06-19
Reverting your intel driver to version 2.4 will get compiz working again. I have the same chip as you and this worked for me. I suggest restarting after installing the package instead of restarting X because X didn't restart for me.
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

