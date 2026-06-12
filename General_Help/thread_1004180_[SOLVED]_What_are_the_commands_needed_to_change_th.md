---
title: "[SOLVED] What are the commands needed to change the default..."
date: 2008-12-06
forum: General Help
---

### Post by Jammanuser on 2008-12-06
ISO when installing Wubi? I'm about to reinstall it, and so i would like to do it the easy way, i.e. use the ISO that i already have, instead of spending the time it takes (AGAIN!) to download the 699 MB ISO!

Looking forward to ANY and ALL replies... ;)

Cheers! :)

-jammanuser

:D

---

### Post by azmo35 on 2008-12-07
Well when installed wubi,	
I used the iso I had in the same folder I think you will not have no problem.
From [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
 
Can I use an existing ISO/CD instead of letting Wubi download a new one?
Yes, physical CDs will be detected automatically, pre-downloaded ISOs should be placed in the same folder as Wubi.exe. Please note tha Wubi 8.10 requires the Desktop 8.10 CD/ISO. The DVD and Altrenate CD/ISO will not work. You can find the 8.10 ISO here. If Wubi does not find an appropriate ISO/CD and/or if the ISO/CD is corrupted, it will automatically download a new ISO. It is recommended to let Wubi download the ISO for you.
	
I hope that helps thanks,AZMO):P

---

### Post by Jammanuser on 2008-12-07
> **azmo35 said:**
> Well when installed wubi,	
I used the iso I had in the same folder I think you will not have no problem.
From [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
 
Can I use an existing ISO/CD instead of letting Wubi download a new one?
Yes, physical CDs will be detected automatically, pre-downloaded ISOs should be placed in the same folder as Wubi.exe. Please note tha Wubi 8.10 requires the Desktop 8.10 CD/ISO. The DVD and Altrenate CD/ISO will not work. You can find the 8.10 ISO here. If Wubi does not find an appropriate ISO/CD and/or if the ISO/CD is corrupted, it will automatically download a new ISO. It is recommended to let Wubi download the ISO for you.
	
I hope that helps thanks,AZMO):P

ok...thanks!!! :D REALLY appreciate it, lol! :)
I'll try it, and let u know if it works! ;)

Cheers! ):P

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-07
Ok...so i tried reinstalling Wubi, with my old ISO in the same folder as it, but I think it rejected it, and decided to download the ISO anyway, because i've been installing it for several hours, and it still says the file size of the stuff its downloading is 699 MBS...which i assume is the ISO its trying to **download**, instead of using the one that i already had! :confused:

Can anyone please tell me why it doesn't appear to be using my pre-installed ISO? ):P

Thanks in advance! :)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-07
And now I have successfully reinstalled Wubi... :guitar:

Cheers! 

It appears, though, balaknair, that backing up the root.disk **before **uninstalling Wubi, and then replacing the **new **root.disk with the **old** root.disk did not allow me, after all, to still have my files and programs from my OLD install of Wubi! :sad:

And so now i lost the program that i had in my OLD install of Wubi...that i manually built! it appears as if the programs and files are stored somewhere other than the root.disk...

Of course, i backed up everything before uninstalling Wubi...including my personal files, and the WHOLE folder of "ubuntu"! so if anyone could tell me where exactly all that stuff is located then, if not in the root.disk...it would be really nice! (hint, hint) ):P

Cheers! 

-jammanuser

:p

---

### Post by magmon on 2008-12-07
Jamman, the live CD can create a new partition for a more stable install. You have to burn the disk tho. I recommend doing this from wubi.

---

### Post by Jammanuser on 2008-12-08
> **magmon said:**
> Jamman, the live CD can create a new partition for a more stable install. You have to burn the disk tho. I recommend doing this from wubi.

yah...that's what i was planning to do! No WAY am i going to take the chance with the crc error on Wubi again...i wont take that risk again! as soon as i finish downloading a movie torrent using BitTorrent, on Windows, i plan on defragmenting, and then will get right on creating a dedicated partition for Ubuntu 8.10! :D thanks anyway, though! and just fyi...i already have the LiveCD, because i burned one several days ago! :guitar:

