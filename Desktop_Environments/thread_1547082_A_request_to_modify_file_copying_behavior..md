---
title: "A request to modify file copying behavior."
date: 2010-08-06
forum: Desktop Environments
---

### Post by mango42 on 2010-08-06
Hi,

Not sure whether this is the right place but a situation occurred yesterday that made me think about ergonomics in file copying behaviour using nautilus under Gnome.

I was rescuing ~300Gb of data off a failing 'My Book' external USB drive; I did it main folder by folder so as to note whether the drive was still copying without corruption (it was, yipee!).

One folder however was around 180Gb and I was copying from one USB drive to another and time estimate was around 2.5hours.

Okay, I finally come to the ergonomics bit for those who haven't already dozed off ;-)

I left the machine to chunter away, thinking I had around 2 hours before I needed to check it but when I did I found a dialog awaiting me, held up about half way through, asking whether I wanted to retry copying a failed file. So, would it not be better (at least from a user's point of view!) just to internally flag failed files and carry on with the rest, THEN put up a dialog at the end of the operation showing which files failed and whether to [Skip | Retry | Repair <joke!> | Delete] ?

I hope this request will be taken in the manner intended - further modest but true glory for the vocational coder philosophy.

Thanks for reading.

---

### Post by Zorgoth on 2010-08-06
I recommend that instead you use the terminal for a long copy like that if you don't want to be prompted -

cp -rf is the command you want, read "man cp" for details.

---

### Post by mango42 on 2010-08-06
Thank you **Zorgoth** for the 'fast route' but how do I link the two USB drives together from the command line to allow use of **cp** successfully? 

GUI's are so much more convenient for general users, IMHO. :)

---

### Post by Zorgoth on 2010-08-06
The USB drives can be found in the directory /media.

---

### Post by KdotJ on 2010-08-06
**mango42** I do like your idea. I too have been in a similar situation. I am currently working on a backup program myself at the moment and will have a think about this idea.

---

### Post by mango42 on 2010-08-18
Thank you Zorgoth for helping a relative newcomer ;-)

Is there a single/central command for finding out what the OS calls every single piece of user addressable hardware?

@**KdotJ** Great. Could it be a preferences option in Nautilus, perhaps?

---

### Post by endotherm on 2010-08-18
it's a good idea, but I think there are deeper technical implications that may result in the behavior you mention. for instance, you want to copy a folder full of files to a location, so you copy/paste them to another location. however there is already a folder by the dest name in the destination location, so you recieve a prompt. do you really want to try to copy the files that go in the dir, before the dir exists? I think situations like this, are why they choose to make the copy commands fire in series, and to do it in order. 

there is likely some kind of robust/bulk copy utility that would behave as you describe when possible. if you find one, let us know.

---

