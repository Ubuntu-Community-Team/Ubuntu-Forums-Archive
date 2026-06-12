---
title: "Can't start desktop session after update to Dapper 6.06.2"
date: 2008-01-25
forum: Desktop Environments
---

### Post by aoakley on 2008-01-25
After updating my Dapper system to 6.06.2 , I now cannot log in to my Gnome session.

GDM works fine.

When I log in with my username and password, I get an error, as per:

```
aoakley@thoth:~$ date
Fri Jan 25 19:50:30 GMT 2008
aoakley@thoth:~$ cat .xsession-errors 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "aoakley"
/etc/gdm/Xsession: Beginning session setup...
INFO: imwheel started (pid=5700)
x-session-manager: error while loading shared libraries: libgnomeui-2.so.0: cannot open shared object file: No such file or directory
```

After clicking OK, it goes back to the GDM greeter.

I notice that in /usr/libs there is a symbolic link:

```
aoakley@thoth:~$ ls -l /usr/lib/libgnomeui*
lrwxrwxrwx 1 root root     24 2007-02-25 20:17 /usr/lib/libgnomeui-2.so.0 -> libgnomeui-2.so.0.140?.0
-rw-r--r-- 1 root root 540660 2006-07-31 21:58 /usr/lib/libgnomeui-2.so.0.1401.0
lrwxrwxrwx 1 root root     21 2007-03-04 21:48 /usr/lib/libgnomeui.so.32 -> libgnomeui.so.32.14.1
-rw-r--r-- 1 root root 869488 2006-01-08 17:16 /usr/lib/libgnomeui.so.32.14.1

/usr/lib/libgnomeui-0:
total 12
-rwxr-xr-x 1 root root 8396 2006-07-31 21:58 gnome_segv2
```

Can anyone help me please?

In other related news, the new kernel 2.6.15-51-k7 keeps panicing after a few minutes, but the above errors still occur regardless of whether I boot into 2.6.15-51-k7 or my previous kernel 2.6.15-29-k7 .

Any help much appreciated.

---

