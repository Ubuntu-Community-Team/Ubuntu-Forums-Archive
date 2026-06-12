---
title: "Location launcher in panel"
date: 2009-01-18
forum: General Help
---

### Post by solwic on 2009-01-18
I created a launcher to open a folder in my /home directory.  On the desktop, the launcher works perfectly.  

When I drag it to my bottom panel though, and click on it, I get the following error msgs:

[IMG]http://i444.photobucket.com/albums/qq165/joojoo612/errormsg.png[/IMG]

What gives?  It's not really important or anything, but I seem to remember this worked in Hardy.  I'm wondering if I did something wrong, perhaps?  Or if this is a known bug?

Thanks!

EDIT:  To clarify, I only get the error when I use the launcher in the panel.  I have no issues opening the folder in any other way.  :)

---

### Post by mssever on 2009-01-18
Try editing the launcher to run ```
nautilus /path/to/open
```

---

### Post by solwic on 2009-01-18
> **mssever said:**
> Try editing the launcher to run ```
nautilus /path/to/open
```

You're a genius.  :)

I'm not sure if the option to mark a thread as solved is back yet, but this did it.  

Though I must note that the first one I tried was a launcher for a location, and the one that eventually worked was a launcher for an application (since nautilus is obviously an app).   

Very cool.  

Thanks!

---

