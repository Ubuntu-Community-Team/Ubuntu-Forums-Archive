---
title: "how to burn long filenames with brasero?"
date: 2007-08-28
forum: Desktop Environments
---

### Post by Krijk on 2007-08-28
Is it possible to burn long file names windows style with Brasero?

I have to burn a DVD with windows-software which contain long filenames and spaces. It is not possible to rename these, because the software won't install.
Unfortunately brasero is the only program I know of that allows my DVD-burner to burn DVD's. Other programs simple refuse to accept empty DVD's.

---

### Post by gOLdenHaWK3D on 2007-10-24
Select "Increase compatibility with Windows systems" :)

---

### Post by moronimontoya on 2007-10-24
I burned a program yesterday to a data CD with Brasero, then I put the CD into a Windows XP machine and it had nothing in it.  

I wasn't aware of the "make compatible with windows" option ..  where is that at?  is there anything else I need to do to the brasero config so my resulting CDs can be viewed and played in windows?  

thanks

---

### Post by Ux64 on 2007-11-26
I tried.

Brasero said, file not found when I tried to burn file with name "tämä on testi öökköset ja ååkköset.txt".

Altough I can read Joliet disks with utf-8 charset, I can't write those, for some reason. Maybe Brasero is the reason.

Solution, create 7-zip archive with stuff and transfer it. It's quite universal solution. Out can have directory structures, huge files, small files what ever. You'll simply get nice container which is right sized too. (In case needed, split archives)

Without Windows mode it seems to trunc filenames to very classic 8.3 format.

---

### Post by Ux64 on 2008-04-20
There are a lot of problems with Brasero. Unfortunately. Just today I found out that one of disk didn't show files on Windows machine even that windows compability mode was selected.

That 64 char limit is also quite annoying. Isn't there a better solution out there?

I could compress before burning, but that makes reliability even worse.

---

### Post by Ux64 on 2008-05-05
What that "Increase compatibility with Windows systems" actually does? Why isn't default disk UDF disk as it should be? Then there shouldn't be any problems?

Many documents recommend ignoring ISO9660+Joliet because UDF is way better.

---

