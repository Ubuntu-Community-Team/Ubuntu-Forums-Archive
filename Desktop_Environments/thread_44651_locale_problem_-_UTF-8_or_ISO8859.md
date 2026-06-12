---
title: "locale problem - UTF-8 or ISO8859"
date: 2005-06-27
forum: Desktop Environments
---

### Post by AndreasMeier on 2005-06-27
Hi folks,

I have a problem with my desktop settings in Kubuntu Hoary, which is installed on my Desktop.
I am in website development and want to update a database.
I have edited the txt-file in kspread and saved it.
My whole ubuntu system is set to locale = "de_DE.UTF-8".
When I upload the txt-file to my database and see what I get,
all german special chars like "ß", "ä", "ü" etc. are wrong and are displayed with cryptic chars.
I guess I have to set it to ISO8859-1 or something like that.

What do you mean, which settings are best or most common, and how can I change my settings in ubuntu ?

Thanks in advance,
Kind regards,
Andreas

---

### Post by tbresson on 2005-06-27
I have issues with danish characters and I use ISO-8859-1 typed exactly like that.

Hope it helps.

---

### Post by smarttaz on 2005-06-27
[QUOTE=AndreasMeier]Hi folks,

I have a problem with my desktop settings in Kubuntu Hoary, which is installed on my Desktop.
I am in website development and want to update a database.
I have edited the txt-file in kspread and saved it.
My whole ubuntu system is set to locale = "de_DE.UTF-8".
When I upload the txt-file to my database and see what I get,
all german special chars like "ß", "ä", "ü" etc. are wrong and are displayed with cryptic chars.
I guess I have to set it to ISO8859-1 or something like that.

What do you mean, which settings are best or most common, and how can I change my settings in ubuntu ?

Thanks in advance,
Kind regards,
Andreas[/QUOTE]

For my part, I have other locale problems: Ubuntu has the filesystem in UTF-8, but my CD-ROMs burned in Joliet filesystem have French and German filenames in some ISO-8859-1 I guess.

Hence, I can NOT read correctly filenames from a mounted CD-ROM if the filename contains extended French or German characters.

However, under SuSE 9.3, which also seems to use utf8, I can get correctly mounted CD-ROMs! (iso-8859-1 or somehow it can read them!)

I have also read all the threads related to UTF-8 in Ubuntu and I still can't get some things:

1. Some people say: "switch to your locale if having problems". Why is that UTF-8 good at? I want to be able to use more ecclectic characters -- don't forget, even Windows (NTFS) uses Unicode and can show characters from different code pages in the same filename!!

2. Some people say: "switch to UTF-8 and delete/forget about all locales if having problems". Wow, but then how will I be able to read my CDs with Joliet filesystem and French/German filenames? Currently, I cannot read them in Hoary (not in Colony-1 either), but only in SuSE 9.3 and... Windows!

What's the problem with the inetrnationalization and the Ubuntu team? They seem to be so shortsighted... :(

OTOH, another lack in Linux in general is the ability to switch quickly between keyboard layouts and languages. Because the Compose feature of GNOME (with AltGr) does not help me to write in all languages I want, and I'm doing this much more easy in Wingoze... :(

Linux, the greatest international project, with the worse support for ALL Internationalization issues... (1. cannot use UTF-8 only, if another filesystem is iso-8859-1!!; 2. can not use multiple languages with or without dead keys as easy as in Wingoze.)

R.

---

### Post by lukasmaci on 2005-06-28
I have the same problem with czech characters. Ubuntu is great distribution, but the only one, I have tested, which has this problems. I hope, this should be solved in Breezy Badger

---

### Post by smarttaz on 2005-06-28
[QUOTE=lukasmaci]I have the same problem with czech characters. Ubuntu is great distribution, but the only one, I have tested, which has this problems. I hope, this should be solved in Breezy Badger[/QUOTE]
The same applies to Breezy Badger Colony-1.
Maybe I'll try tonight to "compare" it against SuSE 9.3 to see how things "should be done".

