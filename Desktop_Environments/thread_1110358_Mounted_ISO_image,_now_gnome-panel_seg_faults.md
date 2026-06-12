---
title: "Mounted ISO image, now gnome-panel seg faults"
date: 2009-03-29
forum: Desktop Environments
---

### Post by nowhere@cox.net on 2009-03-29
Hi,
I used this info to set up nautilus mounting of iso images (rt click)
[https://help.ubuntu.com/community/ManageDiscImages](https://help.ubuntu.com/community/ManageDiscImages)

Works fine. I mounted this one ripped DVD image and the gnome-panel disappeared, the cursor kept blinking on and off, and the image didn't mount correctly. Also I couldn't umount it so I sudo rebooted.

Now the gnome-panel won't appear, and it simply seg faults when I run it from the command prompt.

If I log in as a different user it works fine except for a dialog box with some error about fast user switcher. I don't know if this is due to cntrol alt backspace I had to do to get to the login prompt since I didn't have a log out button.

Anyway, Im guessing that there's a config file issue with the one account now but I don't know which file. I tried deleting several config folders/files that mention the panel in the name but it didn't fix it. I restored all of them after each attempt didn't work.

Which files could be causing the problem?

BTW I tried the same iso image on my laptop and EXACTLY the same thing happened. Only difference was that after rebooting and the panel didn't show up automatically, I ran it from the command line and it worked on my laptop. No seg faults. The panel showed up fine on subsequent logins.

What gives?

Thanks!

---

### Post by nowhere@cox.net on 2009-03-30
Ok here's an update. I couldn't wait for an answer so here is a solution. Not a good one, but it is a solution.

backed up everything in my home folder I needed (including hidden .files)
changed another user to admin and logged in as that user.
deleted my baduser and deleted the /home/baduser
recreated baduser as admin (now it's a gooduser).
logged out of the second user
logged back in as baduser and removed admin from second user.
restored my files and a couple config stuff that couldn't have been causing the problem from the backup (like .mozilla).

Now I will begin to reconfigure my account (themes, icons, sessions etc).

If someone has a clue whats up with this please post for everyone else.

Thanks!

---

