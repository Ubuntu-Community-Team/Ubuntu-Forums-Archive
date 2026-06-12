---
title: "Grub error 17 after re-install of XP"
date: 2006-03-22
forum: Desktop Environments
---

### Post by Deepsyx on 2006-03-22
Hello, 

I have Ubuntu installed on my secondary HDD /dev/sd1 Grub was working fine with a dual boot of XP PRO which was on my PrimaryHDD  /dev/sd0  I recently reinstalled XP knowing that it would overwrite the MBR and possibly Grub which it did. I tried to repair Grub with the ubuntu live cd and am having difficulty doing so. I was wondering if anyone would be able to give me some pointers?

hardware config is as follows

Nvidia nForce 2 Mobo 
AMD CPU
2 x WD Sata Drives Both set to raid 0 running independantly as 2 separate drives. 

to clarify a bit

Sata primary = Win xp pro
Sata Secondary = Ubuntu 5.10 Breezy 
Grub as bootloader

*EDIT* I am at work now and don't have the ubuntu version #'s that were in Grub or the Win settings or I would have posted them as well. I will try to get those when I get home and post them at that time if I can grab them. 

thanks in advance

~D~

---

### Post by benvdh on 2006-03-22
Hey,

From my experience with this problem I usually do the following:

1. boot from the livecd
2. mount your ubuntu partition somewhere. For example:
[COLOR="DarkRed"]
mount /dev/hdb4 /media/hdb4[/COLOR]

(make sure the point where you are going to mount exists.)

3. Change to your ubuntu partition using chroot:

[COLOR="DarkRed"]chroot /media/hdb4[/COLOR]

4. re-install grub:

[COLOR="DarkRed"]grub[/COLOR]

Hope this works for you,

Regards,

Ben

EDIT: link added

ps. else have a look at the following thread (gentoo, but could be used for this problem also)
[http://forums.gentoo.org/viewtopic.php?t=120802]("http://forums.gentoo.org/viewtopic.php?t=120802")

---

### Post by Deepsyx on 2006-03-22
I was thinking if this would work or not as I freshly re-installed Ubuntu about 1 week ago so nothign real drastic that I would need to change.

1. If I disconnect the Sata Cable from the Primary drive (WIN XP) and then reboot PC and re-install ubuntu on the Secondary Drive. That will isolate both systems and the MBR's on each HDD correct?

2. Or, will they migrate once the system is booted back up with both HDD's connected??? If they will remain separate with no changes to the MBR I could then change the Boot order in my raid config to the Secondary drive. and with the working Grub on the 2nd HDD add the settings for the WIN XP install. 

Or am I incorrect in the above assumption???

Any help would be appreciated.

~D~

---

### Post by Deepsyx on 2006-03-23
I am back online this time with both OS's bootable. Thanks for the help on this I tried what I suggested above and it worked like a champ. NO editing of any boot loaders just select the scsi disk that I want to boot from and away I go.

[QUOTE=Deepsyx]
1. If I disconnect the Sata Cable from the Primary drive (WIN XP) and then reboot PC and re-install ubuntu on the Secondary Drive. That will isolate both systems and the MBR's on each HDD correct?
[/QUOTE]
[QUOTE=Deepsyx]
I could then change the Boot order in my raid config to the Secondary drive. and with the working Grub on the 2nd HDD add the settings for the WIN XP install. 
[/QUOTE]

Thanks for the help,

~D~

---

