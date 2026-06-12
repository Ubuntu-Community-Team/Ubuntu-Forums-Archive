---
title: "Kernels on Bootloader"
date: 2009-01-03
forum: General Help
---

### Post by yanom on 2009-01-03
Ok, my bootloader menu looks like this:



Ubuntu, kernel something-11
Ubuntu, kernel something-11 recovery
Ubuntu, kernel something-9
Ubuntu, kernel something-9 recovery
Ubuntu, kernel something-7
Ubuntu, kernel something-7 recovery
Other:
Windows Vista




And I want it to look like this:

Ubuntu, kernel something-11
Ubuntu, kernel something-11 recovery
Other:
Windows Vista



I saw on the Startup manager that there was an option "Limit the number of kernels to keep".

If I set this to 1, will it delete all the other kernels?
If I want it to keep kernel something-11 and something-11-recovery, do I have to set it to 2?

---

### Post by drs305 on 2009-01-03
Install and use StartUp-Manager. It's a gui app that will let you set how many kernels you see, how long you see them, which one to run and lots more, all without having to manually edit grub's menu list.

Here is a tutorial on how to install and use it:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Specifically - SUM hides the number you see but doesn't physically remove them from your system. Each kernel *version* counts as one, so don't include the recovery mode when deciding how many to keep.

---

### Post by unutbu on 2009-01-03
Setting "Limit the number of kernels to keep" to 1 will keep all boot options related to 1 kernel -- both the normal boot option and the recovery mode.

Edit: Oops, too slow...

---

### Post by yanom on 2009-01-04
Ok, Thanks

---

### Post by oldos2er on 2009-01-04
You can use Synaptic to uninstall kernels that are no longer needed. Doing so will update your grub menu.lst.

---

### Post by arepaking on 2009-01-28
> **oldos2er said:**
> You can use Synaptic to uninstall kernels that are no longer needed. Doing so will update your grub menu.lst.

How can we find the kernel to uninstall inside the Synaptic Manager?

---

### Post by drs305 on 2009-01-28
Note the kernel you are currently using:
```

uname -r

```
for instance: 2.6.27-9-generic

Open synaptic. 
Search for "linux-image"
You will see a variety of listing. In addition to "linux-image", you will see listings such as "linux-image-2.6.27-9-generic"
You can delete the ones of a lower number than the one you are using (such as linux-image-2.6.27-6-generic). Many people keep at least one older kernel on their system as a backup.
To delete the older kernels, right click, and select "Mark for complete removal", then "Apply".
You can also remove the associated "linux-headers..."
The removed kernels will also be automatically removed from grub's boot menu.

---

### Post by arepaking on 2009-01-28
> **drs305 said:**
> Note the kernel you are currently using:
```

uname -r

```
for instance: 2.6.27-9-generic

Open synaptic. 
Search for "linux-image"
You will see a variety of listing. In addition to "linux-image", you will see listings such as "linux-image-2.6.27-9-generic"
You can delete the ones of a lower number than the one you are using (such as linux-image-2.6.27-6-generic). Many people keep at least one older kernel on their system as a backup.
To delete the older kernels, right click, and select "Mark for complete removal", then "Apply".
You can also remove the associated "linux-headers..."
The removed kernels will also be automatically removed from grub's boot menu.


Hi,
Thanks for your quick response. I did what you just told me but I notice that linux-headers-2.6-27-9-generic still installed in the system. How can I make sure that all the dependencies from 2.6.27-9-generic are being removed?

Thanks again,
Ak

---

### Post by drs305 on 2009-01-28
[QUOTE=arepaking;6632615]Hi,
Thanks for your quick response. I did what you just told me but I notice that linux-headers-2.6-27-9-generic still installed in the system. How can I make sure that all the dependencies from 2.6.27-9-generic are being removed?

Thanks again,
Ak[/QUOTE

You would uninstall them the same way - select the specific header and mark for complete removal. 

Although synaptic will uninstall certain dependent packages when you select some items, the linux kernel isn't one of the them. If there are multiple items that will be uninstalled, you have a chance to review everything that will be uninstalled when you hit "Apply" by expanding the "To be completely removed" entry. 

In synaptic for the headers you will have to uninstall the headers separately.

---

### Post by arepaking on 2009-01-28
> **drs305 said:**
> [QUOTE=arepaking;6632615]Hi,
Thanks for your quick response. I did what you just told me but I notice that linux-headers-2.6-27-9-generic still installed in the system. How can I make sure that all the dependencies from 2.6.27-9-generic are being removed?

Thanks again,
Ak[/QUOTE

You would uninstall them the same way - select the specific header and mark for complete removal. 

Although synaptic will uninstall certain dependent packages when you select some items, the linux kernel isn't one of the them. If there are multiple items that will be uninstalled, you have a chance to review everything that will be uninstalled when you hit "Apply" by expanding the "To be completely removed" entry. 

In synaptic for the headers you will have to uninstall the headers separately.

Great! Thanks for the clarification.

Kind Regards,
AK

---

