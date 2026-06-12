---
title: "increaseing wubi space"
date: 2008-12-15
forum: General Help
---

### Post by mrbiggbrain on 2008-12-15
hello, i just installed ubuntu by useing wubi, installed KDE4 and a few other things. i was wondering if there would be a way i could increase the size of the partition i created for ubuntu, i know that it is contained within a file under my windows system, is there any way i can load it as a block device under windows or linux and increase its size using gparted or the like?

i have some linux exspirience but i dont think i can mount the file and use gparted on it. some help would be useful

---

### Post by Jammanuser on 2008-12-15
> **mrbiggbrain said:**
> hello, i just installed ubuntu by useing wubi, installed KDE4 and a few other things. i was wondering if there would be a way i could increase the size of the partition i created for ubuntu, i know that it is contained within a file under my windows system, is there any way i can load it as a block device under windows or linux and increase its size using gparted or the like?

i have some linux exspirience but i dont think i can mount the file and use gparted on it. some help would be useful

You can change the size of ur Wubi install (i.e. the root.disk) with a program like [LVPM]("http://lubi.sourceforge.net/lvpm.html").

GL and hope this helps! :p

Cheers! ):P

Jam Man

:guitar:

---

### Post by mrbiggbrain on 2008-12-15
Thanks, i also saw that i could use it to put ubuntu on a partition, but is it possible to do this without overwriting my bootloader?

if not its fine, the ubuntu install i have right now is more for use of learning, and getting things down.

---

### Post by Jammanuser on 2008-12-15
> **mrbiggbrain said:**
> Thanks, i also saw that i could use it to put ubuntu on a partition, but [COLOR="Red"]is it possible to do this without overwriting my bootloader?[/COLOR]

if not its fine, the ubuntu install i have right now is more for use of learning, and getting things down.

Yes, it is possible...however, since i'm in the process of getting my **own** migrated Ubuntu to work, i'm not going to give u advice on how to do it just yet! ;) I managed to transfer my Wubi install using LVPM, and the Windows bootloader wasn't overwritten...it worked side by side with Grub, but i ended up deactivating Grub, and then attempting to use EasyBCD to add the Ubuntu boot option to my Windows bootloader, but i'm having trouble right now figuring out how to get it pointed at the right place! :lolflag:

Cheers! ):P

Jam Man

:guitar:

---

### Post by mrbiggbrain on 2008-12-15
will it give me the option to not overwrite th boot loader, or do i need to do something special before hand. the reason i say this is i dont think i have my vista disk to recover the vista bootloader should it be overwriten

---

### Post by jerome1232 on 2008-12-15
Sort of off topic but since you mentioned you don't have a recovery disc.

You may want to download this Vista Recovery Cd iso and test it, while it's **NOT** an installation cd it can get you to a recovery console to restore the MBR and such things.

edit: I did forget the link lol
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by Jammanuser on 2008-12-15
> **jerome1232 said:**
> Sort of off topic but since you mentioned you don't have a recovery disc.

You may want to download this Vista Recovery Cd iso and test it, while it's **NOT** an installation cd it can get you to a recovery console to restore the MBR and such things.

uhh...no offense, but i think u may have forgotten the link! ;)

Cheers! ):P

Jam man

:guitar:

---

### Post by jerome1232 on 2008-12-15
Ooops, I did forget the link, it's been edited in now :lolflag:

---

### Post by Jammanuser on 2008-12-15
> **mrbiggbrain said:**
> will it give me the option to not overwrite th boot loader, or do i need to do something special before hand. the reason i say this is i dont think i have my vista disk to recover the vista bootloader should it be overwriten

Ok...so now i've got my **own** LVPM transfer worked out! :D now i can help u with urs...

No, LVPM doesn't give u the option not to overwrite the Vista bootloader...however, once Grub is installed, u can access ur Windows bootloader via choosing the "Windows" option at the bottom of Grub! :D in other words, Grub doesn't overwrite the Vista bootloader, and so u can transfer it without hitch!

However, just a few words of advice...when using LVPM, be SURE to choose the correct partition to transfer to (mine was "sda4" but urs will probably be different)...because LVPM wipes the partition being transferred to of ALL data, before transferring! ;) And also, if u get to Grub (after transfer and reboot) and u can't boot into Ubuntu (like me)...it means u need to first edit ur menu.lst via ur **Wubi** install of Ubuntu (a LiveCD also works)!

If u need detailed instructions on how to edit it, i can help u with that...

Cheers! :lolflag:

Jam Man

:guitar:

---

### Post by mrbiggbrain on 2008-12-17
> **Jammanuser said:**
> Ok...so now i've got my **own** LVPM transfer worked out! :D now i can help u with urs...

No, LVPM doesn't give u the option not to overwrite the Vista bootloader...however, once Grub is installed, u can access ur Windows bootloader via choosing the "Windows" option at the bottom of Grub! :D in other words, Grub doesn't overwrite the Vista bootloader, and so u can transfer it without hitch!

However, just a few words of advice...when using LVPM, be SURE to choose the correct partition to transfer to (mine was "sda4" but urs will probably be different)...because LVPM wipes the partition being transferred to of ALL data, before transferring! ;) And also, if u get to Grub (after transfer and reboot) and u can't boot into Ubuntu (like me)...it means u need to first edit ur menu.lst via ur **Wubi** install of Ubuntu (a LiveCD also works)!

If u need detailed instructions on how to edit it, i can help u with that...

Cheers! :lolflag:

Jam Man

:guitar:

thanks, im thinking about transfering it over to an external HDD, guessing that wont be an issue. so if i do that, then grub will be installed into the MBR of the externel and boot im guessing.

---

### Post by Jammanuser on 2008-12-17
> **mrbiggbrain said:**
> thanks, im thinking about transfering it over to an external HDD, guessing that wont be an issue. so if i do that, then grub will be installed into the MBR of the externel and boot im guessing.

Just be sure to transfer to the correct place...get it wrong, and you'll have a lot of crap to deal with, i guarantee it! :D

transferring to an external HDD will be slightly more complicated, i imagine, even though i have never done it myself.

My guess is that the correct device string will be something like "sd**b**1" or "sd**c**1" without the quotes. 

GL and let me know how it goes! :popcorn:

Cheers! ):P

Jam Man

:guitar:

---

