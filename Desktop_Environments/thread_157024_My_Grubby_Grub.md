---
title: "My Grubby Grub"
date: 2006-04-08
forum: Desktop Environments
---

### Post by ububaba on 2006-04-08
I have several kernels listed in my menu.lst, I was just wondering if all kernels except
 **[COLOR="Magenta"]Ubuntu, kernel 2.6.12-9-686-smp[/COLOR]** are deleted, would it cause any damage or would
it quicken the boot time?

---

### Post by llamakc on 2006-04-08
It will not quicken boot time by removing kernel entries in your menu.lst file. However, if your menu.lst has a long timeout set:

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

```

You can change that number to something lower. This will make the boot sequence begin quicker.

You can see which kernel images you have installed in the Terminal with:

# sudo dpkg -l | grep linux-image

And then apt-get remove the appropriate ones you no longer wish to have. I'm sure there are other ways to clean up your menu.lst too.

I'm not familiar with using update-grub after manually editing menu.lst, which could work for you also.

---

### Post by ububaba on 2006-04-08
[QUOTE=llamakc]It will not quicken boot time by removing kernel entries in your menu.lst file. However, if your menu.lst has a long timeout set:

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

```

You can change that number to something lower. This will make the boot sequence begin quicker.

You can see which kernel images you have installed in the Terminal with:

# sudo dpkg -l | grep linux-image

And then apt-get remove the appropriate ones you no longer wish to have. I'm sure there are other ways to clean up your menu.lst too.

I'm not familiar with using update-grub after manually editing menu.lst, which could work for you also.[/QUOTE]


I have yet to learn how to remove unwanted stuff from apt-get. 
Your suggestion  did shorten the time a wee bit. **Thanks a bunch.**

---

