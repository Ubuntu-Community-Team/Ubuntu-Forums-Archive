---
title: "problem with &quot;enable automatic login&quot;?"
date: 2006-08-27
forum: Desktop Environments
---

### Post by av05 on 2006-08-27
Hi all,

I just installed mythtv on an ubuntu box. as part of the installation process it created a user called mythtv, which i've added to admin group.

i'm trying to make this user automatically login, but when i go to the login window administration, on the security tab, the "Enable Automatic Login" lists only 1 user- the user i created during the installation.

is there a way to add more users to this list of automatically login?

thanks!

---

### Post by lagagnon on 2006-08-27
In System, Administration, Login Window, Users, choose Include all users in /etc/passwd.

---

### Post by av05 on 2006-08-28
> **lagagnon said:**
> In System, Administration, Login Window, Users, choose Include all users in /etc/passwd.

Thanks lagagnon- I did that already, and still, mythtv user doen't show on the list, nor does it login automatically when i type-in the mythtv name directly at the dropdown (it doesn't appear as an option in the dropdown, i have to type it directly).

i also tried to change /etc/gdm/gdm.conf, and wrote there:
```
AutomaticLoginEnable=true
AutomaticLogin=mythtv

```

but still, user mythtv doesn't login automatically on startup-
the only user that can auto login is the user i created during the install process....

any idea ???](*,)  ](*,)

---

### Post by av05 on 2006-08-31
actually, here's a few more bits of info that may be relevant:
on the System->Administration->Users, I get a userlist that contains by default only the first user that was defined by the installation. It's only when I check the "show all users" box, then I get a full list.

I've configured mythtv user to be the same (in terms of permissions) as the installation-defined user, and still-
when I go to System->Administration->Login Window, the "security" tab doesn't show the mythtv user as an option for automatic login, only the installation-defined user (and of course, I made sure to check the "include all users" box on the Users tab...).

Anyone??? I have to get this box to auto-login... :-(

---

### Post by brundles on 2006-09-07
I came on here looking for the answer to this exact problem, and while I didn't find the answer your thread did give me enough to poke around and find AN answer. (OK, I'll admit I'm lazy but curious it was more fun to poke around at the risk of my system than keep looking for a readily written answer :biggrin: ).

Anyway, it looks like the problem is that the mythtv install scripts just add Myth as any old new user while the Ubuntu automatic login will only let you use users with an ID of 1000 upwards. (I could be wrong, that was just the logic that led me to try what follows...)

Hope this helps,
Keith

*Edit:* After writing all of this I just found [this other thread](http://ubuntuforums.org/showthread.php?t=205040) which outlines a much easier way of doing it :rolleyes: - although it does confirm my weird logic :)

=================

Before you try it, be aware that while it worked for me, my usage of Myth TV is very limited - I don't use it as a PVR and don't use the TV function - I only use it as a front end for video and DVD playback. (Functionality wise it's replacing an old Xbox with XBMC). I also worked this out fairly quickly by taking the view that as it was a simple install it could be re-installed fairly easily and painlessly.

To others who know better, yes I'm sure there is an easier way - I just don't know it - feel free to butt in :)

*** YOU HAVE BEEN WARNED ***

1. First of all log in as another user.

2. Kill the Myth TV backend - it won't be pretty if you delete a user with a running process and recreate it with a different user ID:
```
keith@HTPC:~$ ps -ef | grep backend
mythtv    5081     1  0 00:20 ?        00:00:00 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
keith     6307  6286  0 00:30 pts/0    00:00:00 grep backend
keith@HTPC:~$ sudo kill 5081
```

3. Find out the original Myth TV user ID and make a note of it.
```
keith@HTPC:~$ cat /etc/passwd | grep -i myth
mythtv:x:116:116::/home/mythtv:/bin/sh
```

4. Using the Ubuntu Users and Groups manager, delete and re-add the MythTV user. Make sure you do this in the same session (i.e. Don't click Close on the Window until you've done the delete and add). This will recreate the user with the user ID we want (above 1000) and automatically chown the contents of /home/mythtv to the new user ID.

5. This is the tricky part. You now need to rummage through your entire system for anything that was owned by the old MythTV user ID and chown it to the new MythTV user. The best way to find the things you need to change is 'Places' -> 'Search for Files' -> 'Select More Options' -> 'Owner is unrecognised' -> Find.
As a starting point, I had to do the following chown's to get things back in place:
```
  sudo chown -R mythtv:mythtv /var/lib/myth*
  sudo chown mythtv /etc/mysql.txt
  sudo chown mythtv /etc/mythweb-settings.php
  sudo chown -R mythtv /var/log/mythtv
  sudo chown -R mythtv /var/cache/mythtv
```
This will vary depending on your install so you're better using the search approach though.

6. Next restart the backend process. If like me you have mythfrontend starting when the mythtv user logs in (all of this should have been preserved during the user delete) then you'll need to su to myth from your current user:
```
keith@HTPC:~$ su mythtv
Password:
sh-3.1$ mythbackend &
```

7. Nearly there! Now try and login as the mythtv user and make sure things seem OK and you can start the front end successfully.

8. Assuming that's all OK, go back to the Login Window settings and you should now be able to choose mythtv from the dropdown box.

9. Reboot and enjoy!

---

