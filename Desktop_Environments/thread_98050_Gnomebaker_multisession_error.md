---
title: "Gnomebaker multisession error"
date: 2005-12-02
forum: Desktop Environments
---

### Post by rem on 2005-12-02
Hello everyone,

I have problems with Gnomebaker – multisession burning. I did a search on the forum about this matter but nothing was helpful. I am able to burn, erase CDs but no multisession :(
When I'm trying to import a previous session, I'm always getting this error:

Error getting session information.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Drive needs to reload the media to return to proper status.
cdrecord: Success. read track info: scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 28
cmd finished after 0.000s timeout 240s
cdrecord: Cannot get next writable address for 'invisible' track.
cdrecord: This means that we are checking recorded media.
cdrecord: This media cannot be written in streaming mode anymore.
cdrecord: If you like to write to 'preformatted' RW media, try to blank the media first.
cdrecord: Cannot read first writable address

Also, I tried some other burning software like k3b but I'm a Gnome fan and I'm not really comfortable with KDE apps since there's Gnomebaker which I think would be the best choice it there would be multisession burning too ... Out of curiosity I tried to compile other CD/DVD burning apps from source but for some reason, my installed libraries couldn't be found (because of some wrong path). I'm very sure I have installed all the dependences since I was able to compile from source other software. Now I'm sure I'll stick with Gnomebaker but I have tons of other libraries that I'm not very sure I'll ever use. How can I find out which libs are safe to be removed or is it OK to load my PC with “failed compilation attempts” leftovers? 

Thanks a lot and sorry for this multi-subjects thread.

---

### Post by teaker1s on 2005-12-02
look [here]("http://ubuntuforums.org/showthread.php?t=93020")

---

### Post by rem on 2005-12-02
[QUOTE=teaker1s]look [here]("http://ubuntuforums.org/showthread.php?t=93020")[/QUOTE]

I already told that I did searched on the forums and nothing was helpful. The thread you pointed me at was the first one I tried with no success. But thanks anyway, this kind of help I'm getting always when I write to this forum... is it just me?

---

### Post by rem on 2005-12-02
I'm only trying to switch to Ubuntu from Windows for good... I'm using it since Hoary with great success. By following up some very helpful threads from this forum, I managed to get almost anything I wanted from my system and I'm very happy because I didn't started windows for a couple of weeks now but I really need Gnombaker working at fullest if possible. Please, is anyone here that could help?
Thank you...

---

### Post by Peej on 2005-12-05
Rem, I think it might be that the CD you are trying to write to was not started as a multisession CD. I had the same problem as you, a disk I'd burnt wouldn't let me add anything new. So I tried an old multisession CD I had created using Nero and GnomeBaker detected the disk and loaded the existing session. So I created a new CD, but when burning it I changed the "mode" from "default" to "tao" (track at once). Once done, I could then use the import session button to load the multisession disk. I hope this helps.

---

### Post by rem on 2005-12-06
[QUOTE=Peej]Rem, I think it might be that the CD you are trying to write to was not started as a multisession CD. I had the same problem as you, a disk I'd burnt wouldn't let me add anything new. So I tried an old multisession CD I had created using Nero and GnomeBaker detected the disk and loaded the existing session. So I created a new CD, but when burning it I changed the "mode" from "default" to "tao" (track at once). Once done, I could then use the import session button to load the multisession disk. I hope this helps.[/QUOTE]

Thanks a lot Peej for your answer. Here's the thing: I spoiled a couple of blanks at first then I took one of my older multiesessioned CD burned with Nero (just like you did) but couldn't import the session within GnomeBaker. I have some kernell  related error I guess, don't think it has anything to do with the CD itself. So, after some more searching on www, I found [Graveman]("http://graveman.tuxfamily.org/") which is working GREAT in TAO mode :). So, I have a great app for burning CDs now with multiessesion, copy at once, ISO images and all.

---

### Post by tanari on 2005-12-16
what's the difference between DAO and TAO? And what is RAW mode?

---

### Post by rem on 2005-12-16
I don't know to much about that either and I guess I couldn't explain it better than [this guy here]("http://linuxgazette.net/issue31/tag_cdr.html") :)

---

