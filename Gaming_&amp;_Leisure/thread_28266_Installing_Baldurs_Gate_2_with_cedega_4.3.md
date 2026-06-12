---
title: "Installing Baldurs Gate 2 with cedega 4.3"
date: 2005-04-19
forum: Gaming &amp; Leisure
---

### Post by nahkapaavali on 2005-04-19
Hi!

I´m trying to install Baldurs Gate - Shadows of Amn with Cedega 4.3 and i have a problem. When I´m trying to do full install and insert the second cd it doesn´t open the tray. I read at transgaming.org site that sometimes it´s necessary to manually change cd:s by typing: 

*umount /media/cdrom* 
*mount /media/cdrom*

It won´t let me do this but it keeps saying that cdrom is reserved or something.

Could you please tell me how to solve this? I would really appretiate it!  :)

---

### Post by jdodson on 2005-04-19
i would suggest using [http://gemrb.sourceforge.net/](http://gemrb.sourceforge.net/)

it is a GPL program that "wraps around" the baldurs gate games, making them playable on GNU/Linux.

here of some screenshots of it running baldurs 2:

[http://gemrb.sourceforge.net/index.php?module=photoshare&func=viewallfolders](http://gemrb.sourceforge.net/index.php?module=photoshare&func=viewallfolders)

[QUOTE=nahkapaavali]Hi!

I´m trying to install Baldurs Gate - Shadows of Amn with Cedega 4.3 and i have a problem. When I´m trying to do full install and insert the second cd it doesn´t open the tray. I read at transgaming.org site that sometimes it´s necessary to manually change cd:s by typing: 

*umount /media/cdrom* 
*mount /media/cdrom*

It won´t let me do this but it keeps saying that cdrom is reserved or something.

Could you please tell me how to solve this? I would really appretiate it!  :)[/QUOTE]

---

### Post by nahkapaavali on 2005-04-19
[QUOTE=jdodson]i would suggest using [http://gemrb.sourceforge.net/](http://gemrb.sourceforge.net/)

it is a GPL program that "wraps around" the baldurs gate games, making them playable on GNU/Linux.

here of some screenshots of it running baldurs 2:

[http://gemrb.sourceforge.net/index.php?module=photoshare&func=viewallfolders](http://gemrb.sourceforge.net/index.php?module=photoshare&func=viewallfolders)[/QUOTE]

Thanks fo your quick reply! 
I´ll go just then... playing! :D

---

### Post by nahkapaavali on 2005-04-20
Well i didn´t went straight to play. Having problems with installation of that program. Is there obvious reasons why i should use Gemrb instead of cedega?

 And what about that cedega issue when changing the installation cd. Is there any help for this?

Thanks!

edit: I tried to umount the cd with command *sudo umount /media/cdrom0/ -l*  and it unmount it, but i can´t open the tray! I tried to remount it but that didn´t help. I thibk that´s because of cedega something...

Little help would be appretiated on how do i open that tray. Thank you and kiitos!  :)

---

### Post by nahkapaavali on 2005-04-20
Think i´m flooding this thread :D

Ok , i have now switched the cd:s with these commands:

[I]sudo umount /media/cdrom0/ -l
sudo eject cdrom0
sudo mount /media/cdrom0/[/I]

but cedega won´t accept the second cd :( . It appears in fake- windows-my_computer as bg2_cd2 but it just won´t accept it. Maybe this is a cedega 4.3 issue and perhaps some older cedega/wine will work...Dunno.

Maybe i´ll look for this GemRB proggy one more time.

---

### Post by Muchacho_Gasolino on 2005-04-20
when im installing with a couple disks,i right click on the CD icon on the desktop and press eject whenever i need to switch

---

### Post by nahkapaavali on 2005-04-21
[QUOTE=Muchacho_Gasolino]when im installing with a couple disks,i right click on the CD icon on the desktop and press eject whenever i need to switch[/QUOTE]

Ok. For me this would´t work :(
When i try to open it that way it just opens a window where it says the device is busy, or something. I think that cedega reserves the right to use cdrom and when i forcefully open the tray then cedega won´t recognice the disk.  :confused: 

Have to try install another many cd game and hopefully learn something about this. ](*,)

---

