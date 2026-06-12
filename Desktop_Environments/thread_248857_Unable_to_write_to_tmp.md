---
title: "Unable to write to /tmp"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-01
Brand new problem today! Immediately after login, Kubuntu complains about not being able to write to /tmp, and dumps me back at the login screen. I've no idea what's causing this, as my last reboot was the last one in a long time that happened after no major changes to the system.

---

### Post by taurus on 2006-09-01
Could be that there is no space left on /tmp or the permission somehow has changed!  So boot into recovery mode (from GRUB menu) and check for space with

```
df -h
```
Otherwise, reset the permissions to /tmp with

```
chmod 777 /tmp
```

---

### Post by Rhapsody on 2006-09-01
Pretty much as I suspected. hda2 has just 60KB free. Wine must've pushed it over the edge.

I will first note that this is highly ironic as I was worried that 5GB wasn't going to be enough (I was told it would be fine, and decided I'd give /home an extra 5GB rather than doubling the size) and tried to check for space just prior to installing Wine (which I seemed unable to do, I could check space on my Windows drives, but not /home or the one that was almost full).

But that's all irrelevant. It's full now, and Kubuntu won't boot. So what am I supposed to do now?

---

### Post by taurus on 2006-09-01
5GB is plenty if you don't install a bunch of extra stuff on it!!!  You need to boot your machine from the LiveCD and mount your / somewhere and go in and clean out the /tmp...

---

### Post by Rhapsody on 2006-09-01
> **taurus said:**
> 5GB is plenty if you don't install a bunch of extra stuff on it!!!
Right. So next time I'm told how much space I need, I'll remember to double or treble the figure.

> **taurus said:**
> You need to boot your machine from the LiveCD and mount your / somewhere and go in and clean out the /tmp...
I've been meaning to make an Ubuntu 6.06 Live CD for a while now. If I do that, will the version of GParted on the disc be able to copy data from an NTFS partition to an ext3 partition? Because I want to kill two birds with one stone here if at all possible.

Also, GRUB currently gives me a choice of *four* different kernels upon boot-up (2.6.15-26-386, 2.6.15-19-386, 2.6.12-10-386, and 2.6.12-9-386, IIRC) of which I'm only using the most recent. Would it help matters to find a way to kill off the old ones?

---

### Post by taurus on 2006-09-01
> **Rhapsody said:**
> Right. So next time I'm told how much space I need, I'll remember to double or treble the figure.

Give it as much space as you can afford so you don't have to worry about space later.  ;) 

> I've been meaning to make an Ubuntu 6.06 Live CD for a while now. If I do that, will the version of GParted on the disc be able to copy data from an NTFS partition to an ext3 partition? Because I want to kill two birds with one stone here if at all possible.

Are you talking about move files from your Windows, NTFS, to Ubuntu, ext3?  Yes, you can from the LiveCD as long as you mount both of them first.

And nobody is going to kill any bird around here...  :twisted: 

> Also, GRUB currently gives me a choice of *four* different kernels upon boot-up (2.6.15-26-386, 2.6.15-19-386, 2.6.12-10-386, and 2.6.12-9-386, IIRC) of which I'm only using the most recent. Would it help matters to find a way to kill off the old ones?
You can remove the entries for your old kernel in /boot/grub/meny.lst.  Again, you can do that from a LiveCD as long as you mount / (or /boot if you have /boot) somewhere first so you can edit /boot/grub/menu.lst.

---

### Post by Rhapsody on 2006-09-01
I've actually thought up of a brand-new plan for this (in keeping with my usual pattern of thinking up of my eventual plans at the last minute).

Instead of trying to fix my root partition (which is clearly broken in quite fundamental ways due to 5GB being nowhere near enough), I just nuke the whole thing and start again. Call those first six months a trial run, and start again from scratch.

So I use the Ubuntu Live CD to shuffle my big NTFS partition (on my secondary 250GB drive) around until I have a 248GB ext3 partition with around 90GB of data on it. Then I copy any data I want to keep from my old FAT32 and /home partitions (which won't take up any more than 20GB at the very most) onto the big ext3 partition (which is on different drive from the others).

After this, I reboot and use a new Kubuntu install CD to make a new 30GB (a ludicrous amount this this PC should never reach) root partition at the start of my smaller 80GB drive and a 50GB /home partition (double the 25GB I have now).

This would give me a lot more breathing room, clear out six months of somewhat clumsy learning from my Kubuntu install, and finish a lot of tasks I've been meaning to do for a while now. It'll eliminate my Windows fallback, but that was going to happen sooner or later.

So, sanity check time. Is any of this really not going to work, or does my plan look good?

---

