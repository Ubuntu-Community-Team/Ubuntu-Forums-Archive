---
title: "Help restoring xorg.conf"
date: 2005-12-16
forum: General Help
---

### Post by DiscoKiller on 2005-12-16
I recently broke my xorg.conf file :( changed something i shouldn`t have, and as a result the system hangs when 'Checking battery state'. I need to know if it is possible to edit my xorg.conf file while running the live cd as i know exactly what needs changing, i even backed the xorg.conf file up when i made the change but as i cant get into breezy i dont really know how i`m supposed to do it. My immediate thoughts were, boot disk and edit it in the terminal, but then i dont know how to do that. I`m not sure of the details but i`m guessing it is some sort of temporary partition made when the live cd is put into the drive and editing the xorg.conf file in here will make no difference. any help would be greatly appreciated, i tried searching on this subject but i couldnt find anything useful. thx DK

---

### Post by kaamos on 2005-12-16
Try the "recovery mode" option in grubs menu. Then restore the original file with "cp your_backupfile.conf /etc/X11/xorg.conf"

---

### Post by DiscoKiller on 2005-12-16
i would do that but with the system hanging, it does so b4 i get to GRUB loader so there no other way for me to even operate the computer without the Live cd

Is there a way i can mount my linux partition in the Live cd boot to edit the file that way, otherwise i`m completely stumped as to how to do it, other than a complete re load.

---

### Post by kaamos on 2005-12-16
You can mount. In Damn Small Linux at least it's as simple as clicking a button.. So there is certainly a way so get your box running again.

---

### Post by Gurgeh on 2005-12-17
Naaah, just have a look at your grub menu in detail, theres a way to boot avoiding all major runlevels and all you do is "sudo vi" your xconf file. Worked for me anyways.

EDIT: Obviously by major runlevels I mean, not syncing the clock or modprode ('orrible thing that)

---

### Post by craty on 2005-12-17
i think by pressing Ctrl+C or Ctrl+Alt+F1  when it hanged at "checking battery state" would lead to a terminal asking for login. once try it.

---

### Post by DiscoKiller on 2005-12-18
Thanks for the help guys, the prob is sorted now. Again cheers for the help and have a good Xmas!

---

### Post by rosslaird on 2005-12-19
[QUOTE=DiscoKiller]... the prob is sorted now. [/QUOTE]

And what is the solution, if I may ask? I'm having the same problem after messing with my nvidia driver.

Ross

---

### Post by newuser111 on 2005-12-19
[QUOTE=rosslaird]And what is the solution, if I may ask? I'm having the same problem after messing with my nvidia driver.

Ross[/QUOTE]

just run sudo dpkg-reconfigure xserver-xorg, it will generate a new xorg.conf

---

