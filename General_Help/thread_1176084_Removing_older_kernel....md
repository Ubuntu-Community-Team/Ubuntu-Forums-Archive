---
title: "Removing older kernel..."
date: 2009-06-01
forum: General Help
---

### Post by akakingess on 2009-06-01
I had updated my software (kernel) from .11 (Jaunty) to .12, and for some reason they both show up in Grub as options to boot up into. Is it best to just leave it be or should I remove that older kernel permanently or just remove it from Grub?  Also, will this always happening when updating the kernel or is this something that is normal so that you can roll back if you have issues with the new kernel?  Thanks in advance for any advice or information.

akakingess

---

### Post by DeMus on 2009-06-01
> **akakingess said:**
> I had updated my software (kernel) from .11 (Jaunty) to .12, and for some reason they both show up in Grub as options to boot up into. Is it best to just leave it be or should I remove that older kernel permanently or just remove it from Grub?  Also, will this always happening when updating the kernel or is this something that is normal so that you can roll back if you have issues with the new kernel?  Thanks in advance for any advice or information.

akakingess

Yes, you just install a new one, next to the old one. They both show up in Grub so you can choose. Just let the .11 stay there until you are absolutely sure .12 is working fine.
Should you decide to un-install .11 you can do so in Synaptic.

---

### Post by vegetarianshrimp on 2009-06-01
I found this very helpful when I had the same problem:
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by akakingess on 2009-06-02
Thank you both for the quick replies, I had thought I had done something wrong (being a noob, but it appears that I haven't done anything wrong, and now that I have been running the newer kernel for close to a month with no major issues, should I go ahead and uninstall the old one or just keep it there until the list in Grub gets as long as my screen when I boot up?

akakingess

---

### Post by lindsay7 on 2009-06-02
Down load Startup-Manager from Synaptic. It will show up under System/Administration.

You can set it to show as many releases as you want and they will not show up during booting, but the will still be there if you need them.

---

### Post by akakingess on 2009-06-02
> **lindsay7 said:**
> Down load Startup-Manager from Synaptic. It will show up under System/Administration.

You can set it to show as many releases as you want and they will not show up during booting, but the will still be there if you need them.
Thanks, Lindsay7 that will help me to keep my system clean and yet still have the backup if I need it. I love this forum because I seem to learn so darn much everyday, I know I am still a noob, but I think I am quickly working my way up to novice. Yeah for me (and I couldn't have made it this far without the help of everyone giving up their time and knowledge on this forum, so thanks yet again.

akakingess

---

### Post by mcduck on 2009-06-02
> **akakingess said:**
> Thanks, Lindsay7 that will help me to keep my system clean and yet still have the backup if I need it. I love this forum because I seem to learn so darn much everyday, I know I am still a noob, but I think I am quickly working my way up to novice. Yeah for me (and I couldn't have made it this far without the help of everyone giving up their time and knowledge on this forum, so thanks yet again.

akakingess

I'd recommend uninstalling the old kernels at some point. The kernel with all related files can easily take quite a lot of disks space, and even in worst case scenario you are not going to need more than one older kernel version.

So, keep one old version available, uninstall the rest as they are just wasting your disk space.

---

### Post by akakingess on 2009-06-02
> **mcduck said:**
> I'd recommend uninstalling the old kernels at some point. The kernel with all related files can easily take quite a lot of disks space, and even in worst case scenario you are not going to need more than one older kernel version.

So, keep one old version available, uninstall the rest as they are just wasting your disk space.
Thanks for the tip, but I am such a noob that I only have one older kernel (.11) and will keep that until the next one comes up, I had not even thought about the disk space usage and that makes a lot of sense.  Thanks again,

akakingess

---

