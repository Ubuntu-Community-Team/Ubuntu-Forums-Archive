---
title: "How to edit ODT files from the command line"
date: 2007-04-01
forum: Desktop Environments
---

### Post by Al_maverick on 2007-04-01
Hi, I am looking for a way to edit my ODT files (kword documents) from the command line. Basically, I spend a lot of time off home, and I can connect to my PC through ssh. It would be nice if I could work on my home docs via SSH. I could download them and edit them locally, but I find it awkward.
Is there a program to do that? Perhaps a plugin for vim?

Thanks for the help
Regards
Al

---

### Post by mexlinux on 2007-04-02
Maybe not the answer you expect, but OASIS files are a collection of XML files compressed in zip.
Try opening one from ark (or any other archiver) and you will see the files, If you are familiar with XML, you might work in there, and then compress back....
Not the best option, but might work.....

Also, OASIS files are supportd by google docs, you might work there also...

---

### Post by Al_maverick on 2007-04-02
> **mexlinux said:**
> Maybe not the answer you expect, but OASIS files are a collection of XML files compressed in zip.
Try opening one from ark (or any other archiver) and you will see the files, If you are familiar with XML, you might work in there, and then compress back....
Not the best option, but might work.....

Also, OASIS files are supportd by google docs, you might work there also...

I was hoping that maybe vim or some other would have a way to edit the file without going through the whole unzip, edit, zip again.

Google docs might be an option, but since Im dealing with personal info, it aint much comfortable to have it on the web. I know the whole "Do No Evil" thing, but still...

---

### Post by Sencer on 2007-04-02
sshfs+fuse might also work for you. It lets you mount a directory you can access via ssh, as a folder on your local system. That way you can edit it with kword without having to manually download/upload it.

---

### Post by Al_maverick on 2007-04-14
The thing is I usually access my files from a crappy 98. I was wondering if there was something like a CLI word processor I could run through SSH. 
(something like the old DOS Works but for ODT comes to mind) :D

---

### Post by sas on 2007-04-14
> **Al_maverick said:**
> I was hoping that maybe vim or some other would have a way to edit the file without going through the whole unzip, edit, zip again.

You could write a small shell script that unzips the file to a temporary one, vi's the temporary file, then when you quit vi, zips up the temporary file overwriting the old one and then deletes the temp one.

The script would probably be less characters than this post for a quick and dirty version.

---

