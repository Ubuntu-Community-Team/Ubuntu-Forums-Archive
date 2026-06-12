---
title: "Ubuntu Won't Boot! Help!"
date: 2009-04-22
forum: General Help
---

### Post by Jersey Legend on 2009-04-22
I was trying to see why mpd (music player daemon) wouldn't create a database if my files.  I set the symbolic link right, but then I realized that the permissions weren't set to write so I wanted to do this command in my Music directory

# chmod 744 [A-Z]* .

but instead did this

# chmod 744 [A-Z]* /

I realized immediately what I did and went straight to /.  Iwent to my / directory on my net book and compared permissions with my desktop, the machine i did the command above on.  Everything was the same so I went back and did the right command.

I then do this

# ls -l | less

and I get a weird pop up error, my wallpaper disappears and my icons all turn to red x's.  I go to shut down, but all the words have been replaced with [].

Now it doesn't restart.

I go to recovery mode and these have failed.

Start-stop-daemon: Unable to start /sbin/klogd: Permission denied (Permissions denied           [fail]

Starting avahi mDNS/DN-SD Daemon avahi-daemon [fail]

then it just sits there. When I press alt/ctrl/del I get one more fail

Stopping Music Player Daemon [fail]

but I removed it and it does not appear when i run ps aux

Help please! I'm gonna go to my prof tomorrow since he is a unix admin, and see if he can help, if no one can here

---

### Post by Yashiro on 2009-04-22
Repeat the command on / (# chmod 744 [A-Z]* /) but use 755.
This should probably get it working but you will need to fix up some stuff afterwards perhaps.

---

### Post by Jersey Legend on 2009-04-22
yea thanx man. I emailed my prof. and he sent me an email this morning saying basically the same. I'm gonna to go and do that when my roommate gets up

Aprreciate it.

---

