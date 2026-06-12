---
title: "Desperate: hard disk completely screwed"
date: 2009-04-27
forum: General Help
---

### Post by shepsii on 2009-04-27
Hi,

I use linux to host an svn server and to code my website which is going live on Friday.

Today, a friend asked me to do some video editing. I installed kino and left the tape recording to my external hard disk. When I came back the computer had froze. When I turned it off and rebooted, it starts loading linux, brings up the first graphic with the loading screen, then goes to a "built-in prompt". This is very limited and navigating around the filesystem it appears nothing is there.

I am guessing that what has happened is that kino has actually recorded to my hard disk, not the external, and taken up all the space which has just completely screwed it.

I have a ubuntu disk which I have used to boot the pc. It refuses to mount my hard disk, giving me a message just listing all the possible errors with hard disks (bad sectors or wrong fs type, bad option, bad superblock, missing codepage or other errors etc).

Please please can someone offer me some advice. Is there anything I can do to find out more about what has happened? Are there any programs I can run to try to fix the disk? How would I run them?

I'm really desperate here - I've spent 8 months out of a job making this website and the last version I have backed up is from 2 weeks ago and has major features missing.

---

### Post by Niniel on 2009-04-27
If you have disk errors, this [thread]("http://ubuntuforums.org/showthread.php?t=365714") might help you. 

If you just think your disk is full, you could try to delete the file/s that were created by Kino.
I would navigate to my home directory and do "ls -sSr" to list files with file sizes (s), sorted by file size (S) and with the largest files last (r) (so you'll see them and not tons of small fry that you are not interested in). I would also check my Desktop folder, the Video directory and the system /tmp directory. 
"rm file name" deletes files.
"ls --help" lists more switches for the ls command.

---

