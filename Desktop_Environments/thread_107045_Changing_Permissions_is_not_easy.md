---
title: "Changing Permissions is not easy"
date: 2005-12-22
forum: Desktop Environments
---

### Post by dinkleburger on 2005-12-22
Hello

Coming across from XP where i am used to clicking around doing things
i find it impossible to write to my cd burner its read only and i cant set permissions like i could in Mandrake

I think the Root Admin was a mistake to leave it out......

At least we should have been given a choice on installation to include the Root Permission changing system option Yes/No

i rather remember a passord than try and learn heaps of commands...

is there some software out there that i can use to change permissions as easy as point and clicking like in mandrake and XP

if not can some one give me a step by step instruction how to make my cd burner have write permissions..

Kind regards DB

PS this should be noted for the developers too
apart from that i like the OS

i went back to XP for a week to do things i cant do on here YET!!!!
I know i sound annoyed but the OS most are comming from doesnt require much typing in commands....

Merry Xmas to All;)

---

### Post by localzuk on 2005-12-22
Hi,

Please could you tell us how you are trying to burn a cd as this may lead to an answer to your problem.

---

### Post by 23meg on 2005-12-22
To change file permissions GUI-wise, hit alt+f2 and type ```
gksudo nautilus
```and you'll have a superuser mode Nautilus where you can change ownerships and permissions of files you don't own however you like (right click, "Properties", "Permissions").

To run your CD writing app with root privileges, append "sudo" (or "gksudo" if using alt+f2) to the command you use to launch it.

---

### Post by dinkleburger on 2005-12-22
Thankyou 23meg
I wrote a folder with a app to the cd....

This is strange thing happening

1: First i put CD in the drive which has 500 meg of free space
2: I selet burn to cd
    and get error message saying i must insert a blank cd or re writable

3: So i put a brand new balnk cd in and copy 2 megs
4: Now i want to add some more to the same cd,   but the error message keeps popping up telling me to add a blank or re writable

it seems like the software sees some file and assumes the disk is full...

anyone familiar with this behaviour

btw thanks for the Permissions Tip.... i have to write that down in my pad that is cool way to change permissions. i like it very much..:razz:

---

### Post by GrumpyBob on 2005-12-22
Is "multisession" an option with the burner you are using?

Robert

---

### Post by localzuk on 2005-12-22
This is due to the cd writing app 'locking' or 'finalising' the cd when it has finished. You should be able, in most writing apps, to choose multisession/'don't finalise' as an option.

---

### Post by fordfan753 on 2005-12-22
I'm a GNOME fan, but everyone wanting to burn a CD in Linux should be introduced to K3B, the second best KDE application, and the easiest to use, full featured Linux burning program.

---

### Post by ACK!! on 2005-12-22
[QUOTE=fordfan753]I'm a GNOME fan, but everyone wanting to burn a CD in Linux should be introduced to K3B, the second best KDE application, and the easiest to use, full featured Linux burning program.[/QUOTE]

Gnomebaker

Features:

* Create audio cds from existing wavs, mp3, flac and oggs
* Import M3u and pls audio playlists.
* Create data cds
* Blank rewritable disks
* Copy data cds
* Copy audio cds
* Burn existing cd iso images
* Can burn via scsi and atapi on linux kernels 2.4 and 2.6. Basically if cdrecord works then GnomeBaker will work.
* Drag and drop to create data cds (including DnD to and from nautilus)
* Integrate with gconf for storage of application settings
* Burn DVDs.
* Supports multisession burning
* Blank/Format DVDs
* Burn Cue/Bin files
* Burn data cds on the fly

Notice the multisession line.  I am not busting on the KDE (AT ALL!!!) but you should be able to do this in gnome as well.

---

### Post by fordfan753 on 2005-12-22
I have used gnomebaker a little, and I did find it a very good program, but whenever I have cd writing problems K3B seems to have some fix. On first install it can change permissions of your CD drives to burn as normal user, which I think is good. I'm not sure if you can do this on gnomebaker, because it's been a while since I used it. I also used gtoaster a few times, that seemed ok.

---

### Post by Griff on 2005-12-22
[QUOTE=fordfan753]I'm a GNOME fan, but everyone wanting to burn a CD in Linux should be introduced to K3B, the second best KDE application, and the easiest to use, full featured Linux burning program.[/QUOTE]
I prefer Gnome as well, but you don't need KDE to run K3B.  It runs fine in Gnome.  It's what I use all the time.  BTW, what would you say is the best KDE app? (since you mention K3B being 2nd :))

---

### Post by fordfan753 on 2005-12-22
I love amaroK, it's definitely my favourite KDE application. It's just a great music player, that looks good and gets the job done, I especially like the built-in lyrics browser, and built-in audioscrobbler/last.fm client. It also has a way of burning audio CDs by using K3B, which I think is pretty neat.

---

### Post by Griff on 2005-12-22
[QUOTE=fordfan753]I love amaroK, it's definitely my favourite KDE application. It's just a great music player, that looks good and gets the job done, I especially like the built-in lyrics browser, and built-in audioscrobbler/last.fm client. It also has a way of burning audio CDs by using K3B, which I think is pretty neat.[/QUOTE]
Hmm.  I wonder if amaroK will run in Gnome...  Only one way to find out. ;)

---

### Post by Griff on 2005-12-22
It does.  And very nicely I might add.  Might become one of my fav apps.  :cool:

---

### Post by fordfan753 on 2005-12-22
[QUOTE=Griff]It does.  And very nicely I might add.  Might become one of my fav apps.  :cool:[/QUOTE]

:D

It's worth a try...I use GNOME, but I always install qt and kdelibs just so I can get amarok and k3b, because they both rule.

Oh, and btw, don't worry if lyrics fetching isn't working in amaroK, the site where the lyrics come from changed it's formatting or something, anyway, the amaroK devs have found a fix, and lyrics will work again in the next release or amaroK.

---

