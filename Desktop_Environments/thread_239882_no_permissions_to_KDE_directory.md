---
title: "no permissions to KDE directory"
date: 2006-08-19
forum: Desktop Environments
---

### Post by 5centcigar on 2006-08-19
When attempting to change to a KDE session, I get this message: 'Could not start kstartupconfig. Check your installation.' I am then kicked back to the logon screen.
It seems I do not have permissions to the 'kde' directory in my home directory.
I saw this same problem posted back in Feb. with no responses whatsoever.
What gives?

---

### Post by gerbman on 2006-08-20
If you're having permission problems with a particular directory, you can change them with```
sudo chown -R user:user directory
sudo chmod -R 644 directory
```chown changes the owner of "directory" to "user", as well as any subdirectories/files (-R means to make the same change to all subdirectories). chmod changes the permissions for directories/files, as well as any subdirectories/files (again indicated with -R). The 644 part can be confusing, so I won't explain it unless you need it. I would try the two commands above on the problematic directory in your home directory and see if that fixes your problem.

PS - Don't go changing permissions with the -R option unless you know what you're doing. Using -R in your home directory isn't a big deal, but it can mess things up elsewhere.

---

### Post by dr.jackal on 2006-10-23
Hi,
I'm getting the same problem: "could not start kstartupconfig". 
My .xsession-errors looks like this:
```
jakob@jakob-laptop:~$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jakob"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/jakob-laptop:/tmp/.ICE-unix/6069

(gnome-panel:6141): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:6141): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 25

```

i tried sudo chown and chmod as described above and that solved half of the problem because now i no longer get the message that access to /home/jakob/.kde were impossible. 

plz help

---

### Post by blackest_knight on 2006-12-29
I had a similar problem started when i installed konquerer wasn't going right at all progressively installed more and more kde still not right.

The problem is kde wants to write to the .kde folder in your home directory but permissions are wrong.

solution login with gnome and rename .kde .kdeold logout login with kde it will rebuild .kde with the right permissions. delete .kdeold 
problem solved.

---

