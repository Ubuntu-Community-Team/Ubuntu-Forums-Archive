---
title: "login loop"
date: 2009-05-27
forum: General Help
---

### Post by Klipstraat on 2009-05-27
Hi all

I am running Jaunty - has been working fine up until recently.
Something went awry last week and I am unable to solve this problem.

When I boot I am unable to get past the gui login - even with my correct password the system just loops back to the login. I can get a console login and I can see my home dir - it is still intact. But I cannot run the xserver - err msg indicates a broken xconfig.

I have had this problem before - the solution revolved around the  removal/renaming of the following files : 

.kde to .kde_old
.Xauthority
.sudo-as-admin-successful
.xsession-errors
.local

and .serverauth.(number) - (a few files)

This time none of these solutions (search login loop in forums) has worked.

The problem seems to be related to my Xconfig and initializing the Xserver.

Does anyone have a solution ? / Does this sound familiar to anyone?

I can use the live CD to get a gui but not if I boot from my internal drive.

I have tried a reinstall but the problem remains.

Thanks in advance

---

### Post by ctav01 on 2009-06-13
Sorry for piggybacking but I'm having the same problem...

---

### Post by ctav01 on 2009-06-14
Not sure what fixed it for me.  I ran through all of the recovery menu fixes and tried to reinstall kdm (when apt-get tells you that you already have the latest version, is there an option to reinstall anyway?).

Turns out I had run out of free space on the drive so nothing was working until I freed up some space.  Any one of the fixes might have done it for me.

---

### Post by Matt Damon on 2009-08-31
Same problem, caused after a system update.  Apparently my drive space was used up, proven when I took the option of logging in via the console, doing a df (100% full!) and deleting some of the files on my desktop.

Now that i've got the desktop back up, it's time to learn how to do a clean up of old files and packages...

---

### Post by Matt Damon on 2009-08-31
hah, 

sudo apt-get clean

---

### Post by Matt Damon on 2009-08-31
and because I love replying to myself...

[http://ubuntuforums.org/showthread.php?t=1122670&highlight=disk+full+clean+packages](http://ubuntuforums.org/showthread.php?t=1122670&highlight=disk+full+clean+packages)

---

