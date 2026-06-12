---
title: "gnome settings daemon error msg"
date: 2006-12-03
forum: Desktop Environments
---

### Post by petejuk on 2006-12-03
I am looking for some help with this error msg that shows on login. I have read other threads and added gnome-settings-daemon to the sessions menu but this message still displays:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

The last error message was:

There was an unknown activation error.

GNOME will still try to restart the Settings Daemon next time you log in."

As the session starts, it appears like it isn't going to run but then everything starts as normal. Is it possible it isn't starting early enough?

---

### Post by ponx on 2007-04-18
Hey,

I just started getting this error myself yesterday (can't remember if it was after an update or what)...

But yeah, when I log in the system seems to hang for a while (a good couple of minutes or so), then I guess something times-out coz then the Gnome desktop finally comes up.

Annoying thing is the error message box doesn't say what the problem is..?!

any ideas..?

(I'm running Feisty beta, up-to-date except for 2 upgrade manager updates that i haven't been arsed installing yet...)

ponx.

---

### Post by kdub432 on 2007-04-21
I'm also having this problem
Any ideas, anyone?

---

### Post by John Azelvandre on 2007-04-28
I am also having this identical problem on my vendor-installed edgy (6.10)  system on my brand-new LinuxCertified laptop.

As the previous posts have described, login to gnome is inordinately long (several minutes), then the gnome settings daemon error msg quoted above appears.

I also note that initial boot is rather longer than I would expect (several minutes).  I've installed all the security and recommended package updates, so my version of Edgy should be completely up to date.

A solution to this annoying little problem (and particularly the very slow boot and logins) would be great!

---

### Post by dpar on 2007-04-30
I started having this error this morning also.....anyone find a fix yet??

---

### Post by John Azelvandre on 2007-04-30
See my further posts on this error in this forum: [http://ubuntuforums.org/showthread.php?t=406054&page=3]("http://ubuntuforums.org/showthread.php?t=406054&page=3")

Maybe one of the suggestions there will help you. although nothing has worked for me yet.

---

### Post by dpar on 2007-04-30
John: I went to the post that you suggested and tryed the reinstall of gnome-control-center, and that seems to have done the trick for me. Hopefully it will last....lol. I hope you have better luck with yours. I'm using Feisty by the way.

---

### Post by John Azelvandre on 2007-05-03
unfortunately nothing has worked for me yet.  Anyone have any other ideas?

---

### Post by I-Built Computers Inc. on 2007-05-08
Working on the same exact problem. In the three  recent instances where we have seen this problem here, all three were AMD based systems. Swapping graphics cards/CPUs had no effect. Our next step is to try the alternate (text based, but easy) Ubuntu installation and see if that works.

---

### Post by John Azelvandre on 2007-05-08
I solved my problem by a completely fresh install of Feisty.  So, I'm not sure what the ultimate cause of the problem was.  Good luck.  I  used the regular graphical installer.  It worked fine.

---

