---
title: "panel bar background image"
date: 2009-03-18
forum: Desktop Environments
---

### Post by faf1393 on 2009-03-18
when i tried changing the background image on the panel bar, the system just froze and when i restarted the machine both top and bottom bars were gone. i could still access the terminal but i could not find any help on as to how to fix the problem. at this point i was very disappointed with ubuntu and had to reinstall. i could not believe that such a small thing could render a linux system unusable.

does anyonw know how to fix that problem if it occurs again, because i#m now afraid of meddling with my ubuntu system. 

my system is 8.10 gnome

cheers.

---

### Post by s.fox on 2009-03-18
Hi,

I think you could have just restored it by

1)  Pressing Alt + F2.

2) ```
gnome-panel
```

Hope this helps you in future,  shame about the reinstall.

---

### Post by faf1393 on 2009-03-18
i believe i tried that several time, but it didn't do it

---

### Post by s.fox on 2009-03-18
Out of interest where you able to add a brand new panel?

---

### Post by mcduck on 2009-03-18
> **Ash R said:**
> Hi,

I think you could have just restored it by

1)  Pressing Alt + F2.

2) ```
gnome-panel
```

Hope this helps you in future,  shame about the reinstall.

Actually that won't work, since the dialog that opens when pressing Alt-F2 is part of the Gnome-panel. So you can't do that if Gnome-panel isn't running.. But starting the panel from a terminal sure works. Or if it doesn't, it will at least output errors that will help solving the problem.

Re-installing is hardly ever the correct way to fix problems in Linux. Most of the time things can be solved with much less work.

---

### Post by s.fox on 2009-03-18
> **mcduck said:**
> Actually that won't work, since the dialog that opens when pressing Alt-F2 is part of the Gnome-panel.

Oh, I didn't think Alt+F2 was part of the panel.  My bad.

[This]("http://prabath321.blogspot.com/2008/03/restore-gnome-panel.html") blog says that these terminal commands will restore the panel. 
```


gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel & 
```

---

### Post by faf1393 on 2009-03-18
i'll give it a go on the virtual box

---

