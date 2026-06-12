---
title: "Scripting to RUN AS another user?"
date: 2009-01-16
forum: General Help
---

### Post by Kissell on 2009-01-16
So, I've created some /etc/init.d scripts which run some daemons at boot-up, so that the server can be doing things without someone needing to login when its rebooted...

but, i've got a problem with this...  if the auto-started daemon kicks of process, like it moves a file to another volume, then that file is writable by everyone because it has the permissions set for the root user...  that's not cool...  see the root user creates the file automatically via this process, and then moves the file when it's done, so the result is that the user's file has the wrong rights...  my daemon doesn't have any ability to change the rights, so i've been doing a non-elegant work around by scheduling a cron job that routinely goes around setting permissions correctly...  but this isn't ideal, for one it prevents hard drives from going into standby mode.

So what would fix it, is if when I ran the daemon via /etc/init.d that I could specify an alternate user for it to run as...  instead of running as root, what if it ran as a regular user account?  can I do that?

Ideally what i'd like is for it to run as root, but for the files it creates to be of chmod 770 setting with chown root:users...  so that all people in the users group could modify the files it creates...  but I don't want to have to do a reoccuring permissions script because that stops the drives from going into standby, and this is more of an archival file server, so it doesn't get used very often, i want the disks to be in standby mode most of the time, instead of never.

---

### Post by RealPSL on 2009-01-17
All the scripts in /etc/init.d run as root however within the script you can make it run the command to start a daemon as a different user by running the daemon as follows```
su user_name -c daemon_name
```

That will run the daemon daemon_name as user user_name. As for the permissions on the files if you set a umask with ```
umask 007
``` before the process creating the file starts it will create the resulting file with 660 permissions. Now to ensure that the group is always users I would recommend applying the setgid bit to the directory you are creating the files in with ```
sudo chmod g+w directory_name
```This will ensure the file created in that directory will always have have group name users.

---

