---
title: "Help Menus under &quot;System&quot; don't work"
date: 2006-09-23
forum: Desktop Environments
---

### Post by fatsheep on 2006-09-23
I've got an interesting little problem here...  If I click on "About Ubuntu" under the System menu, a window appears to load in the bottom toolbar for about 5 seconds and then disappears.  The "About GNOME" link, on the other hand, works.  Under the System>Help menu, System Documentation acts the same as "About Ubuntu.  "Online Documentation", "Community Support", and "Commercial Support" all point towards [www.arizona.edu](www.arizona.edu) for some reason.  The Ubuntu Book excerpt is the only link in the Help menu that works.  

Any ideas on how to fix this strange problem?

---

### Post by meng on 2006-09-23
Have you got yelp installed? I think that's the help program, so to speak. Another way of asking this is, has this always been the case, or did it work previously?

---

### Post by fatsheep on 2006-09-23
Yea I do have yelp installed and it did work previously.

---

### Post by meng on 2006-09-23
Try this from the terminal then:
yelp ghelp:about-ubuntu

---

### Post by fatsheep on 2006-09-23
> **meng said:**
> Try this from the terminal then:
yelp ghelp:about-ubuntu

Here's my output:

> Could not initialize gecko!

---

### Post by meng on 2006-09-23
Well there's your answer then.
Which means I don't know why gecko isn't initializing.

---

### Post by fatsheep on 2006-09-23
Yea it's very strange.  Gecko is used by Firefox isn't it?  Firefox works fine for me...

---

### Post by fatsheep on 2006-09-23
Now whenever I click on an external link it takes me to [www.arizona.edu](www.arizona.edu).  Very strange...  Perhaps these problems are related?

---

### Post by kbro237 on 2006-10-11
i'm having the same problem. i have a feeling it has happened since i've been using firefox rc2... i fiddled with the lib folder a bit...

---

