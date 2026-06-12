---
title: "Recovery partition &quot;disabled&quot; by Ubuntu install?"
date: 2009-05-25
forum: General Help
---

### Post by allanlewis on 2009-05-25
I have an Acer Aspire 1642WLMi laptop that came with a recovery partition (about 3GB). I haven't touched this partition at all but installing Ubuntu seems to have "disabled" the recovery partition. I've tried installing a "standard" MBR (from syslinux) but trying to boot the recovery partition directly (by setting the "boot" label in gparted) doesn't work. I get a "Windows 98" splash screen and then an error message saying that command.com is "missing or corrupted". I've downloaded a program called IOPatch (or IOPat) that cliams to be able to patch IO.sys to fix this problem, but I don't want to mess with my recovery partition unless absolutely necessary. (I guess I could copy he original IO.sys somewhere and restore it if necessary...)

Is there any way I can restore my Windows XP installation? I have the Acer backup DVD I created when I first bought the computer, but that just has drivers on it and isn't bootable. (My DVD drive is playing up too and takes ages to load anything.) If I ran a Windows boot disk (perhaps from USB), would I be able to mount the recovery partition and run its "autoexec.bat"? (This seems to have a script to run Acer's recovery software.)

Any ideas?

---

### Post by Girl™ on 2009-05-25
I don't think this will be of much help to you, but: Ubuntu seems to find **all** partitions on your drive and count the rescue partition as free space. That happened to me once, with my old  thinkpad, and I had contact IBM and ask them to send me some rescue cd's instead.

---

### Post by allanlewis on 2009-05-25
> **Girl™ said:**
> I don't think this will be of much help to you
Correct ;)
> **Girl™ said:**
> ...but: Ubuntu seems to find **all** partitions on your drive and count the rescue partition as free space.
I know that, but I haven't overwritten the recovery partition: it's still there in tact, but I can't boot from it. I think I might just abandon Windows and give Ubuntu the whole drive.

Anyone else?

---

### Post by mike555 on 2009-05-25
Sometimes these "recovery" sections are only to be used with a recovery disc , the disc has the ability to start the recovery....  sometimes you can just hold a key while starting your computer (like f12 )to activate it ...... this info is usually displayed on the splash screen for your computer make.

---

### Post by allanlewis on 2009-05-26
> **mike555 said:**
> Sometimes these "recovery" sections are only to be used with a recovery disc , the disc has the ability to start the recovery...
Correct, but not with my laptop.
> **mike555 said:**
> ...sometimes you can just hold a key while starting your computer (like f12 )to activate it ...... this info is usually displayed on the splash screen for your computer make.
It's not displayed on the splash screen, but the manual says Alt+F10. This seems to rely on a particular MBR (possibly the one originally installed on the laptop) and it doesn't currently work. I've tried replacing the GRUB MBR with a "standard"/Windows one (from syslinux), but that hasn't worked either.

Does anyone know if it's likely that the original MBR installed on my laptop was somehow non-standard to deal with the recovery partition? Or are these things handled by the BIOS? There's a "D2D Recovery" option in the BIOS, which is currently set to "enabled". (I think it has always been enabled.)

I've tried patching the IO.sys file on the recovery partition using IOPatch but now it just sits at a "Windows 98" splash screen forever. (I left it for over an hour.) If I press "Esc" to see behind the splash screen, all I have is a blinking cursor, as if nothing is happening, although there is plenty of hard disk activity.

Any other ideas?

---

