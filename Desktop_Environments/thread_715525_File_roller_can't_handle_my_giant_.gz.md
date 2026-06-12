---
title: "File roller can't handle my giant .gz"
date: 2008-03-04
forum: Desktop Environments
---

### Post by clesage on 2008-03-04
Hi everyone,

I have a 23 GB .tar.gz on an external hard drive and I need to get 12 GB out of the archive and back onto my computer after a failed backup.

My /tmp folder (6 GB) isn't big enough to handle the job if I use File-roller. Ark tries to load the entire archive into the /tmp just by opening the archive! I think GUI interfaces are out of the question.

I'm trying to move it to /storage where I have 20 GB free. (not enough to extract the whole file.)

file-roller and ark can't do the job. I would do small sections at a time, except that file-roller takes an extremely long time to process the entire file, even if you just want to extract a few megs.

Does anyone have any suggestions for me to get these selected files out of the archive? I am not afraid of the command line, but I haven't found anything suitable yet.

Thanks a lot,
- sage

---

### Post by trey85stang on 2008-03-05
in the terminal you can change your temp path by using the following

export tmp=/where/you/want

you can list files in a tar archive by the following:

tar -t filename.tar.gz

you can exact specific directories or files by the following:

tar xzvf filename.tar.gz whatever.fileordirectory

---

### Post by clesage on 2008-03-05
Thanks trey85stang,

Unfortunately, that didn't solve the problem either.

Simply trying to list the files with -T overloaded my RAM and it failed.

Also, when I used your export command, it dumped a bunch of directories into my /storage directory. (things that weren't already in /tmp)

lib, games, cache, backups, lost+found, mail, packages, opt and many more. Any idea where all that came from? (I know it wasn't in /tmp, because I had been poking around /tmp the other day, and it wasn't from the .tar.gz because it's only old project files.)

---

