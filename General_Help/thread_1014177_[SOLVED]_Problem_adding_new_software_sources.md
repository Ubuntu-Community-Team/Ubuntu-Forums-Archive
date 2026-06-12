---
title: "[SOLVED] Problem adding new software sources"
date: 2008-12-17
forum: General Help
---

### Post by bedhead75 on 2008-12-17
I've encountered a problem with adding new "third party software" sources from the administration > software sources menu.  After clicking on the "third party software" tab and then clicking on "add", the window pops up for me to enter the APT line of a new repository.  After I fill in the field, the "add" button is still not available.  Only the "cancel" works.  Am I doing something wrong or is this a bug?

---

### Post by jenkinbr on 2008-12-17
How are you tryping in the line?

---

### Post by taurus on 2008-12-17
What does that window look like?  Take a snap shot of it--Applications -> Accessories -> Take Screenshot.

---

### Post by bedhead75 on 2008-12-17
I forgot to say I'm using Ibex 64 bit.

---

### Post by jenkinbr on 2008-12-17
> **bedhead75 said:**
> I forgot to say I'm using Ibex 64 bit.
Okay, but could you answer/respond to mine or taurus's requests?  They still apply in your situation.

---

### Post by bedhead75 on 2008-12-17
Here's the screenshot.  You can see that the "add" button is still locked.

---

### Post by drs305 on 2008-12-17
We cannot see the end of the line you are adding but my guess is you haven't added the version and/or the component after the address.

For instance: 
```

deb http://ppa.launchpad.net/psyke83/ubuntu/ intrepid main

```

---

### Post by bedhead75 on 2008-12-17
You are right.  It worked now.  Thanks...stupid mistake on my part!

---

### Post by adult swim on 2008-12-17
that is a good looking desktop :)

---

### Post by jenkinbr on 2008-12-17
@original poster:

If this is solved, please mark it as such by clicking on thread tools and choosing "mark thread as solved".

---

