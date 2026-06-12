---
title: "Calling all gurus. Post your tips and tricks."
date: 2005-12-24
forum: Desktop Environments
---

### Post by ardchoille on 2005-12-24
** Calling all gurus **

I have become quite interested in command line use lately and I recently learned how to do the following:

```

tar -cjf /home/backups/`date +%Y%m%d`.user_backup.tar.bz2 /home/user
mkisofs -o /desired/path/to/filename.iso -R /path/to/source/dir
cdrecord dev=/dev/cdrom1 /path/to/backups.iso

```

The tar command makes a backup of my $HOME directory.
The mkisofs command makes an ISO file from a directory of files.
The cdrecord command burns an ISO file to CD.

If you tweak the paths for your own system, you can make a bash script out of some or all of the above commands and have a simple, yet powerful backup scheme without having to install gui apps.

This is one of the greatest things about Linux (other than the freedom), you can do some powerful things on the command line. I have been learning more and more about cli and this has made me wonder why I use so many gui apps.

Now I am wondering: What are your cli tips and tricks? Post them i this thread so we can all benefit from them :)

I wanna learn more !

---

### Post by briancurtin on 2005-12-24
there is a tips and tricks forum

---

### Post by ardchoille on 2005-12-24
[QUOTE=briancurtin]there is a tips and tricks forum[/QUOTE]
I didn't know about it. Ooops, sorry guys.

---

