---
title: "No window controls after upgrade"
date: 2010-05-03
forum: Desktop Environments
---

### Post by Youri219 on 2010-05-03
Yesterday I upgraded from Ubuntu 9.10 to Ubuntu 10.4. After the upgrade I noticed the entire title bar, including the window controls to minimize/maximize/close a window disappeared. Resizing/moving a window is not possible either.

At first I thought something went wrong with the upgrade, so I did a full reinstall, but using the same home dir (sda5 mounted to /home). The problem remains.

I can temporarily fix it by changing the visual effects to normal or extra, but each time I restart I have to do this again. The controls appear at the right side, opposed to the left side which I would have expected from this release.

I realized that this must be something in my home dir, so I created a new user. For this new user, everything appears as expected, so it's most likely some configuration file left from 8.10 which 9.4 doesn't like.

Does anyone know how I can fix this?

Everything else seems to be working fine.

---

### Post by dino99 on 2010-05-03
metacity --replace

---

### Post by Youri219 on 2010-05-03
Thanks, but unfortunately it didn't help. After entering that command all controls disappeared again.

Anything else potentially giving conflicts?

UPDATE:
I started moving directories out of my home dir, to see what happens.  After I moved a lot of them out, I got window controls back even after  logging out/in.

The only one not moved back into my home yet is  /.config/gnome-session/saved-session and I still have window controls.  They are on the right side though, and it still doesn't look the same as  a 'fresh' user, but it is fully functional now.

---

