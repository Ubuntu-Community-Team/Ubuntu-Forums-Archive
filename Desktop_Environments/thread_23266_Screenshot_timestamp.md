---
title: "Screenshot timestamp?"
date: 2005-04-01
forum: Desktop Environments
---

### Post by vaskark on 2005-04-01
Is there any way, when using the gnome-screenshot applet, to get a timestamp as part of the filename? If not, can someone recommend another way to do this easily?

---

### Post by Compwiz on 2005-04-01
put it in manually :-s

---

### Post by jeremy on 2005-04-01
[QUOTE=Compwiz]put it in manually :-s[/QUOTE]
 it will show the clock/calendar on the panel

---

### Post by vaskark on 2005-04-02
I made a nautilus script using scrot (which you can install thru apt-get).

 ```
#!/bin/bash
scrot '%Y-%m-%d_%I-%M-%S%p_scrot.jpg' -e 'mv $f ~/shots/' -q 100 -d 5 -c
```

Make a text file with the above code, make it executable, and save it to ~/.gnome2/nautilus-scripts. View the scrot manpage to learn the different options.

Hope this helps somebody :D

---

