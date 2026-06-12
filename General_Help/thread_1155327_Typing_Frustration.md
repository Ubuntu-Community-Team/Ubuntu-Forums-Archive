---
title: "Typing Frustration"
date: 2009-05-10
forum: General Help
---

### Post by fiveacez on 2009-05-10
Usually when I'm typing on Ubuntu, in a text box like the one I'm using to create this thread, my typing cursor will all of a sudden disappear and the next letter I type in will cause the page to scroll down, or I will begin typing in the middle of a previous sentence.  

I noticed this a bit during the installation off of the Live CD too, so this isn't just a Firefox issue.

Has this been happened to anyone else?

---

### Post by fiveacez on 2009-05-10
bump

---

### Post by leandromartinez98 on 2009-05-10
Are you typing in a laptop? If so, probably you are touching the touchpad
and that is moving the cursor from the actual position. You can disable clicking with the touch-pad to avoid that, or use the package "syndaemon" to disable the touchpad while typing.

---

### Post by fiveacez on 2009-05-10
Ok, well this sometimes happens when my touchpad is disabled also...

---

### Post by Mirge on 2009-05-10
Happens to me too sometimes when the page isn't finished loading. Just another possible scenario.

---

### Post by fiveacez on 2009-05-10
So how would that work when I'm using the Live CD installation program or after the page is done loading?

---

### Post by Alterax on 2009-05-10
Add this line to /etc/pbbuttonsd.conf

```
TPMode                = notap

```

Log out and back in.  That should take care of it, if not, let us know.  Had the same problem on my iBook, drove me up the wall!

---

### Post by fiveacez on 2009-05-10
What does this do? I'm new to Linux, so I'm still learning how to use it.

---

### Post by fiveacez on 2009-05-11
> **Alterax said:**
> Add this line to /etc/pbbuttonsd.conf

```
TPMode                = notap

```Log out and back in.  That should take care of it, if not, let us know.  Had the same problem on my iBook, drove me up the wall!

Um, I can't find pbbuttonsd.conf in etc.

---

### Post by fiveacez on 2009-05-12
bump

---

### Post by fiveacez on 2009-05-13
bump

---

