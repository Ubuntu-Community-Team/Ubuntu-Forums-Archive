---
title: "Unbootable USB Drive?"
date: 2009-03-02
forum: General Help
---

### Post by Altay_H on 2009-03-02
I have a 4GB USB drive made by SimpleTech which my BIOS doesn't seem to recognize. I've tried it on multiple machines and no BIOS has recognized its existence yet. I am sure these BIOSes have support for booting from USB, because they have no trouble recognizing and booting from my other 256MB USB Drive made by Memorex.

I have a friend who owns the exact same USB drive as I do and he was having the exact same problem I'm having. The BIOS simply does not acknowledge the existence of the USB drive. The drive works perfectly, it simply cannot be booted from.

It seems I have a non-bootable USB drive. I was under the impression that whether or not a USB drive was bootable depended *entirely* on the contents of the USB drive and was not hardware related. Am I wrong? Is it possible to have a non-bootable USB drive?

I used an img file to write a bootable [Arch] linux image to the drive, but I simply can't get any BIOS to even acknowledge the presence of the drive. I know how to boot from USB, but neither my friend nor I can boot from this hardware. Does anyone have any ideas or suggestions? Do I need to use a different USB drive? If so, why? Thanks for any help/comments/suggestions.


Here's the USB drive I simply can't boot from: [http://www.acsoutlet.com/STI-UFD%2F4GB-Standard.aspx](http://www.acsoutlet.com/STI-UFD%2F4GB-Standard.aspx)

---

### Post by Rallg on 2009-03-02
Might it be that the drive (as shipped) is partitioned? For example, could there be built-in security and privacy software in a hidden first partition? If so, perhaps you installed your boot image to the second partition, where a bootloader cannot find it?

I am just guessing.

If so, then you would need to nuke the built-in software and partitions. Can you look at the device in partition manager? If there is more than one partition, or something else occupying space, then you would need to remove it, and probably give the empty drive a new drive label. To be sure, in Terminal:

sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1

ought to nuke whatever is in the boot sector of the USB (where sdX is the device mount location).

Of course, you would lose any data already on the USB, so copy your stuff first.

It could also be that the USB has a buffering circuit that simply does not play well with a boot sector. If so, then the device really might be unbootable.

---

### Post by Altay_H on 2009-03-03
> **Rallg said:**
> sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1
The drive doesn't contain anything important currently, so I just "nuked" it with this command.


> **Rallg said:**
> Can you look at the device in partition manager?
Sure. I just used the command you suggested to nuke the partitions, then used dd to write an img file which wrote a bootable arch linux partition to the drive. I've attached an image of the current partition layout. I'll try booting from it in a bit.


EDIT:
Hey, it actually worked! Thanks so much. I'll mark this thread as solved if that tool ever returns...

EDIT2:
Interestingly, it still isn't working on one of my two computers. One computer recognizes both of my flash drives and can boot from either. The other computer only acknowledges one of my flash drives and boots successfully from it. Does the BIOS treat different flash drives differently?

---

### Post by Altay_H on 2009-03-04
Some more information about the situation:

I have two bootable flash drives and two computers that are capable of booting from flash drives. Any combination of flash drive and computer should be bootable, but only one isn't.

The BIOS of the computer that refuses to boot from my one particular flash drive has an option in its BIOS to allow the user to select a device to boot from. It displays *all* connected devices, including non-bootable ones. However, it doesn't display this particular USB drive.

This means that the problem isn't with the USB drive. For some reason my BIOS chooses not to see it as a device. I know it's possible to fix this problem because I have a friend with the exact same hardware who is able to boot from my flash drive. Any ideas as to why his BIOS would display my flash drive but mine won't?

---

### Post by Rallg on 2009-03-04
Happy to hear that there was a partial solution. I do not know why one computer would recognize the bootable drive, while another would not.

Might it be that the USB is classified as "removable media" (something other than USB) on the other computer, on the boot menu?

---

### Post by Altay_H on 2009-03-06
> **Rallg said:**
> Might it be that the USB is classified as "removable media" (something other than USB) on the other computer, on the boot menu?
No, unfortunately that's not the problem.

I have a friend with the same BIOS who was able to boot off of my USB drive. His BIOS also doesn't recognize it, but if he enters his BIOS settings and then exits (without making any changes) it will recognize the USB drive and boot successfully from it.

Unfortunately my BIOS is locked and I don't have the password. I'd just reset it my removing the battery, but my computer is a laptop. Do you know how I can unlock my BIOS? It wasn't a problem until now...

My computer is a Compaq tc4400.

Thanks.

---

