---
title: "Cannot change Default Application in Nautilus"
date: 2005-05-07
forum: Desktop Environments
---

### Post by rykel on 2005-05-07
Hi there,

When i choose Properties on an icon (say, a JPG), and try to change the default application to something in the list of programs (say, F-Spot), it always says, "Could not add application to application database".

This happens with ANY application I try to associate with any file.

Do you know how I can solve this problem?

I have remove "ubuntu-desktop"... has it got anything to do with it? I do remember that the same bug appeared even when I had ubuntu-desktop installed, but I could be wrong...


Best Regards,

Rykel
Singapore

---

### Post by Burgundavia on 2005-05-07
Check the permissions on .local in your home folder. If this gets messed up or changed to owner root, then you won't be able to edit those prefs.

Corey

---

### Post by MaX on 2005-05-07
[QUOTE=Burgundavia]Check the permissions on .local in your home folder. If this gets messed up or changed to owner root, then you won't be able to edit those prefs.

Corey[/QUOTE]
 That doesn't help.. it seems like I get that error only with VLC wxvlc is the command in gnome but it's vlc in the console??? and vlc works when I "add application" but not wxvlc... both commands work in the console

---

### Post by zilverling on 2005-12-22
Hello,

I have the same problem in breezy. I have reset the permissions of .local in my user directory (it was owned by root), but this does not solve the problem: I still get the same error message "Could not add application to the application database"

---

### Post by zilverling on 2005-12-28
I have solved the problem. For some reason all directories and files in .local had been set to owner and group root. After I had reset all directories and files in .local (including .local) to 'username' and group 'username' everything works as it should.

---

