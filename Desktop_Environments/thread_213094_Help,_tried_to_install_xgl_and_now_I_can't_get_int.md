---
title: "Help, tried to install xgl and now I can't get into gnome"
date: 2006-07-10
forum: Desktop Environments
---

### Post by AFeuer on 2006-07-10
Ok,so I'm very new to linux and I have been playing around for the last week learning a lot and trying to make linux do everything I used to use windows for (not a small task).  Earlier today I finally decided to try the cool new 3d desktop xgl.  I felt pretty good about myself because I got the new ati drivers to work along with the extended desktop.  I decided to try the directions in this link to install xgl [http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389")
Now when I boot up it goes to a grey dotted screen and trys to login 3 times and then just goes to the nongraphical terminal screen.  This is fine because I can log in and do stuff.  The problem is that I don't know what to do!](*,) I'm great at following directions for installing something, but I usually have no idea what they mean.  Now I don't know how to get xgl to work, or more important how to get back into the graphical interface where I can at least navigate a little bit.  Please help, I'm pretty lost and while I can always reinstall Ubuntu, I'm trying how to learn how to fix the problems instead of reinstalling everything like in windows!  Thanks

---

### Post by Milamber_Cubed on 2006-07-10
How far through the guide did you get?

If you got as far as editing the /etc/gdm.conf-custom file, try reverting those changes. If you do that, then none of the XGL software will ever be loaded, it will just be sitting there on your system. You might get other issues once logged in, but we can deal with them as they come up ;)

---

### Post by AFeuer on 2006-07-11
I got all the way through the guide.  I would like to edit that file, but i'm not sure how from the prompt.  I can't use the gedit command.  Thanks.

---

### Post by Milamber_Cubed on 2006-07-11
You will have to use a command line editor. I use "vi" but that is not very friendly for people who don't know how to use it.

try this:

```

sudo pico /etc/gdm/cdm.conf-custom

```

This will bring up the file in the pico editor where you canm make the changes needed and the use the shortcuts Ctrl+X (listed at the bottom of the page) to exit and answer yes to save the changes.

---

