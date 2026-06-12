---
title: "Directory Structure"
date: 2005-12-13
forum: Desktop Environments
---

### Post by dwanders on 2005-12-13
Could some one post (or point me to) a listing of the Ubuntu direcotry structure? Something like:

/			Root
|---root		The home directory for the root user
|---home	     Contains the user's home directories
|    |----user1	      Users include many services as listed here
|    |----user2
|
etc...

---

### Post by earobinson on 2005-12-13
like this? [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)
(I found this go googling (linux Directory Structure))

---

### Post by 23meg on 2005-12-13
Check these out for a start:

[http://www.builderau.com.au/program/work/soa/10_things_you_should_know_about_every_Linux_installation/0,39024650,39219801,00.htm](http://www.builderau.com.au/program/work/soa/10_things_you_should_know_about_every_Linux_installation/0,39024650,39219801,00.htm)
[http://www.linuxchix.org/content/courses/filesystem/Lesson1.html](http://www.linuxchix.org/content/courses/filesystem/Lesson1.html)
[http://www.aleph1.co.uk/armlinux/book/x2654.html](http://www.aleph1.co.uk/armlinux/book/x2654.html)
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

---

### Post by dwanders on 2005-12-13
Yes, all those links are very nice for a generic Linux/Unix file sytem, but not specific to Ubuntu's. I would like to know if there is a specific layout for the Ubuntu system? Having a list is really all I would like to have, but it would be nice to have "we put this here for this reason" etc... Some one, some where must know the structure, and there must be a reason for the way Ubuntu decided to do thier layout just a smidge different than say Suse, or RedHat - and way different from Solaris etc...

---

### Post by earobinson on 2005-12-13
could you not just browse from / and look at the links provided for discryptions?

---

### Post by tomwell on 2005-12-13
Earobinson, But isnt it so much easier to have someone else do the work for ya??? LMAO!!! ;o)

Seriously all those links explain everything ya need....

Peace

T

ps: Sorry am being goofy the Jack Daniels is at it again... :oD

---

### Post by earobinson on 2005-12-13
Im a rum and coke man my self.

Well it would be nice to have exactly what the OP asked for i am unable to find it via google.

---

### Post by leech on 2005-12-13
[QUOTE=dwanders]Yes, all those links are very nice for a generic Linux/Unix file sytem, but not specific to Ubuntu's. I would like to know if there is a specific layout for the Ubuntu system? Having a list is really all I would like to have, but it would be nice to have "we put this here for this reason" etc... Some one, some where must know the structure, and there must be a reason for the way Ubuntu decided to do thier layout just a smidge different than say Suse, or RedHat - and way different from Solaris etc...[/QUOTE]

I don't think Ubuntu does anything specific.  I know it's no different than Debian's.  Linux distributions for the most part all comply with the standard (LSB I think may have something to do with this).  So any of those links should pretty much describe it.

Leech

---

### Post by tomwell on 2005-12-13
[QUOTE=earobinson]Im a rum and coke man my self.

Well it would be nice to have exactly what the OP asked for i am unable to find it via google.[/QUOTE]

Google is a bitch!! I can hardly find anything using it... LMFAO!!!! ;o)

I love Rum And coke too, I lived in madagsacar for 1 year and i got soooo drunk like every weekend on rum and coke.... lmao was sooo nice!!!

Jack Daniels and coke now though...

Peace

Tom

---

### Post by dwanders on 2005-12-14
[QUOTE=tomwell]Earobinson, But isnt it so much easier to have someone else do the work for ya??? LMAO!!! ;o)

Seriously all those links explain everything ya need....[/QUOTE]

Yes indeed it is much easier to let someone else do it - but what I needed you have provided (I will take the information from the link and map it to match what the system has) I was unsure if it was that simple or not. 
Thanks for the information. 
I have always been partial to Beam & Coke.

---

### Post by dwanders on 2005-12-14
I believe that I have managed to link up most of the directories on the installed Ubuntu system to something from those links given above except for the following directories:

|---debootstrap  ???
|---initrd              ???
|---lost+found    ???
|---media            ???
|---opt                 ???
|---srv                  ???
|---sys                 ???
|---usr
|    |
|    |----games      ???
|    |----lib64         ???
|    |----share        ???
|    |----src            ???
|---var
|    |----backups    ???
|    |----cache        ???
|    |----games      ???
|    |----opt            ???

could someone let me know what these are used for?

---

### Post by carlosqueso on 2005-12-14
I know only a few....
lost+found: if weird stuff happens to your file system, what it can save goes here
media: where you will mount drives
var/cache: caches for various programs (i.e. /var/cache/apt/archives is used for storing debs downloaded by apts)
usr/src: holds source code for stuff

These are all I know...and it's either Maker's Mark and Coke or George Dickle and Coke for me...or, if I can get it, some good old straight Becherovka :-D

---

### Post by jobezone on 2005-12-14
|---opt -> Where usually people install self-compiled or external software
|---usr
| |
| |----games ->where games binaries are installed on the system

---

