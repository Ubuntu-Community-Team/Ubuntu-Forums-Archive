---
title: "recommend dvd movie burning software"
date: 2009-05-27
forum: Desktop Environments
---

### Post by andrea000 on 2009-05-27
I recently converted a friend from windows to ubuntu she has
wine up with i tunes and now she is looking for dvd movie burning
software she has tried k3b with no luck.Could someone recommend
a really good and fast movie burning software for her.Thank you

---

### Post by Tibuda on 2009-05-27
[DeVeDe]("apt:devede") is simple, easy and good.

---

### Post by oldos2er on 2009-05-27
What's wrong with k3b?

---

### Post by Locutus_of_Borg on 2009-05-27
ffmpeg
mencoder
dvdauthor
mkisofs
cdrecord

these 5 programs will convert any video file into a dvd capable of being played on any standard dvd player

devede is kind of a frontend to all of these, but ive had a few issues with devede so i only use the commands now

say you have file.avi which is an illegally downloaded movie
run the following commands to produce a dvd with said movie on it
```

<put a blank dvd in your dvd drive>
mencoder -o out.avi -noidx -oac copy -ovc copy file.avi
ffmpeg -i out.avi -y -target ntsc-dvd -sameq -aspect 16:9 out.mpg
dvdauthor --title -o dvd -f out.mpg
dvdauthor -o dvd -T
mkisofs -dvd-video -o dvd.iso dvd/
cdrecord dev=/dev/sr0 dvd.iso
```

if the source file is not avi either convert it to avi with mencoder or modify the above

---

### Post by Locutus_of_Borg on 2009-05-27
> **oldos2er said:**
> What's wrong with k3b?
k3b is fine for burning stuff to disk, but it does not convert to dvd structure

---

### Post by deadlockedgamer on 2009-05-27
k3b can rip dvds great with menus and all you just need to find the libdvdcss2 in a .deb and install first

---

### Post by andrea000 on 2009-05-28
ok i found a dvd program called [ManDVD]("http://www.getdeb.net/app/ManDVD") it looks good
but when i was testing it the software gives me
a error that said two many frames would anyone 
know what this is and how to fix it.

---

### Post by Chronon on 2009-05-28
> **Locutus_of_Borg said:**
> say you have file.avi **which is an illegally downloaded movie** run the following commands to produce a dvd with said movie on it


I don't understand why that's relevant at all.

> **andrea000 said:**
> but when i was testing it the software gives me
a error that said two many frames
What's the exact error message?  After googling, I found a bunch of references to an error "Too many frames dropped", which seems to have something to do with setting too high of a max. video bitrate.  I don't know if this helps you or not.

---

### Post by andrea000 on 2009-06-01
just for the record there not illegally downloaded movie's
when i first posted the question i said i installed wine
and then itunes.But thank you to all of you who answered my 
question.I found a piece of software that makes k3b
work i didn't have it installed that is why i couldn't get
it to work.Dvd burning isn't supported by default.

---

