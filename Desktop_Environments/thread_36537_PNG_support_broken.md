---
title: "PNG support broken"
date: 2005-05-23
forum: Desktop Environments
---

### Post by sparx on 2005-05-23
I just upgraded to Hoary today and things went relatively smoothly.. had to dpkg-reconfigure xserver-xorg before I could get back to the gui, but that's about it.

Now when I login and gnome loads up, I get quite a few popups such as "Failed to load image gnome-terminal.png  Details: Unrecognized image file format", and a bunch of red X's where the images would have been had they loaded properly.

This happened once under Warty, and I think the solution ended up being deleting libpng12.so.0 from /usr/local/lib - that didn't work this time. I've tried reinstalling the package libpng12-0, but that doesn't do much to correct the proplem. I can't do an upgrade since it's version 1.2.8-rel1, and uninstalling it and reinstalling clean would take out quite a few packages in the process.

I'm hoping someone out there knows of a fix, since my own searching is turning up a whole lot of nothing. Thanks for the help.

---

### Post by sparx on 2005-05-24
Ok, so I've spend the last day banging my head against this and still haven't come up with anything. I've tried deleting the libpng related files, downgrading libpng10-0 & 12-0, reinstalling, etc.. nothing is fixing this problem. I've done just about everything I could think of short of completely removing these packages.

Since it doesn't look like I'm going to get an answer to this question, and it's quickly falling down through the pages.. is there a way to remove a package and have the package manager ignore any dependency issues? Right now if I attempt to remove the libpng packages there doesn't seem to be any way to prevent a whole slew of other packages from being removed along with them.

---

### Post by RastaMahata on 2005-05-24
just guessing here, but how about reinstalling the ubuntu-desktop package? and if that doesnt work, ubuntu-base?

---

### Post by sparx on 2005-05-27
Tried both.. and nothing is different. ](*,)  I think I'll just have to keep trying to fix it until I completely destroy my install and have to start from scratch.  :wink:

---

### Post by sparx on 2005-05-27
Grrr... ok. I fixed it. Quite accidentally too. Right now I'm pretty sure that if you gave me a banana, a bottle of gatorade, a few sticks, and managed to convince me that it was once a working computer - I'll have you playing doom 3 on it in just under 2 weeks. Or not. :P

Certain error messages that can't be reproduced now led me on a trail of files and commands that eventually led me to the command 'update-gdkpixbuf-loaders'.. *poof* problem solved.

Hopefully no one else runs into this mess, but if they do, I hope this can be of some help. And to think I was going to back everything up and start over with my warty cd. Ouch.

---

### Post by lesinfox on 2006-08-08
Thanks a lot.
I just had the same problem, this solution also worked for me

---

