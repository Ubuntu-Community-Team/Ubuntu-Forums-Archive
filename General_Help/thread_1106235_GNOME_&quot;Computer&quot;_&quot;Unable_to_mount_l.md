---
title: "GNOME &quot;Computer:///&quot;: &quot;Unable to mount location, Can't mount file&quot;"
date: 2009-03-25
forum: General Help
---

### Post by djbon2112 on 2009-03-25
When I insert any sort of removable media (USB drive, external HDD, iPod), the device shows up in "Computer:///", however double-clicking it gives me the above error. Now, I'm quite Linux savvy, I know that I can mount the drives manually, but I don't WANT to have to! Is there any reason why the GNOME "Computer:///" screen can't mount these files? Also, why do drives that have been manually mounted not show up here? As a preliminary idea I tried taking ownership of my /mnt folder (/media redirects to /mnt) but it changed nothing. Suggestions?

Using Ubuntu Studio Intrepid (8.10) x86_64.

---

### Post by jimmyhacker on 2009-03-25
you must type "computer://" not "Computer:///"

---

### Post by djbon2112 on 2009-03-26
> **jimmyhacker said:**
> you must type "computer://" not "Computer:///"
Both work for me. But either way I don't think this makes a difference regarding the issue at hand.

---

### Post by evilaim on 2009-03-26
Well, you could try to manually mount the media with the -f flag.  Should help a bit.  it's the Force flag.

---

### Post by djbon2112 on 2009-03-26
> **evilaim said:**
> Well, you could try to manually mount the media with the -f flag.  Should help a bit.  it's the Force flag.

That's exactly what I'm trying to avoid. I want to find out why the Nautilus "Computer" screen can't do it for me.

---

### Post by neilevan814 on 2009-03-27
Is it possible you did an unclean shutdown from a windows dual boot on this system??  I had that happen once and I needed to reboot into windows and do a complete shutdown with my external media mounted for linux to recognize and mount the media for me in gnome desktop

---

### Post by djbon2112 on 2009-03-27
> **neilevan814 said:**
> Is it possible you did an unclean shutdown from a windows dual boot on this system??  I had that happen once and I needed to reboot into windows and do a complete shutdown with my external media mounted for linux to recognize and mount the media for me in gnome desktop

They're all FAT32, but I always safely dismount them on both systems.

---

### Post by neilevan814 on 2009-03-27
Hope you get a solution here...this seems quite puzzling.  I will be interested to know myself.

---

### Post by djbon2112 on 2009-04-21
I'm still wondering if anyone has an explanation for this.

As best as I can tell, the "Computer:///" interface is a GNOME invention that seems to have very little functional compatibility with the actual Linux filesystem backend. Is there any possibility of getting this working? I'd really like to see something akin to Windows "My Computer" where every mounted partition and removable drive is shown in the Computer screen, as opposed to just random removable devices (that don't work), mounted network places (which only works via SMB), the CDROM drive and the Filesystem (which is all I see now).

---