---

### Post by AndreasMeier on 2005-06-28
No, I had the same problem in Suse 9.3.
I think it is a "trend" to go for UTF-8 to have a unique and plattform-independent setting for network things like files / samba etc.
So far, the development is correct. 
But only windows has ISO8859-1 or something like that,
or in my case some internet plattforms needs iso-code as well.

Regards,
Andreas

---

### Post by smarttaz on 2005-06-28
[QUOTE=AndreasMeier]No, I had the same problem in Suse 9.3.
I think it is a "trend" to go for UTF-8 to have a unique and plattform-independent setting for network things like files / samba etc.
So far, the development is correct. 
But only windows has ISO8859-1 or something like that,
or in my case some internet plattforms needs iso-code as well.
 
Regards,
Andreas[/QUOTE]
 
Maybe it's because you used an editor that saved the *contents* of the file in UTF-8!
You said "have edited the txt-file in kspread and saved it."
But at least SuSE 9.3 copes well with file *names*!
 
R.

---

### Post by EcliptuX on 2005-06-28
[QUOTE=smarttaz]For my part, I have other locale problems: Ubuntu has the filesystem in UTF-8, but my CD-ROMs burned in Joliet filesystem have French and German filenames in some ISO-8859-1 I guess.

Hence, I can NOT read correctly filenames from a mounted CD-ROM if the filename contains extended French or German characters.

However, under SuSE 9.3, which also seems to use utf8, I can get correctly mounted CD-ROMs! (iso-8859-1 or somehow it can read them!)

I have also read all the threads related to UTF-8 in Ubuntu and I still can't get some things:

1. Some people say: "switch to your locale if having problems". Why is that UTF-8 good at? I want to be able to use more ecclectic characters -- don't forget, even Windows (NTFS) uses Unicode and can show characters from different code pages in the same filename!!

2. Some people say: "switch to UTF-8 and delete/forget about all locales if having problems". Wow, but then how will I be able to read my CDs with Joliet filesystem and French/German filenames? Currently, I cannot read them in Hoary (not in Colony-1 either), but only in SuSE 9.3 and... Windows!

What's the problem with the inetrnationalization and the Ubuntu team? They seem to be so shortsighted... :(

OTOH, another lack in Linux in general is the ability to switch quickly between keyboard layouts and languages. Because the Compose feature of GNOME (with AltGr) does not help me to write in all languages I want, and I'm doing this much more easy in Wingoze... :(

Linux, the greatest international project, with the worse support for ALL Internationalization issues... (1. cannot use UTF-8 only, if another filesystem is iso-8859-1!!; 2. can not use multiple languages with or without dead keys as easy as in Wingoze.)

R.[/QUOTE]

I had exactly the same problems with Ubuntu :(
Every time there is a component with locales problem : apache, nautilus and the file names....](*,)
Is there a tutorial or a how-to to solve definitly the problem ?

---

### Post by rwabel on 2005-07-01
I had the same problem, when ubuntu switched from ISO8859 to UTF-8 once during the hoary beta.
It tooks me long, but finally it was quit simple for me. Even my old windows burned cd's are correctly displayed with the french and german accents.

1. check that your system is completly on utf-8
2. mount the partitions, cdrom and stuff with utf-8

for example the cdrom:
/dev/hdc        /media/cdrom0 udf,iso9660 ro,user,noauto,utf8 0 0

or a fat32 partition:
/dev/hdb5       /mnt/hdb5       vfat    user,rw,exec,auto,umask=000,utf8

I hope it helps, let me know if it's working!

---

### Post by smarttaz on 2005-07-01
[QUOTE=rwabel]I had the same problem, when ubuntu switched from ISO8859 to UTF-8 once during the hoary beta.
It tooks me long, but finally it was quit simple for me. Even my old windows burned cd's are correctly displayed with the french and german accents.
 
