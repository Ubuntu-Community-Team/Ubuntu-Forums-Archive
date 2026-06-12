---
title: "Fedora 8 hangs post-install"
date: 2007-11-08
forum: Fedora/RedHat and derivatives
---

### Post by rudeboyskunk on 2007-11-08
I decided to try going back to Fedora with v8.  I was an avid user of Fedora when Core 3 was out (used it even more than Ubuntu at that time!), and want to see if they fixed all the crappiness that came with Core 4 in version 8 (yeah, I waited awhile).

Anyway, after installing it, it hangs right after GRUB boots into it.  It says "Red Hat Nash version *something*" (something being the version number), then just sits there.  Doesn't do anything.  I did a reinstall and same problem.

I tried posting on the Fedora Forums but got no reply.  I'm trying to increase my chances by posting on this forum and the Linux Forums.  Anybody have any ideas?

---

### Post by igknighted on 2007-11-08
> **rudeboyskunk said:**
> I decided to try going back to Fedora with v8.  I was an avid user of Fedora when Core 3 was out (used it even more than Ubuntu at that time!), and want to see if they fixed all the crappiness that came with Core 4 in version 8 (yeah, I waited awhile).

Anyway, after installing it, it hangs right after GRUB boots into it.  It says "Red Hat Nash version *something*" (something being the version number), then just sits there.  Doesn't do anything.  I did a reinstall and same problem.

I tried posting on the Fedora Forums but got no reply.  I'm trying to increase my chances by posting on this forum and the Linux Forums.  Anybody have any ideas?

That's real vague.  I had an issue once with the lvm's that sounds like yours, perhaps try manually partitioning with normal partitions instead of using lvm's (the default).

---

### Post by rudeboyskunk on 2007-11-08
I did.  On sda, I have sda1=OpenSuSE, sda2=Ubuntu, sda3=swap and sda4=Fedora.  I just made sda4 as / and let it do the rest.  I tried it with sda4 being both a primary and a logical partition, with the same result.

---

### Post by rudeboyskunk on 2007-11-08
Ok, right before the Red Hat nash version part, it says:

ACPI Invalid PBLK length [5]

Does that mean anything?

---

### Post by igknighted on 2007-11-08
> **rudeboyskunk said:**
> Ok, right before the Red Hat nash version part, it says:

ACPI Invalid PBLK length [5]

Does that mean anything?

Try adding the boot option acpi=off

---

### Post by rudeboyskunk on 2007-11-08
Do I just throw that into menu.lst?

---

### Post by igknighted on 2007-11-08
> **rudeboyskunk said:**
> Do I just throw that into menu.lst?

Add it to the end of the line calling the kernel.  So the line would look something like this: ```
kernel /vmlinuz-2.6.23.1-21.fc7 ro root=LABEL=/ noapic rhgb quiet acpi =off
```

Another thought... how sure are you that your CD is good?  That could very well be the issue.

---

### Post by rudeboyskunk on 2007-11-09
Ok, the thing said the dvd is fine.  LOST!!!

---

### Post by rudeboyskunk on 2007-11-09
Is there maybe a bootlog file that I can access?  I can mount that partition from Ubuntu no problem.  I just don't know where any bootlog file would be.

---

### Post by rudeboyskunk on 2007-11-09
Ok!  I deleted "quiet" from the kernel line in GRUB, and I see now where it gets stuck.  It says something along the lines of "attempting to resume from sda3."  NOW, sda3 is my swap partition.  I made it swap when I installed Ubuntu.  Would I have had to remake it as swap under Fedora?

---

