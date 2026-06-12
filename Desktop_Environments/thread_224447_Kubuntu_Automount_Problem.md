---
title: "Kubuntu Automount Problem"
date: 2006-07-28
forum: Desktop Environments
---

### Post by cypher35 on 2006-07-28
Alright, so the automount feature has never worked for me since I first started using kubuntu last november...  I was going to mess around with it and see if i could get it to work, but I figured i'd wait until Dapper comes out and maybe the problem would fix itself.  Well it hasn't, so now i'm going to try to do something about it...


Here's the issue.

I have a dvd drive linked to /dev/hdd.

When I insert a CD, everything goes the way it should...  The icon appears on the desktop with the appropriate name, i click on it, it opens konqueror to "**media:/hdd**", and the little "**mounting dev/hdd**" dialog comes up after which it shows the contents of the disk.


Now when i insert a DVD on the other hand, the disk appears on the desktop not as the name of the disk (as it does with cds), but with the name "DVD-ROM" instead.  When i double click the icon on the desktop, it goes to "media:/hdd" as expected, but gives me a "**Malformed URL**" error.  Additionally, if i hit refresh, type in the "media:/hdd" address manually, or try to access the drive by double-clicking on the DVD-ROM icon in the "media:/" folder yields a different dialog:
```

    Open 'media:/hdd'?
    Type: Blank DVD

[] _D_o not ask again
[ Save _A_s... ] [ _O_pen With... ] [ _C_ancel ]
```

The automount icons and 'media:/' urls act the same regardless of weather or not the disk is mounted (i have done so manually before to test this).  It will just continue saying malformed url or asking me what to do with a blank dvd.

This problem occurs on all dvd forms i've tried including udf and iso9660 dvd-roms and dvd-rs.

Konqueror or whatever app is behind the whole "media:/" folder resolution seems determined to believe that every dvd i enter is blank media or something.

The only workaround i have been able to perform has been to place a "link to device" on the desktop for '/dev/hdd' and just right-click and mount whenever something is entered.  This works, but i'd *much* rather have the automount work for me the way it should...



So, in the interests of debugging this problem I would like to know what exactly happens when i insert a disk into the drive.  I would assume that some command is envoked by the kernel to let a script of some sort know that a disk has been entered.  It must then try to mount/read it and fail miserably but neglect to give any sort of error message.

I would also like to know how exactly the 'media:/' folder is implemented.  Is it controlled by konqueror?  Is there anything i can do to control what drives show up in there?  How are these redirects handeled?  Obviously "media:/hdd" is not just a symlink to "dev/hdd" or it would have simply taken me to it.

Any help anyone could give would be greatly appreciated...

**EDIT:** '*sudo dmesg*' give me:
cdrom: This disc doesn't have any tracks I recognise!

every time a dvd is entered...  perhaps it's a driver issue?

---

### Post by orb9220 on 2006-07-28
Are you trying to open blank dvd's? there is nothing to open on a blank?

"Type: Blank DVD"  is what your drive is saying. You have to burn files to a blank before it can be accessed.

---

### Post by cypher35 on 2006-07-28
Alright, i'm not stupid...  Yes i'm trying to open non-blank dvds.  As i said in my first post, i've tried both dvdroms and dvdrs using both udf and iso9660 formats.

It seems to think that these dvds are blank even though they all have data on them.  And yes, i have checked to see that they work in my other computers as well.

---

### Post by NiksaVel on 2006-09-12
was this problem ever fixed... I just started having it a few days ago and noticed that there are quite a few posts on this topic... just search for "malformed url" in these forums...

---

### Post by CGW on 2006-12-04
I'm having the same issue with both CD's and DVD's on Kubuntu Edgy.

---

### Post by gemidjy on 2007-01-13
I can confirm this for Edgy and Dapper, but have to tell that it ain't *buntu issue, but general hal/udev issue that affects other distros too, such as Suse and Kanotix Linux (Tried and seen the problem persistant).

It is really PITA for new and unexperienced users :/

---

