---
title: "Remove default option from Grub"
date: 2006-02-10
forum: Desktop Environments
---

### Post by benmoreassynt on 2006-02-10
Hi,

Its easy enough to change the default OS in GRUB, and extend the time before it boots the default OS, but I would actually like not to have a default at all, and for GRUB to just wait for me to choose which OS I want. That's because some weeks I don't use Windows at all, other weeks I don't use Ubuntu. I'm forever loading the wrong OS! My own stupidity I know - I always go and get a coffee after pressing the computer's 'on' button.

Any idea how to do this?

Thanks
Ben

---

### Post by lha on 2006-02-10
Do
```
sudo gedit menu.lst
```
and find line
```
default 0
```
and replace it with
```
default saved
```. Then find the entries you usually use. For example, find line
```
title Windows
``` and add
```
savedefault
``` under it.

If you now boot Windows and shut your computer down, Windows will be default option next time.

You can also edit
```
timeout 10
``` to change the time before default option is automatically booted.

---

