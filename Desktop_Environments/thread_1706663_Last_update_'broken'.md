---
title: "Last update 'broken'"
date: 2011-03-14
forum: Desktop Environments
---

### Post by kadellon on 2011-03-14
Hi all,
i've been searching but i don't found anything. I would like to know if anyone is having the same problem as me. I can't give any screenshots at this time, but i will when i gone home. The problem is that after the last ubuntu upload, all the gnome interface becomes very very 'retro' like if it's broken. Al the usual appearance get to a very ugly desktop.

Anyone is in the same situation or could know the reason?

thanx in advance,

---

### Post by abhibr95 on 2011-03-14
Well the same things happened to me when I changed the password of my user account. The desktop theme changing and not the usual style... adopting a classic windows look and all... but once I changed it back.. it got all right... I dont think I helped..but jus lettin you know...

---

### Post by kadellon on 2011-03-14
Thanx abhibr95,
I'll try at home to locate the desktop themes and figure if it's what has happened.

Regards,

---

### Post by Copper Bezel on 2011-03-14
It's not specific to a recent updat. See [this thread]("http://ubuntuforums.org/showthread.php?t=1575703&highlight=nautilus+reverts+theme").

It's a problem with Gnome Settings Daemon dying for some reason. If you run 

gnome-settings-daemon && killall nautilus

it'll fix the problem. (Just opening Appearance Preferences should restart the daemon, but Nautilus has to be restarted to reset the desktop icons.)

For most folks, this is happening at boot, and you can set the above command as a startup  application.

---

### Post by kadellon on 2011-03-14
Thank you very much Copper Bezel!!!!!

  that's exactly the way i'm seeing gnome. So, this night i'll do that, and i promise feedback.

Regards!!

---

