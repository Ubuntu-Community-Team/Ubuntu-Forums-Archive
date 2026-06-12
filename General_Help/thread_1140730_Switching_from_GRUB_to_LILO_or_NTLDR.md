---
title: "Switching from GRUB to LILO or NTLDR"
date: 2009-04-27
forum: General Help
---

### Post by ironstoneh on 2009-04-27
G'day all.
 
I have a Clevo M57U laptop on which I need to dual-boot Ubuntu (8.1) and XP. However, the Clevo has a know issue with GRUB - it makes the DVD-RW device invisible to Windows. The only know solutions are to boot using LILO or NTLDR.

So, for NTLDR, I have dd'd the first 512B of my Ubuntu /boot partition to the Win C:\ directory, and configured the boot.ini to pick it up, but it just hangs on a blank screen: my guess is because GRUB is in the MBR; this sounds a but like catch 22 to me, because a) I don't know how to move GRUB out of the MBR and into the /boot partition, and b) if I get it wrong, I'll need to fix the MBR.

For LILO, I have configured the lilo.conf file. When I tried to install LILO to the MBR, it for some reason installed NTLDR there - which, as I've said, doesn't work.

It seems such a simple thing, why is it so difficult? All I need is to ensure that booting Windows doesn involve GRUB at any point.

Can anyone help me out? Please?

Edwin
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7164975")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7164975")

---

