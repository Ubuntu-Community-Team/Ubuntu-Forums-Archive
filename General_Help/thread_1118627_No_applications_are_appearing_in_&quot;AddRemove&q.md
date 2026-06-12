---
title: "No applications are appearing in &quot;Add/Remove&quot;"
date: 2009-04-07
forum: General Help
---

### Post by jermsie on 2009-04-07
I mean it's not a huge deal but would be great if it was working because I've gone there a few times to grab programs.

**No applications are appearing in "Add/Remove" in the Applications menu.**

Why would this be and how can I change it?


Thanks a lot!

---

### Post by kpkeerthi on 2009-04-07
What happens when you run this command?
```
sudo apt-get update
```

---

### Post by lisati on 2009-04-07
One place to check is what you have selected for the "Show" button.

---

### Post by jermsie on 2009-04-07
> **kpkeerthi said:**
> What happens when you run this command?
```
sudo apt-get update
```

Just updates the repos but doesn't show anything different in add/remove.
"There is no matching application available"
That's even with "All available applications" selected

---

### Post by mb_webguy on 2009-04-07
"sudo update-apt-xapian-index"

---

### Post by jermsie on 2009-04-07
> **mb_webguy said:**
> "sudo update-apt-xapian-index"

No change. [Screenshot]("http://dl.getdropbox.com/u/38257/add-remove.png")

---

### Post by plucky on 2009-04-07
Have you tried to install Adobe Air or some other software recently?

Try ```
sudo apt-get install --reinstall gnome-app-install
```


Good Luck

---