1. check that your system is completly on utf-8
2. mount the partitions, cdrom and stuff with utf-8
 
for example the cdrom:
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto,utf8 0 0
 
or a fat32 partition:
/dev/hdb5 /mnt/hdb5 vfat user,rw,exec,auto,umask=000,utf8
 
I hope it helps, let me know if it's working![/QUOTE]
 
Thank you!!
 
For my part, I'll try this in the weekend. However, Ubuntu or not (I'm still sthinking of SuSE as well), there are two issues:
1. Manually mounting with info from /etc/fstab is one way...
2. Mounting (usb sticks, etc.) with "udev" is another way.
I'm not sure "udev" reads /etc/fstab, since it doesn't need to, so I may find myself with 2 different mounted devices! (speaking about usb flash, not cd-rom)
Actually, I hate udev!
 
I just remembered that one of two CDs happen to behave differently in Windows, Ubuntu Hoary and SuSE 9.2/9.3, when fdisked/formatted in Windows versus fdisked/formatted in Ubuntu!
 
Radu
p.s. Ralph, do you know how to use Genius Vivid series scanners with xsane in Ubuntu Hoary? They send me to Genius for some firmware & stuff, which is absurd. Rumours say it could work with SuSE 9.3, but I was very busy and not trying yet...

---

### Post by rwabel on 2005-07-01
[QUOTE=smarttaz]Thank you!!
 
For my part, I'll try this in the weekend. However, Ubuntu or not (I'm still sthinking of SuSE as well), there are two issues:
1. Manually mounting with info from /etc/fstab is one way...
2. Mounting (usb sticks, etc.) with "udev" is another way.
I'm not sure "udev" reads /etc/fstab, since it doesn't need to, so I may find myself with 2 different mounted devices! (speaking about usb flash, not cd-rom)
Actually, I hate udev!
 
I just remembered that one of two CDs happen to behave differently in Windows, Ubuntu Hoary and SuSE 9.2/9.3, when fdisked/formatted in Windows versus fdisked/formatted in Ubuntu!
 
Radu
p.s. Ralph, do you know how to use Genius Vivid series scanners with xsane in Ubuntu Hoary? They send me to Genius for some firmware & stuff, which is absurd. Rumours say it could work with SuSE 9.3, but I was very busy and not trying yet...[/QUOTE]
 About udev and usb, I had no problems. I plug my RIO Carbon and it gets mounted after some seconds and all special characters are displayed correctly. 

Unfortunately I've no idea about scanners.

---

### Post by smarttaz on 2005-07-04
[QUOTE=rwabel]1. check that your system is completly on utf-8
2. mount the partitions, cdrom and stuff with utf-8
 
for example the cdrom:
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto,utf8 0 0
 
I hope it helps, let me know if it's working![/QUOTE]
 
YES, IT WORKS!
 
However, /etc/fstab is usually for:
1). Manually-mounted devices;
2). Overwriting of what "udev" will mount if nothing is found in /etc/fstab.
 
I mean, w/o mentioning (in my case) /dev/hdc and /dev/hdd with iocharset=utf8 will cause trouble for some international characters when udev will mount the CD-ROM. HOWEVER, in SuSE9.3 you don't need to have any entry in /etc/fstab for the CD-ROM and the DVD, and SuSE's configuration of udev will automatically mount them utf8!
 
How could this be done here?! I mean, "udev" should default to utf8!
 
R.

---

### Post by rwabel on 2005-07-04
[QUOTE=smarttaz]YES, IT WORKS!
 
However, /etc/fstab is usually for:
1). Manually-mounted devices;
2). Overwriting of what "udev" will mount if nothing is found in /etc/fstab.
 
