---
title: "Ubuntu for a Public Computer"
date: 2005-10-16
forum: Desktop Environments
---

### Post by EnderTheThird on 2005-10-16
I work at a rather small hotel, and we had an extra computer lying around that we put in the lobby so guests without laptops could use it to access the Internet with our high speed connection.  Windows XP is on there right now, so naturally it has been filled with a bunch of unnecessary crap since we got it set up (had difficulties getting the wireless to work while using a Guest account, so 90% of the time it's logged in as administrator).

Now I've been using Ubuntu more often at home, and with Breezy out now I would like to put that on there.  That way they can't install anything that they shouldn't be, and they can still use Firefox and OpenOffice to do everything they need to.  What I'm wondering is if any of you know of something I can use to occasionally wipe all temporary user files from the Home directory and reload it with a pre-configured set of files.  I would still like them to be able to download, save, edit, and send any files that they need to using the Desktop and/or Home folders, but I don't want to have to manually delete all of the files every day/week.

Would there be a simple script that I could make or you guys could give me that would wipe the Home directory before the user logs off/on every time and re-creates it with that preconfigured setup?

Hopefully you guys understood all of that and have an idea of what I'm asking.  If it doesn't make sense or if something's not clear, just let me know.  Thanks!

---

### Post by cwaldbieser on 2005-10-16
[QUOTE=EnderTheThird]I work at a rather small hotel, and we had an extra computer lying around that we put in the lobby so guests without laptops could use it to access the Internet with our high speed connection.  Windows XP is on there right now, so naturally it has been filled with a bunch of unnecessary crap since we got it set up (had difficulties getting the wireless to work while using a Guest account, so 90% of the time it's logged in as administrator).

Now I've been using Ubuntu more often at home, and with Breezy out now I would like to put that on there.  That way they can't install anything that they shouldn't be, and they can still use Firefox and OpenOffice to do everything they need to.  What I'm wondering is if any of you know of something I can use to occasionally wipe all temporary user files from the Home directory and reload it with a pre-configured set of files.  I would still like them to be able to download, save, edit, and send any files that they need to using the Desktop and/or Home folders, but I don't want to have to manually delete all of the files every day/week.

Would there be a simple script that I could make or you guys could give me that would wipe the Home directory before the user logs off/on every time and re-creates it with that preconfigured setup?

Hopefully you guys understood all of that and have an idea of what I'm asking.  If it doesn't make sense or if something's not clear, just let me know.  Thanks![/QUOTE]

I would think that these steps should work:
1) Create new user.  Set up home directory how you want it.  Configure the settings, etc.
2) archive the home directory with "tar" and put it somewhere safe that the guest user doesn't have write access.  Read access will be required.
3) I think "gnome-session" is the program that starts up a new Gnome session when a user logs on.  I think there is some sort of startup script that it runs before the session actually starts.  If not, you could do something like renaming "gnome-session" to "gnome-session-2" and creating a script called "gnome-session" that deletes the current $HOME directory and unpacks the tar archive in its place if (and only if!) $HOME == /home/guest.  This is the trickiest bit, and you should be comfortable working in the command line or have an alternate window manager set up, as if you mess it up, you probably won't be able to get back into Gnome to correct any mistakes.  The last line of the script would be:
```

exec gnome-session-2

```
to execute the original gnome-session program.

Not sure exactly details you need filled in, as I have no idea what your experience with basic shell scripting is.  If you need more help,   feel free to ask more specific questions.  Maybe someone else will have even written up a better script by the time I finish this reply!

---

### Post by EnderTheThird on 2005-10-17
I don't really have any experience with shell scripting.  I understand how they work, but that's about it.  I don't know the language nor the filesystem well enough to know what commands to use and where to put the script file so that it is executed correctly.  Thanks for the input, and if anyone else has something to add, please do so.

---

### Post by mgor on 2005-10-17
Advanced bash scripting guide is _really_ good for learning bash: 
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

oh, if you're running kubuntu this might be helpful:
[http://www.linuxcompatible.org/KIOSK_Admin_Tool_v0.5_released_s30591.html](http://www.linuxcompatible.org/KIOSK_Admin_Tool_v0.5_released_s30591.html)
kde has nice kiosk features.

i also found this about locking down gnome:
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-intro-gconf-overview.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-intro-gconf-overview.html)

---

### Post by stack445 on 2005-10-17
Ive been thinking about a .login and a .logout file. These file execute command either at login time or at logout time. You could actauly delete the content of the home folder ( execpt some file like the .login and .logout ) and copy a default home folder pre-set like you want. Ive been trying to do it on my machine ( with the help of the new login in system tools. Quite handy ) but did not manage to do it yet. Of course im not a jedi by anymean. 

If someone with a bit more experience could tell me if i'm looking in the right direction or not ? I do know that the .login and .logout are a bit more UNIX related than to linux

---

### Post by dabear on 2005-10-17
Here's how you could do it:

Make a guest user called «guest».
Make a script calling the «users» command, finding out if the user guest is logged in or not. If he/she is not logged in, wipe out the /home/guest directory. Offcourse, you would have to run this script in some kind of loop; may I suggest cron jobs?

---

### Post by cwaldbieser on 2005-10-18
[QUOTE=EnderTheThird]I don't really have any experience with shell scripting.  I understand how they work, but that's about it.  I don't know the language nor the filesystem well enough to know what commands to use and where to put the script file so that it is executed correctly.  Thanks for the input, and if anyone else has something to add, please do so.[/QUOTE]
Well you should be able to create the new user on your own.  I will assume it is named "guest" in these examples.  Once it is set up the way you want it, log in as your admin account and:
```

$ cd
$ mkdir guest_bkup
$ chmod u=rwx guest_bkup
$ chmod go=r guest_bkup
$ cd guest_bkup
$ tar --bzip2 -cvvf guest.tar.bz2 /home/guest

```
This will backup the entire home directory of the guest user to a tar archive that is compressed with bzip2.  The backup will be in your admin user's ~/guest_bkup folder.  The guest user can read this folder, but nothing else.

Now you need to create a script to restore the home directory.  Open your favorite editor and create a file called "restore_guest.sh" in ~/guest_bkup.  In it, paste the following (I assume your admin user is named "admin"-- this is not likely to be the case so you should change it):
```

#!/bin/bash

#Enter guest's home directory and erase all files.
cd /home/guest
rm -R *
#Enter home directory.
cd /home
#Restore archive into guest folder.
tar -xvvf /home/admin guest.tar.bz2

```
Make the script executable with
```

chmod ugo+x restore_guest.sh

```

You should be able to test the script at this point:
```

$ sudo su guest
$ cd
$ rm -R /home/guest/*
$ /home/admin/guest_bkup/restore_guest.sh

```
This changes your user to guest.  Then you change to guest's home folder and erase all the files in his home directory.  Then you try to run the script to restore it.

I haven't tested this script out myself, so it may be a bit buggy.  If you can get that much to work, I'll expalin how you can rig it so the restore script runs before each login.

---

