---
title: "Removing the pc-speaker kernel module"
date: 2005-08-26
forum: Desktop Environments
---

### Post by daller on 2005-08-26
Hi All,

I just installed breezy, and it's quite a while since i installed hoary...

...In the meantime i've forgot where the pcspkr kernel-module is located (I wanna delete it, so that my pcspeaker is no longer initiallized)

Thanks...

---

### Post by vruum on 2005-08-26
```
locate pcspkr
``` 

but maybe adding it to /etc/hotplug/blacklist is slightly less hackish than just deleting it.

---

### Post by daller on 2005-08-29
Thanks - Will see if it works, next time I boot!

I'm trying to avoid hacking whereever possible :)

---

### Post by daller on 2005-08-29
Well, keeps on beeping - :(

---

### Post by az on 2005-08-29
...Works for me.


As soon as I remove the module:

sudo rmmod pcspkr

I can no longer beep when I use tab browsing for example.


Are you sure that you spelled it properly or put it on it's own line in /etc/hotplug/blacklist....

---

### Post by daller on 2005-08-29
rmmod pcspkr

ERROR: Module pcspkr does not exist in /proc/modules

---

### Post by az on 2005-08-29
Bummer.

---

### Post by Mishura on 2005-08-30
Whoa.. you mean there is a KERNEL MODULE for these blasted things to work?!  Thanks for letting me know!

** Rushes off to blacklist said module **

---

### Post by az on 2005-08-30
Maybe this will help, too?

Although, *nothing* will stop that beep when your bios is loading, before the OS gets started...

---