I mean, w/o mentioning (in my case) /dev/hdc and /dev/hdd with iocharset=utf8 will cause trouble for some international characters when udev will mount the CD-ROM. HOWEVER, in SuSE9.3 you don't need to have any entry in /etc/fstab for the CD-ROM and the DVD, and SuSE's configuration of udev will automatically mount them utf8!
 
How could this be done here?! I mean, "udev" should default to utf8!
 
R.[/QUOTE]
 in ubuntu by default cdroms are in fstab. I don't know for suse. But as far as I know suse uses or has used automount for that case. Maybe they've also switched.

I think by default udev uses utf-8, but I could be wrong.

So far your international characters are working correctly now under ubuntu, right?

try asking for udev or automount in suse forums

---

### Post by smarttaz on 2005-07-04
[QUOTE=rwabel] 
So far your international characters are working correctly now under ubuntu, right?
[/QUOTE]
 
Yes! (with utf8 in fstab)
(but again, automount or not, utf8 is by default in suse)

---

### Post by Copter on 2005-07-07
Hi! I have also problems with locales. I have unistalled all polish packages and set locales to en_US. Now I have KDE in english and konsole (mc, and other stuff) in polish - ofc without polish sings :(. To get polish signs in openoffice I had to install uindows font - it shouldt be this way...

---

### Post by rwabel on 2005-07-07
[QUOTE=Copter]Hi! I have also problems with locales. I have unistalled all polish packages and set locales to en_US. Now I have KDE in english and konsole (mc, and other stuff) in polish - ofc without polish sings :(. To get polish signs in openoffice I had to install uindows font - it shouldt be this way...[/QUOTE]
 is it only a problem within openoffice? ofc?
You should have set locales to en_US.UTF-8

---

### Post by smarttaz on 2005-07-08
[QUOTE=rwabel]You should have set locales to en_US.UTF-8[/QUOTE]
 
Why should everybody use **AMERICAN** locale, folks?
He should be able and even **encouraged** to use **pl_PL.UTF-8**, if he wants to benefit of as much is available in Polish!
The "UTF-8" part is for supporting all possible characters (that's about the internationalization, remember?), what the hack?
**What kind of internationalization would be that in which everyone should set "American English"?**
Not Even Microsoft is not requiring that...

---

### Post by rwabel on 2005-07-08
[QUOTE=smarttaz]Why should everybody use **AMERICAN** locale, folks?
He should be able and even **encouraged** to use **pl_PL.UTF-8**, if he wants to benefit of as much is available in Polish!
The "UTF-8" part is for supporting all possible characters (that's about the internationalization, remember?), what the hack?
**What kind of internationalization would be that in which everyone should set "American English"?**
Not Even Microsoft is not requiring that...[/QUOTE]
 mhhh, maybe I'm wrong, but when you set them to pl_PL.UTF-8 your OS will be in polish! or am I wrong. I don't wanna have my linux in german, I prefer it in english. Correct me if I'm wrong

---

### Post by smarttaz on 2005-07-08
[QUOTE=rwabel]mhhh, maybe I'm wrong, but when you set them to pl_PL.UTF-8 your OS will be in polish! or am I wrong. I don't wanna have my linux in german, I prefer it in english. Correct me if I'm wrong[/QUOTE]
 
You're right.
But MAYBE the user who wants Polish characters would also like its Linux in Polish!
You, a German, might want your Linux in English. Fine. 
Me, a Romania, I certainly want my Linux in English. Fine.
But Internationalization means that people should be able to want the OS in their language, where available!
From my experience, French-speaking people always want their OS in French. 
The same for Spanish-speaking people and Spanish.
 
R.F.

---

### Post by rwabel on 2005-07-08
Your statement is correct. That's what internationalization is! I've just assumed he wants his OS in english, because he had en_US per default :-)

p.s. you are right, french people wants to 99% their OS in french, about spanish speaking people I didn't know.

For me it's just confusing, to use Linux in german or french. I was once on german Llinux OS....they've even translated mountpoint. Sometimes they just translate too much :grin:

---

