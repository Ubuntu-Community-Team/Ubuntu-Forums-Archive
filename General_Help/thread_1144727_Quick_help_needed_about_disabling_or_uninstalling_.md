---
title: "Quick help needed about disabling or uninstalling a kernel"
date: 2009-05-01
forum: General Help
---

### Post by Mad dog on 2009-05-01
Hi, I recently installed a newer kernel and wish to revert back to my old one, since my video card driver won't work with the new one. I can Esc into GRUB before booting and select the old kernel, however, I'd rather the old kernel just booted automatically, either by making it default or removing the old one. Can someone please help me real quick. Thanks.:)

---

### Post by rob1408 on 2009-05-01
You should be able to uninstall it via Synaptic.  Just look for 'linux-image' and then the Kernel number.

---

### Post by Mad dog on 2009-05-01
I did that, but it's still first in my GRUB menu for some reason.

---

### Post by Mad dog on 2009-05-01
> **Mad dog said:**
> I did that, but it's still first in my GRUB menu for some reason.
 
Oops :x only removed the headers not the image. Thanks for your help :)

---

### Post by zero7404 on 2009-05-13
> **Mad dog said:**
> Oops :x only removed the headers not the image. Thanks for your help :)

if we wish to remove an older kernel, do we need to remove only the 2 components (header and image) or just the image ?

---

