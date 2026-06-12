---
title: "No Login Screen Setup"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Micahb on 2006-06-20
I need to get into the Login Screen Setup, but it does not appear under System > Administration as it says it should in a few guides (including ubuntuguide.org/)
I looked in the Alacarte Menu Editor to see if it was unchecked and it isn't in there either.

Any help?
*note* I am a new Linux user, so please keep that in mind.

Thanks in advance

---

### Post by aysiu on 2006-06-20
Try Alt-F2 ```
gksudo gdmsetup
```

---

### Post by Micahb on 2006-06-20
That opens up the Login Window Preferences. I need the other one for [this]("http://ubuntuguide.org/wiki/Dapper#How_to_allow_root_user_to_login_into_GNOME") tho.

---

### Post by aysiu on 2006-06-20
[QUOTE=Micahb]That opens up the Login Window Preferences. I need the other one for [this]("http://ubuntuguide.org/wiki/Dapper#How_to_allow_root_user_to_login_into_GNOME") tho.[/QUOTE] It's now called "allow local system administrator login."

Um, there's no reason to ever log in as root, though.

If you want to make graphical root changes, just create a launcher for the command ```
gksudo nautilus
```

---

### Post by Micahb on 2006-06-20
Maybe I should make a new thread, but I will post the problem here first.
I need to resize a partition, but when I open up QTParted it says "No devices found. Maybe you're not using Root User?"
So I need to get in root user, but don't know how. I tried making the launcher, but it just takes me to the root directory...

---

### Post by aysiu on 2006-06-20
Most likely, you'd want to Alt-F2 ```
gksudo qtparted
``` Frankly, I'm surprised you were allowed to launch QTParted at all without root privileges. The "no devices found" message sounds worrisome, though.

---

### Post by Micahb on 2006-06-20
That worked, thanks. I'm not sure why I would have to do it like that tho.

---

### Post by aysiu on 2006-06-20
[QUOTE=Micahb]That worked, thanks. I'm not sure why I would have to do it like that tho.[/QUOTE]
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Micahb on 2006-06-20
Thanks for your help.

---

