---
title: "Desktop Drive Shortcuts"
date: 2015-06-06
forum: Desktop Environments
---

### Post by obsidian3 on 2015-06-06
Hey guys. I've have a small irritating issue with Xubuntu that hopefully is a simple fix.

Since I've used Xubuntu, I've had 2 problems with the desktop icons.

Problem 1 is that the icon drives reset to a mixed up order after every reboot. I was fortunately able to fix this issue using chattr. I used this following command..
sudo chattr +i /home/obsidian/.config/xfce4/desktop/icons*
This works great. The icons are always in the correct place after reboot.

Although, problem 2 is that certain icon drives don't show up on boot. The only way I've found to fix this which is temporary, is to go to desktop settings and check Show hidden files on the desktop, under the icons tab. The odd thing is that whether the show hidden files check box is checked or not, 1 simple click will show all the missing drives. I have all my drives set to automount at startup and I don't believe they are hidden but it's always the 2 that won't show at startup.

I made sure when I ran the chattr fix that all my drive icons were visible in the order I wanted them but they still seem to hide. Is there something I need to change in fstab to make the missing drives automatically show?

Of course, it's not a huge issue but rather irritating when I'm trying to access those drives quickly.

---

