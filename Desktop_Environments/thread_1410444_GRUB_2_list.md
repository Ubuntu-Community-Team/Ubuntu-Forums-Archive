---
title: "GRUB 2 list"
date: 2010-02-18
forum: Desktop Environments
---

### Post by Droned on 2010-02-18
Hello,

After each update of ubuntu I get a new line in my GRUB 2 boot list, I know I can delete this with the manager or delete the entries from the list but I don't find that this is a good idea.

Is there maybe an option like in grub, where I can say that they have only have to show the latest kernel? Like grub had the #howmany=1?

Thanks in advance.

---

### Post by satx on 2010-02-18
> **Droned said:**
> Hello,

After each update of ubuntu I get a new line in my GRUB 2 boot list, I know I can delete this with the manager or delete the entries from the list but I don't find that this is a good idea.

Is there maybe an option like in grub, where I can say that they have only have to show the latest kernel? Like grub had the #howmany=1?

Thanks in advance.

I have wondered the same thing. I have a dual boot, and got good info on how to edit the config file so it defaults last in line (WIN 7 64). There has got to be a way to limit the number of entries given all the recent updates to the kernel- my list is getting quite long.](*,)](*,)](*,)

---

### Post by Grinr0th on 2011-01-11
To clean up the list you should remove the old kernels.
Here's a handy command to do that automatically for you.

First run this to be sure you're only removing the old kernels:

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
```

If this looks good for you (it should remove all kernels except the one you're running of course)
If you don't know for shure which version you're running type ```
uname -r
``` This returns te version you're running.

Then remove the old kernels with this command:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y remove
```

---

### Post by mrkazoodle on 2011-01-11
I always remove old kernels through synaptic [COLOR="DimGray"](system > admin > synaptic package management)[/COLOR]: search for "linux-image" [COLOR="DimGray"](you'll like to sort the list by installed software)[/COLOR] and delete the oldest version [COLOR="DimGray"](mark for removal and apply the change)[/COLOR]. It automatically updates your grub menu.
I like this way better because I like doing it manually.
PS: I always keep one old kernel (better safe than sorry)

---

