---
title: "Getting nautilus to go to a specific directory"
date: 2005-09-04
forum: Desktop Environments
---

### Post by Curlydave on 2005-09-04
I used to have a desktop launcher that had a good gksudo nautilus browser that went to the main directory. I don't remember the command, but I think that it was --/ at the end of the command. This isn't working though. Can anyone help?

---

### Post by felipe on 2005-09-04
gnome-sudo "nautilus --no-desktop /"

or if you prefer browser mode:

gnome-sudo "nautilus --browser --no-desktop /"

---

### Post by Curlydave on 2005-09-04
Thanks. It turns out that the problem was that I left out "--no-desktop /" and the quotes, which are both required. (My actual command looks a bit different though as I don't need the --browser part as it's checked in the settings and I use gksudo and not gnome-sudo.

---

