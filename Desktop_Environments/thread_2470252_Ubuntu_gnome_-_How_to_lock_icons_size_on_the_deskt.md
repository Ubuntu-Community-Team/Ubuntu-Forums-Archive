---
title: "Ubuntu gnome - How to lock icons size on the desktop"
date: 2021-12-23
forum: Desktop Environments
---

### Post by henrysmith98 on 2021-12-23
I tried to post this solution in this thread: [Ubuntu 18.04 gnome - How to lock icons size on the desktop]("https://ubuntuforums.org/showthread.php?t=2439863")
If a mod could post this solution there that would be great as a google search links to that thread.

I finally solved it. I can now resize the icon size in Files without it changing the icon size on the desktop. Here is the solution:


1. As your normal user run this command:
dconf read /org/gnome/nautilus/icon-view/default-zoom-level
Take note of the output, for me it is:
'small'
2. Use root user for the rest of the steps below:
3. Ensure that this file:
/etc/dconf/profile/user
contains at least these 2 lines(it may have others after these 2 lines, leave them there):
user-db:user
system-db:local
4. Create this file:
/etc/dconf/db/local.d/01-icon-view
with these contents:
[org/gnome/nautilus/icon-view]


# After the = sign use the output from the cmd in step 1 for me it was 'small'
default-zoom-level='small'
5. Create this file:
/etc/dconf/db/local.d/locks/00-default-zoom-level
with this content:
/org/gnome/nautilus/icon-view/default-zoom-level
6. Run this command:
dconf update
7. Log your normal user off GNOME.
8. Log back in again as normal user.
9. Use Files and change the icon size by clicking the hamburger icon and then clicking the - and + next to the percentage. The icon sizes will now change in Files but stay a fixed size on the Desktop.

---

### Post by ActionParsnip on 2021-12-24
Great share. Not a fan of desktop icons myself but others do....

Not a mod but I like encouraging this sort of thing :P

---

