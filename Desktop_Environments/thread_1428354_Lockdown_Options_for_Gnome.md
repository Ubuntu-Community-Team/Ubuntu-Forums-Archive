---
title: "Lockdown Options for Gnome"
date: 2010-03-12
forum: Desktop Environments
---

### Post by ckroon on 2010-03-12
First Time Poster and Ubuntu Noob here.

I am getting an Image of Ubuntu ready to deploy in a high school computer lab.

I have a user profile locked down pretty well using Sabayon.
I have two things left:

1- prevent the user from right clicking the desktop and changing the wallpaper/background.

2- Hide the Places menu so they can't get to Computer and the files therein.

If I can't do 1, then I would need to have a way to reload default settings at Login time.

Thanks!

---

### Post by asmoore82 on 2010-03-13
I work for a school system as well...
I hope you will take this in the spirit which it is intended...

My friend, I feel you are heading in the wrong direction.
Lockdown options can easily be taken too far and this is quite contrary to the whole Linux paradigm.

Locking down the panels is sensible because it is easy to change them accidentally, especially
when Gnome is new and unfamiliar. But no right-clicking on the desktop?? come on!!

How are the youth supposed to learn to use computers if they are not allowed to use the computers?

Even if you do manage to do this, wallpapers can still be set directly from within firefox.

Why can't students be allowed to browse "Places -> Computer" ~
surely you don't have all of them running with root privilege.
Therefore, they can't possible change, delete, move or overwrite
any system files outside of their home folder.

The only viable long-term solution to the lockdown problem is some sort of
directory services where the students can each use their down account for login.

If the students are to share a user account, I can see a need to prevent someone
from leaving and inappropriate wallpaper for the next person. But in all honesty,
this is more a disciplinary issue than a technological one.
I am testing the "mandatory" wallpaper setting, I'll let you know how it works.

---

### Post by asmoore82 on 2010-03-13
This works for the wallpaper, it will even stop Firefox...

Set it to what is desired in an admin account, then run ```
gconf-editor
``` in the left pane, navigate down to "/desktop/gnome/background,"
in the right pane, right-click "picture_filename" and choose "Set as Mandatory"
you will probably also want to do the same for "picture_options"

It seems the admin account you are in has to log out and back in
for this restriction to affect it.

To review all mandatory settings at a later time, run ```
gksudo gconf-editor
```
and open "File -> New Mandatory Window"

---

### Post by ckroon on 2010-03-13
Thanks for the response.

These are HS kids... they know full well how to use a computer.. and they LOVE to set the desktop wallpapers and delete icons so it ruins the experience for the next user.

Its a large lab and is not always policed well so I need to lock it down as much as possible.

Your instructions will help a lot with that.
Thanks!

---

