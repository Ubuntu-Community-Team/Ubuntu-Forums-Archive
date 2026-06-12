---
title: "Setting A Default Application For All Users"
date: 2008-12-11
forum: General Help
---

### Post by RobMagus on 2008-12-11
I'm running Ubuntu 8.10 and I'd like to set all files of a certain type to be opened by one program for all users on the system.

I can right click on the file and set it to always be opened by a default application just fine, it's just that the default doesn't persist for other users.

The files are in a shared folder that all users have access to, and I've made sure the program I want to use is executable by everyone.  I've searched around for a config file that lists file types and what program should open them, but I'm stumped.

(To be more concrete, I have a number of users who want develop and test text adventures.  These text adventures have file extensions like .zblorb and .glulxe, and there are a whole lot of different extensions.  Not all my users know how to set default programs for themselves, and it's a headache to log in for everyone and set them manually.

I want to find a way to configure .zblorbs and .glulxes -and any new format that might come up in the future- to be run by Gargoyle -no matter what user you are-.)

Any help would be GREATLY appreciated!

- Rob

---

### Post by albinootje on 2008-12-11
Here's a solution : [http://ubuntuforums.org/showthread.php?t=654320](http://ubuntuforums.org/showthread.php?t=654320)

---

### Post by ajcham on 2008-12-11
Each user's default file associations are stored in ***~/.local/share/applications/defaults.list***

However, the file you will be interested in is ***/usr/share/applications/defaults.list*** - which sets the defaults for all users. (Except where the defaults.list file in their home specifies a different association)

---

### Post by RobMagus on 2008-12-11
Thanks for pointing me to the file!  Unfortunately, the thread albinootje linked to doesn't actually say how to edit the file to set file associations.

I edited /usr/share/applications/defaults.list by adding the following line at the end:

```
#Added Associations
misc/zblorb=gargoyle
```

Then I logged out, logged in as a test user (with access to the files) and tried running a zblorb.  It didn't work.

I also tried ```
misc/zblorb=gargoyle.desktop
``` , following the convention of all the other lines in defaults.list, but that didn't work either.

Is there some convention I'm not following?  Should I have used "application/" instead of "misc/"?  Does gargoyle need to be in a particular directory?  (Right now it's in /usr/bin)

Thanks again for any help!

- Rob

---

### Post by ajcham on 2008-12-11
My guess is gargoyle.desktop isn't the correct name.

Try:
```
ls /usr/share/applications
```
and search for gargoyle's entry from the resulting list.

---

### Post by ajcham on 2008-12-11
On second thoughts, since you have already created the association in your own *defaults.list* (using the right-click method), you could check that file for the appropriate text.

---

### Post by albinootje on 2008-12-11
Create a desktop-icon for the application and put it in /usr/share/applications/ with the corresponding name.
And perhaps you will need to log out of Gnome and log in again before those changes are active.

---

### Post by RobMagus on 2008-12-11
Gargoyle isn't in /usr/share/applications .  Should I move it there from /usr/bin ?

Also, I don't have a local defaults.list in ~/.local/share/applications, but I -do- have a mimeapps.list which contains the following lines:

```
[Added Associations]
application/x-extension-zblorb=userapp-gargoyle-5J9QLU.desktop;
application/x-extension-gblorb=userapp-gargoyle-5J9QLU.desktop;
application/x-extension-z8=userapp-gargoyle-5J9QLU.desktop;
application/x-extension-GAM=userapp-gargoyle-5J9QLU.desktop;
application/x-extension-z5=userapp-gargoyle-5J9QLU.desktop;
```

which presumably was created when I right-clicked and set the default program myself.

Also in ~/.local/share/applications is the file userapp-gargoyle-5J9QLU.desktop which contains the following lines:

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec='/usr/bin/gargoyle' %f
Name=gargoyle
Comment=Custom definition for gargoyle
NoDisplay=true
```

I think this file is required to let mimeapps.list associate zblorbs et al. with gargoyle.

So now the problem is:  how do I replicate this for all users?  Do I have to put a copy of "userapp-gargoyle..." into /usr/share/applications and then edit /usr/share/applications/defaults.list to include the same added associations as mimeapps.list?

That seems right, so I'll try it and report on success/failure.

- Rob

EDIT:

So I copied the userapp gargoyle launcher into /usr/share/applications and edited defaults.list to add the appropriate lines.  I tried it both with semicolons at the end of each line (like in the original) and without (like the other entries in defaults.list) and it didn't work.

I tried renaming userapp-blablabla to gargoyle.desktop and changing the lines in defaults.list to reflect it, and that didn't work either.

:(  Any other ideas?

---

