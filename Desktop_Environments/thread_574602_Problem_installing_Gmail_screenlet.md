---
title: "Problem installing Gmail screenlet"
date: 2007-10-13
forum: Desktop Environments
---

### Post by Shay Andrews on 2007-10-13
I've never installed a screenlet before and this is my first official day on Ubuntu, so I might be doing something completely stupid, but bear with me, please.
Here's my problem. I downloaded the Gmail checker screenlet from gnome-look.org to my desktop, then opened the screenlet manager, clicked install, and navigated to the archive file. I got this error message:[I]
Invalid archive. Archive must contain a directory with the screenlet's name.[/I]
Is the archive bad, or am I doing something wrong?

---

### Post by martinw89 on 2007-12-03
Does anyone know a solution for this?  I have the exact same error message for the RSS screenlet available on Gnome look.

---

### Post by p_squared on 2007-12-06
Try extracting the file to /usr/local/share/screenlets instead.

---

### Post by lanchongzi on 2007-12-12
I Have the same problem
when I extract it to either /usr/local/share/screenlets  or to /.screenlets then the screenlet manager won't start anymore
as soon as i delete the files i pasted into it works again

really weird

but is there another way, or something?

---

### Post by lanchongzi on 2007-12-13
solved my problems by overriding the screenlet-0.0.10 with screenlet-0.0.7

---

### Post by nikolas68 on 2007-12-13
..check this forum:

[http://ubuntuforums.org/showthread.php?t=639388](http://ubuntuforums.org/showthread.php?t=639388)

---

