---
title: "help mirroring a directory/rsync ?'s"
date: 2008-12-08
forum: General Help
---

### Post by mma8x on 2008-12-08
basically, i'd like certain directories on my desktop and laptop to be sync'ed, so that each would act as a backup for the other.  i'm doing that with a daily cron job via rsync, but had a couple of questions:

1.  do i have to run 2 rsync commands to get each directory to copy to the other? eg, rsync -avzu desktop:/home/Documents/ /laptophome/Documents, and also rsync -avzu /laptophome/Documents/ desktop:/home/Documents, or is there one command that does the same thing?
2.  what exactly is the update (-u) option?  i'm not clear if that should or should not be included to prevent overwriting a newer file?
3.  is there a better way to do this that i don't know about?

---

### Post by snova on 2008-12-08
1. I think if you did this, the second version would overwrite the first.

2. " -u, --update                skip files that are newer on the receiver"

From what I can tell, it only copies files that haven't been modified on the target directory. So if you changed both, nothing would happen.

3. Due to 1, I would perhaps suggest a version control system? A VCS will have merging capabilities. It won't work with binary files (OpenOffice, images, etc.) but it will at least tell you where files are in conflict and remind you to fix the problem.

I personally like Bazaar... But there may well be a way to do it with rsync.

---

### Post by mma8x on 2008-12-08
> 1. I think if you did this, the second version would overwrite the first.

it would only overwrite the first if there were changes, i think.  for instance, if i put foo.txt on the laptop, and foobar.txt on the desktop, then the first command should copy foobar to the laptop, and the second would copy foo to the desktop.

> 2. " -u, --update                skip files that are newer on the receiver"

From what I can tell, it only copies files that haven't been modified on the target directory. So if you changed both, nothing would happen.

i kind of thought that update would/should prevent any problems with overwriting; that is, if i modified a file on the destination (let's say desktop) computer (foo.txt) it would now have a new timestamp.  foo.txt on the source (laptop) would now be older, and wouldn't copy.  however, when i switched source/destination, the newer version should copy to the original source (laptop).  i think.

> 3. Due to 1, I would perhaps suggest a version control system? A VCS will have merging capabilities. It won't work with binary files (OpenOffice, images, etc.) but it will at least tell you where files are in conflict and remind you to fix the problem.

unfortunately, most of the files that i care about (pictures, music, documents) are binary, so this doesn't appear to be an option.

---

### Post by snova on 2008-12-08
> **mma8x said:**
> unfortunately, most of the files that i care about (pictures, music, documents) are binary, so this doesn't appear to be an option.

It would also store all of the history, which is overkill...

---

### Post by amac777 on 2008-12-08
I haven't used it yet myself, but I've seen several people using a program called Unison to do synchronization between folders on different computer. Here is a quick introduction / tutorial:

[http://www.ubuntugeek.com/unison-file-synchronization-tool.html](http://www.ubuntugeek.com/unison-file-synchronization-tool.html)

Note that the comments say the one thing you have to make sure is you run the same version of Unison on both computers or else they won't connect.

There are also some other people on these forums doing similar things. Search for "folder synchronization" etc to find them.

---

### Post by Trevster on 2008-12-08
There is a product called dropbox that I find very useful. It's not open source but works well with ubuntu. The free version limits you to 2gb though.

[http://www.getdropbox.com/]("http://www.getdropbox.com/")

---

### Post by mma8x on 2008-12-09
> **amac777 said:**
> I haven't used it yet myself, but I've seen several people using a program called Unison to do synchronization between folders on different computer. Here is a quick introduction / tutorial:

[http://www.ubuntugeek.com/unison-file-synchronization-tool.html](http://www.ubuntugeek.com/unison-file-synchronization-tool.html)

Note that the comments say the one thing you have to make sure is you run the same version of Unison on both computers or else they won't connect.

There are also some other people on these forums doing similar things. Search for "folder synchronization" etc to find them.

thanks--this is exactly what i was looking for.  pretty sweet, and apparently it will work across windows boxes as well.  i've tried it a bit, and it works well.  only problem is it requires user input if it detects a conflict.  i'll need to play around with the command line options so that i can use it as a cron job.

---

