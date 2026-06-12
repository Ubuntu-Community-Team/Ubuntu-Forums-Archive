---
title: "Xauth error"
date: 2008-01-14
forum: Desktop Environments
---

### Post by TechMansoor on 2008-01-14
xauth: creating new authority file /home/techmansoor/.serverauth.4249

Fatal server error:
Server is already active for display 0
                 If this  server is no longer running, remove /tmp/.X0-lock and start again.

-----------------------------------


Have you guys seen this before? This happens when I try to log in with my regular profile. Root logins graphically just fine,but when I log in as my standard user 'techmansoor', I get a command prompt. When I type in 'startx' I get the error above. Where do I start?

Things I've done:

Searched for .x0-lock in tmp, it isn't there.
Cleared some space from the root partiaion(previous error not mentioned).
Tried changing and putting my user in another group.


Can anyone help?

Thanks a million guys..

---

### Post by Mister.Vash on 2008-01-15
If the command prompt that you are getting is tty1, the x server may already been running

Press Ctrl+Alt+F7 from the prompt and see if that take you to the desktop

If that doesn't do anything, do the following
```

cd /tmp
ls -la

```

then post the output.  If it doesn't show anything of interest then some of the system logs may need to be posted

---

### Post by TechMansoor on 2008-01-15
drwxrwxrwt 16 root root 4096 Jan 14 20:06 ./
drwxr-xr-x 20 root root 4096 Jan 14 19:41 ../
drwx------ 4 root root 4096 Jan 9 16:58 1604873229/
drwxrwxrwt 2 xfs xfs 4096 Jan 14 19:42 .font-unix/
drwx------ 2 root root 4096 Jan 14 20:00 gconfd-root/
drwx------ 2 techmansoor techmansoor 4096 Jan 13 15:18 gconfd-techmansoor/
drwxrwxrwt 2 root root 4096 Jan 14 20:06 .ICE-unix/
drwx------ 5 techmansoor techmansoor 4096 Dec 24 00:05 kdecache-techmansoor/
drwx------ 2 root root 4096 Jan 14 20:06 kde-root/
drwx------ 3 root root 4096 Jan 14 20:06 ksocket-root/
drwx------ 2 root root 4096 Jan 14 20:00 orbit-root/
drwx------ 2 techmansoor usb 4096 Dec 23 23:57 plugtmp/
drwx------ 2 root root 4096 Jan 14 19:54 plugtmp-1/
drwx------ 2 techmansoor usb 4096 Dec 30 11:56 .vbox-techmansoor-ipc/
drwx------ 3 techmansoor techmansoor 4096 Dec 17 04:17 .wine-501/
-r--r--r-- 1 root root 11 Jan 14 20:06 .X0-lock
drwxrwxrwt 2 root root 4096 Jan 14 20:06 .X1


Does this say anything?

---

### Post by Mister.Vash on 2008-01-15
You do have that file in your tmp folder

-r--r--r-- 1 root root 11 Jan 14 20:06 .X0-lock

Type in the following to remove the file.
```

sudo rm /tmp/.X0-lock

```
Note that your file system is most likely case sensitive so make sure that you match the case.



  The dot preceding the filename may have been why you didn't see the file when you searched previously. The ls command does not display files that start with a dot unless you specify the -a option

After you delete the /tmp/.X0-lock file, restart your system and see if logging in with your techmansoor account works

---

### Post by TechMansoor on 2008-01-15
I appreciate the help brother. THat undoubtedly did it!

---

