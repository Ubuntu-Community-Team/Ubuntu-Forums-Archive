---
title: "Gnome-Do does not recognize compositing"
date: 2009-01-31
forum: General Help
---

### Post by richardq on 2009-01-31
I've just upgraded to Intrepid and have got everything working just about how I like it. I've got compiz sorted too. The only problem I'm having is that I'm running Gnome-Do (the 0.8 release with the new Docky theme) and for some reason it's not seeing that I have compositing enabled - and therefore won't let me change themes.

I have set Gnome-do to auto start and this is when the problem happens. However, if I kill the Gnome-Do process and restart it from a terminal (or don't autostart it to begin with) it sees the compositing no problem.

So how do I ensure Gnome-Do is starting *after* Compiz is up and running?

---

### Post by mknepher on 2009-01-31
I'm not sure if it makes a difference, but did you add gnome-do manually to the session manager, or did you set it in the gnome-do preferences?

---

### Post by Patricrawley on 2009-01-31
You could write a 30 second sleep bash script to delay the launch of gnome do until after compiz is running.

---

### Post by Patricrawley on 2009-01-31
```

#!/bin/bash
sleep 30 &&
gnome-do

```
Save that as whatever
Make it executable
```

chmod +x *filepath*

```

Open the sessions menu
Add
Name:Gnome-Do
Command: *Your script*
Comment: *Whatever you choose*

Make sure to remove old gnome-do startup entries in the gnome-do prefs and sessions menu.

---

### Post by johnjohn2 on 2009-01-31
> **Patricrawley said:**
> ```

#!/bin/bash
sleep 30 &&
gnome-do

```
Save that as whatever
Make it executable
```

chmod +x *filepath*

```

Open the sessions menu
Add
Name:Gnome-Do
Command: *Your script*
Comment: *Whatever you choose*

Make sure to remove old gnome-do startup entries in the gnome-do prefs and sessions menu.

Perfect thanks

---

### Post by richardq on 2009-01-31
> **mknepher said:**
> I'm not sure if it makes a difference, but did you add gnome-do manually to the session manager, or did you set it in the gnome-do preferences?

I actually tried both ways. No difference.

> **Patricrawley said:**
>  You could write a 30 second sleep bash script to delay the launch of gnome do until after compiz is running. 

Thanks for providing that, it did the trick! :)

Thanks guys.

---

### Post by dnl.close on 2009-09-28
works like a charm.!

---

