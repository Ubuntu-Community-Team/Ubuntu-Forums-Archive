---
title: "Cannot remove desktop shortcut to DVD"
date: 2008-02-03
forum: Desktop Environments
---

### Post by GlennB on 2008-02-03
Hi all,

Gnome seems to have got its knickers in a twist...

I have a desktop icon 'stuck' on my Gnome Desktop that I can't get rid of. I checked many similar posts, but the solutions (deleting entries in the ~/Desktop directory) don't work for this.

The shortcut doesn't seem to appear anywhere in /media or in my ~/Desktop directory. I can't delete it. It's a link to a DVD that was in the drive when I powered down the machine, and appears as "ALIEN_RESURRECTION_DISC_1". If I place that disc back in the drive, it automounts and a second shortcut appears, looking identical. I can then right click either of the desktop icons and choose 'eject'. The disc pops out, but the 'new' shortcut then disappears, leaving the rogue behind.

I've no idea where to look for this desktop file in order to remove it. I checked in /media, /mnt, ~/Desktop, and all over my home directory including in the hidden gnome directories. 

Can anyone let me in on the secret of where Gnome might be hiding this entry?

Thanks,

Glenn.

---

### Post by wjp.reg on 2008-02-03
That is strange.

Have you tried using the gnome configuration editor (gconf-editor) and see what is checked in the "apps | nautilus | desktop section?

Perhaps "volumes_visible" is checked?  Try unchecking it and see what happens.

---

### Post by GlennB on 2008-02-03
Well Whaddaya know!

I unchecked volumes_visible in gconf-editor, then exited gconf-editor, restarted it and rechecked volumes_visible. Restarted gnome, and all is well. Odd!

Thanks for the help. I'd still like to know where the heck the file representing that icon was living though!

Regards,

Glenn.

---

### Post by wjp.reg on 2008-02-03
Glad that worked for you.

:guitar:

---

### Post by shields on 2008-02-04
This worked for me too.  Thanks.

But I wonder -- how did that checkmark get set there?

---

### Post by wjp.reg on 2008-02-04
> **shields said:**
> This worked for me too.  Thanks.

But I wonder -- how did that checkmark get set there?

The default perhaps.

---

