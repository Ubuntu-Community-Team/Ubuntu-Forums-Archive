---
title: "Help Compiz Themes Gone !!"
date: 2006-07-21
forum: Desktop Environments
---

### Post by KFASheldon on 2006-07-21
Hi

After update today Compiz Themes no longer work, the themer is installed and comes up but selecting themes does nothing, compiz stays in it old original form and I had a wonderful OSX look allsorted.

I think it has something to do with the new theme engine installed 'cgwd' as I am sure I never saw that before.

Anyone having same problems, any ideas how to fix.

The compiz package I am using is 'quinns-21' 

Quinn you out there, love your work but what happened ??? HELP

Thanks
Karl

---

### Post by KFASheldon on 2006-07-21
If it helpd attempting to run cgwd at root terminal gives this

cgwd: Connection Error (No reply within specified time)
7975: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4628.
This is normally a bug in some application using the D-BUS library.
7975: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4592.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
Aborted

---

### Post by lazyd2 on 2006-07-21
> **KFASheldon said:**
> Hi

After update today Compiz Themes no longer work, the themer is installed and comes up but selecting themes does nothing, compiz stays in it old original form and I had a wonderful OSX look allsorted.

I think it has something to do with the new theme engine installed 'cgwd' as I am sure I never saw that before.

Anyone having same problems, any ideas how to fix.

The compiz package I am using is 'quinns-21' 

Quinn you out there, love your work but what happened ??? HELP

Thanks
KarlYou have to edit your compiz script
[http://www.ubuntuforums.org/showpost.php?p=1283090&postcount=23](http://www.ubuntuforums.org/showpost.php?p=1283090&postcount=23)

---

### Post by KFASheldon on 2006-07-21
Thanks just found that !!! Just a thought but is there not a way for updates to inform on things like this some-how !! Got me realy confused ! Still sorted now Thanks

---