Cheers! ):P

-jammanuser

P.S. in my above post, i stated that i needed to know which file (when using Wubi) in the "ubuntu" folder contains the program files, personal data, etc...if not in the root.disk itself, because i backed up my old one, and replaced the new one with it, mistakenly thinking that that would solve the problem with me not wanting to lose my programs that i had already installed (on my old Wubi), by simply replacing the root.disk with the old one! but it appears as if it doesn't contain the stuff on Ubuntu 8.10 OS after all (that is, MY stuff, i.e. my programs, and personal files!)...balaknair said (suggested?) that it did! :confused: XD :guitar:

---

### Post by Jammanuser on 2008-12-08
> **Jammanuser said:**
> And now I have successfully reinstalled Wubi... :guitar:

Cheers! 

It appears, though, balaknair, that backing up the root.disk **before **uninstalling Wubi, and then replacing the **new **root.disk with the **old** root.disk did not allow me, after all, to still have my files and programs from my OLD install of Wubi! :sad:

And so now i lost the program that i had in my OLD install of Wubi...that i manually built! it appears as if the programs and files are stored somewhere other than the root.disk...

Of course, i backed up everything before uninstalling Wubi...including my personal files, and the WHOLE folder of "ubuntu"! so if anyone could tell me where exactly all that stuff is located then, if not in the root.disk...it would be really nice! (hint, hint) 

Cheers! 

-jammanuser



Never mind, balaknair! :D scratch that! ^ I figured out what i did wrong...**apparently** Wubi wipes the root.disk the first time booting, after the install, and so what must of happened, was Wubi deleted all the files and settings that had been on the root.disk before...resulting in, of course, the apparently fresh install of Ubuntu 8.10, i.e. with all the stuff that had been previously on there wiped off! 

so anyway, how I fixed that problem, was simply (after booting into Ubuntu 8.10, and getting that result, of course!) was replacing the root.disk AGAIN with the old root.disk...and this time it worked!!! Now I have my stuff again, and i am EXTREMELY happy! 

I don't know how I could ever thank u enough...Thank you, thank you, thank you, thank you, thank you, thank you, thank you...oh! and thanks again! :D

I have now (thanks to you!) successfully "regenerated" if u will, my Wubi install of Ubuntu, so that I now have all my old stuff back...without doing all the hard work again! MAN! am i happy! :D 

For all those who might also experience the "crc error, system halted" error message at bootup as I did...here's what can be done to fix it, and to return it to the way it was before:

1) back up ur root.disk, which can be found at Computer (if on Vista...if on XP, then it would be "My computer")>C:/>ubuntu>disks>root.disk
Create a copy of this, and then back it up to somewhere safe...i.e. like another hard drive or CD...flash drive, etc.
2) Reinstall Wubi
3) boot into Ubuntu 8.10 the first time, after install...by rebooting after the install is done, and then choosing the "Ubuntu" boot option in the boot menu.
4) Let the **final** installation complete, after booting into Ubuntu, and getting past the login screen...i.e. after typing ur username and password.
5) Reboot again.
6) Boot into Windows again.
7) Retrieve ur backed up "root.disk" from wherever u saved it to.
8) Open up the Ubuntu folder again, on ur C drive.
9) Cut, and then paste onto ur desktop the root.disk that's currently in there...i.e. the **new** one.
10) Next cut, and paste the **older** one from wherever u saved it, to (or copy it, if u prefer...although, be warned, it'll take longer!:p) the same place where the **new** one was previously located, i.e. in ur "Disks" folder in "Ubuntu"!

Note: what u just did was simply swapped the "root.disk"s around, so now the old one is in the place that the new one previously occupied...and vice versa!

11) Reboot ur computer again, and once more boot into Ubuntu...u should now see the Wubi install setup the way u had it previously **before** the CRC ERROR! Congratulations! :D You just successfully fixed ur Wubi install! Now if u have any sense, u will do what i'm about to do...i.e. move the Wubi install of Ubuntu 8.10 to a dedicated partition, using the LVPM tool! Cheers! 

-jammanuser

:guitar

---

