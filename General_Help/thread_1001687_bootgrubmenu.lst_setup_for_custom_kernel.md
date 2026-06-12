---
title: "/boot/grub/menu.lst setup for custom kernel"
date: 2008-12-04
forum: General Help
---

### Post by zilla62 on 2008-12-04
I built a new kernel and installed it. The installation process, asked me if I wanted to keep the current menu.lst, or use the package's menu.lst. I elected to keep mine. Now how do I include the custom kernel in my menu.lst? I'm confused regarding getting the uuid values. In hindsight I should've elected to merge the two. Here's my current one.

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu 8.10, kernel 2.6.27-9-generic
uuid            55e5cb9c-e823-4b2f-ba9f-389574c4032b
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=55e5cb9c-e823-4b2f-ba9f-389574c4032b ro quiet splash
initrd          /boot/initrd.img-2.6.27-9-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid            55e5cb9c-e823-4b2f-ba9f-389574c4032b
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=55e5cb9c-e823-4b2f-ba9f-389574c4032b ro  single
initrd          /boot/initrd.img-2.6.27-9-generic

---

### Post by mikewhatever on 2008-12-04
You'll need to edit GRUB's menu to include the new kernel. If the kernel is in /boot, then <ls /boot> should show all relevant info.

---

### Post by zilla62 on 2008-12-04
> **mikewhatever said:**
> You'll need to edit GRUB's menu to include the new kernel. If the kernel is in /boot, then <ls /boot> should show all relevant info.

I KNOW to add the info in /boot/grub/menu.lst, but what info, specifically, the uuid information - how do I get that for the new kernel? Thanks.

---

### Post by caljohnsmith on 2008-12-04
> **zilla62 said:**
> I KNOW to add the info in /boot/grub/menu.lst, but what info, specifically, the uuid information - how do I get that for the new kernel? Thanks.
The UUID is to identify the Ubuntu partition, so it doesn't change for your different kernels. If you built your own 2.6.27-XX-generic kernel, just change all the kernel references in the boot stanza:
```
title Ubuntu 8.10, kernel [COLOR="Blue"]2.6.27-XX-generic[/COLOR]
uuid 55e5cb9c-e823-4b2f-ba9f-389574c4032b
kernel /boot/vmlinuz-[COLOR="Blue"]2.6.27-XX-generic[/COLOR] root=UUID=55e5cb9c-e823-4b2f-ba9f-389574c4032b ro quiet splash
initrd /boot/initrd.img-[COLOR="Blue"]2.6.27-XX-generic[/COLOR]
quiet
```
And that should be all it takes. :)

---

### Post by mikewhatever on 2008-12-04
If you need more help, please post the output of <ls /boot>.

---

### Post by zilla62 on 2008-12-04
> **caljohnsmith said:**
> The UUID is to identify the Ubuntu partition, so it doesn't change for your different kernels. If you built your own 2.6.27-XX-generic kernel, just change all the kernel references in the boot stanza:
```
title Ubuntu 8.10, kernel [COLOR="Blue"]2.6.27-XX-generic[/COLOR]
uuid 55e5cb9c-e823-4b2f-ba9f-389574c4032b
kernel /boot/vmlinuz-[COLOR="Blue"]2.6.27-XX-generic[/COLOR] root=UUID=55e5cb9c-e823-4b2f-ba9f-389574c4032b ro quiet splash
initrd /boot/initrd.img-[COLOR="Blue"]2.6.27-XX-generic[/COLOR]
quiet
```
And that should be all it takes. :)

I'm just dumb...

I did this but had a type on the name, *-2-custom instead of *.2-custom. Duh. Once recognized this it worked, and is what I'm using now.

---

