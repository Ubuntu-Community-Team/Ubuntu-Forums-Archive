---
title: "script to reset default user desktop?"
date: 2010-05-17
forum: Desktop Environments
---

### Post by Mip5 on 2010-05-17
Hey Gang,

I'd like to run a script that will reset the panels and desktop wallpaper to the default user once a student has finished their session (students like to customize their desktop, and I'd like to allow them to do that, but don't want their customizations to impede the use for other students).

The commands I'd like to use are:

rm -rf .gnome .gnome2 .gconf .gconfd

executed as the user (in this case, "student") from their home directory.

I've tested the command, and it appears to achieve the goals of providing a unified experience for students when they login, but I'm not sure where and how to implement it.

Should it be the basis of a logout script that's called when the user "student" logs out? Would it be better as a part of a login script?

In either case - where would I put it?

Thanks in advance,

M

---

### Post by Mip5 on 2010-05-18
Still hunting around for this. I found a reference to:

/etc/gdm/PostSession

which contains the file: Default

```
#!/bin/sh

exit 0

```
Which I think just ends the bash shell. 

Would it be appropriate to add my script to the /etc/gdm/PostSession directory?

---

### Post by Mip5 on 2010-05-18
Okay, I put the commands into a script, and made it executable, and it works:

```

#! /bin/sh
# This script removes panels and desktop wallpaper settings
# They will be restored on next login
rm -rf /home/student/.gnome /home/student/.gnome2 /home/student/.gconf /home/student/.gconfd

```

I can't seem to get it to run on logout, however. I've tried adding a reference to it in .bash_logout for student, also have tried adding it to the directory: /etc/gdm/PostSession/Default

Any ideas where I should put this to get it to run on logout?

Thanks,

M

---

### Post by Mip5 on 2010-05-21
Okay - I've got this going now.

Here's the sequence:

I edited /etc/gdm/PostSession/Default to include a reference to the .bash_logout

```
#!/bin/sh
$HOME/.bash_logout
exit 0

```

I edited .bash_logout (and made it executable) to call the script I wrote after it finishes clearing the console (which is there by default):

```
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi
/home/student/reset_student_desktop


```

The reset_student_desktop script is an inelegant (but gets the job done) script that deletes the relevant gnome prefs:

```
#! /bin/sh
# This script removes panels and desktop wallpaper settings
# They will be restored on next login
rm -rf /home/student/.gnome /home/student/.gnome2 /home/student/.gconf /home/student/.gconfd

```

This works pretty well. Changes to the panels (added apps, being moved to the sides, or deleted altogether) and changes to the desktop picture all get deleted. I like to be able to offer the students the opportunity to modify their environments, but also want to give students a uniform and easily navigable desktop when they login. This method does both.

The next step is to get this applied to my 30 or so machines in each of a few labs. 

Cheers,

M

---

### Post by BenAshton24 on 2010-05-21
You should probably, also change the permissions on your scripts in order to prevent students from deleting them.

Good luck,
Ben.

---

### Post by Mip5 on 2010-05-21
> **BenAshton24 said:**
> You should probably, also change the permissions on your scripts in order to prevent students from deleting them.

Good luck,
Ben.

Yeah. I shared my work with a coworker, and that was the first comment he had. I'd also like to modify it so that a teacher could design their "ideal" desktop layout, and have *that* be the thing that is restored after a student logs out. 

Thanks for the reply,

M

---

