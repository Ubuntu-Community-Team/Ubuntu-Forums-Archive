---
title: "Mount CD/DVD Returns &quot;No medium found&quot;"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Synnergy on 2005-06-15
I've got almost a fresh install of Kubuntu 5.04 (installed just a couple of days ago) and I'm trying to load some of my data that I backed up to DVD.  When entering the DVD, I get no auto-mount or icon for the drive, and when I try to manually mount it, I got the message stating "No medium found"

I know that other users have had this issue, because there are numerous posts littered throughout the forums; but I haven't found anyone that has answered the question.  Besides "are you sure the disk is good"  - which I am, as I used these same discs 2 weeks ago.  I also cannot read the official pressed Ubuntu discs I've got, (or any other for that matter).  Google brings back nothing but old posts for kernels in past days on a level that I do not understand :)  (BTW - seperate question, but anyone know a syntax for limiting Google reslts to pages created/modified since a date?)

Anyway - someone, please help!  And I swear, if I get an working solution here, I'll go back and link to all the other posts out there to try and eliminate the problem!

---

### Post by rachii on 2005-06-16
what is listed in /etc/fstab?

---

### Post by Synnergy on 2005-06-16
Sorry about that, I guess I got carried away in my message and forgot a few things :/  I'm at work now, so I don't have what it's set with.. I did get the following entries from a post here on the forums about auto-mounting:

/dev/hdc        /media/Rcd	auto	ro,user,noauto,exec  0       0
/dev/hdd        /media/Wcd	auto	ro,user,noauto,exec  0       0

([http://ubuntuforums.org/showthread.php?t=39591&highlight=automount](http://ubuntuforums.org/showthread.php?t=39591&highlight=automount))

I tried these two entries, I had to change Rcd and Wcd to cdrom0 and cdrom1 though, and my default entries were about the same, except for the auto detection type.  I believe it's set to ISO9660 instead (if I remember the numbers correctly).

I'll get the output from dmesg when I get home, but if I remember there was a generic error at the end stating something around cd not found.  It didn't look like a lot of information, but I'll get a post on here tonight.

---

### Post by themoddingden on 2005-06-16
hi;
well my thought are that if it will not read the pressed cd's is that the drive is messed up ????

Have you tried other cd's too like a 98 cd 
or a disked burned with nero???
maybe the drive cable is not in all the way check cables and reboot
do you have another cd rom drive???
make sure ones set to master and the other to slave if they are on the same channel/ide cable.
have you updated the drives firmware maybe it got a bad flash???
when did this start after a software install of program tweak???
if after a program install try removing it .
can you view the cd you burned in another computer???

---

### Post by desdinova on 2005-06-16
Try mounting it as fs type udf perhaps?

---

### Post by Synnergy on 2005-06-16
Ok, here's the original lines in my fstab

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

I believe this takes care of the udf suggestion since those didn't work either.  Although, if I need to change something else, please let me know.

For the other suggestions posted, I can assure that the drive works because I just loaded Kubuntu using it.  I was able to access this exact DVD using Arch a few days ago.  I have not opened the case, moved the computer, or installed any applications since having the drive work in Kubuntu (which it hasn't since I installed.  I can boot the live CD using this drive as well, so I'm sure that it is working fine.

The DVD was burned using K3b on Mandrake 10.0 and after switching both mine, and my brothers machine to Kubuntu, we've got 3 DVD drives that we cannot open this DVD, surely not all of them have gone bad in the last week.

Please keep up the suggestions, I'll continue looking over here and trying different things.  If I get any more info I'll be sure to update.  Thanks!

---

### Post by haaglin on 2005-06-17
i have almost the same problem, cd's or dvd's never automount anymore. i have to manually mount it, but that works for me though, but i wish they could automount. hope you figure out what the problem is.

---

### Post by rajaiskandarshah on 2005-06-27
i have the same problem too. i am using ubuntu 5.04 (the gnome version). now my cd, card reader, and external hard disk will not auto mount. trying to auto mount the cd gives me a 'no medium' error as well. 

the last time it was ok, it was before i installed kig (a kde geometrical application) and its dependencies. after installing that i did note an error about missing fonts. i guess this is a kde problem ?

tried uninstalling kig and the dependencies, but no luck still.


updates: fixed it ! but i think it only works for ubuntu (gnome). all i did was completely removed gnome-volume-manager (this will remove the config files as well), then installed gnome-volume-manager back. ubuntu uses a combination of hal, pmount, and gnome-volume-manager.

---

