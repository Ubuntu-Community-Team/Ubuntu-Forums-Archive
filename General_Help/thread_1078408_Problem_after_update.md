---
title: "Problem after update"
date: 2009-02-23
forum: General Help
---

### Post by porchrat on 2009-02-23
Hi all I have had a bit of problem after a reboot.

Basically the system hadn't been updated for around 50 days and when I updated it it moved from kernel 2.6.27-9 to 2.6.27-11.

The update seemed to have gone smoothly, but when I rebooted the system it seems to freeze on this message:

```
/dev/sda:
  setting Advanced Power Management level to 0xfe (254)

/dev/sdb
  setting Advanced Power Management level to 0xfe (254)
```

It does show [OK], but no further activity happens.  The screen flickers on then off several times while this is displayed.

I can ctrl+alt+F1 to get to a tty terminal, but I can't seem to start gdm, recovery mode yields nothing of value.

Any help would be greatly appreciated.

I can't seem to find anything online about it either.

---

### Post by Thelasko on 2009-02-23
You should see an option to boot an older kernel in Grub, try one of them and see if it boots.

What kind of video card do you have?

---

### Post by porchrat on 2009-02-23
> **Thelasko said:**
> You should see an option to boot an older kernel in Grub, try one of them and see if it boots

Sorry probably should've mentioned that it does this regardless of which kernel I use.

On an aside not I dual boot this machine with Vista and as a result of the new menu.lst file Vista wasn't on it.  In order to at least allow Vista to boot until I got Ubuntu sorted out I edited the menu.lst adding the Vista partitionand rearranging the 3 kernels I currently run in numerical order.

This resulted in a different error, although Vista boots and I have checked that the UUID's all match so that isn't the problem either.

I will post the error when I next get a chance (probably tomorrow morning).

> What kind of video card do you have?

The machine is running an ATI x1250 or something I think (it isn't my machine). It has the catalyst 8.11 drivers installed if I can recall correctly.  Once again I will confirm this tomorrow morning, but as it turns out the gdm is running, however nothing is being displayed.

Thanx for replying.

---

### Post by Thelasko on 2009-02-23
I too dual boot Vista and Ubuntu, but I can't say I've heard of Vista disappearing from the menu.lst.  I have noticed Vista is no longer visible on the menu as it is off the page. This is because I never removed any of the old kernel entries.  Simply scrolling down reveals it though.

You likely need to reinstall the driver for your graphics card.  The proprietary ATI driver has a kernel module that sometimes has issues when you update your kernel.

---

### Post by porchrat on 2009-02-24
> **Thelasko said:**
> I too dual boot Vista and Ubuntu, but I can't say I've heard of Vista disappearing from the menu.lst.  I have noticed Vista is no longer visible on the menu as it is off the page. This is because I never removed any of the old kernel entries.  Simply scrolling down reveals it though.

You likely need to reinstall the driver for your graphics card.  The proprietary ATI driver has a kernel module that sometimes has issues when you update your kernel.

That is a good point, weird that I don't have an error though.  However even when I use the old kernel it still causes the error.  Wouldn't using the older kernel solve the problem?  I will of course reinstall it (I need a new driver anyway).

Failing that I will just reinstall as there is nothing particularly worthy of saving on that drive.

---

### Post by theShaggy on 2009-03-05
This has happened with me, as of yesterday (March 4th) with the Kernel update.

I've fully reinstalled Ubuntu, but it's still giving me the problem... I've installed the Nvidia drivers for my 7300 multiple times and there has been no change.

---

### Post by Thelasko on 2009-03-05
> **theShaggy said:**
> This has happened with me, as of yesterday (March 4th) with the Kernel update.

I've fully reinstalled Ubuntu, but it's still giving me the problem... I've installed the Nvidia drivers for my 7300 multiple times and there has been no change.

Are you sure your hardware didn't fail?

---

### Post by theShaggy on 2009-03-05
Looking in to that now, actually... it might just be.

---

### Post by porchrat on 2009-03-06
Just an update.

I haven't been able to solve this so I am just going to reinstall and see what happens.

Weird that theShaggy had this problem with his Nvidia system and I had it with an ATI system. Seems like it has nothing to do with what card you are running. Anyone have any idea what has caused this problem?

---

