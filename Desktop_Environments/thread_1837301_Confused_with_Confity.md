---
title: "Confused with Confity"
date: 2011-09-01
forum: Desktop Environments
---

### Post by eldonkr on 2011-09-01
I've had the tarball for confity-1.6 sitting on my desktop for about a month now. I finally got around to trying to configure it last night. I got as far as the ./configure step and it told me that the command wasn't found or something, that's not the problem.

I check the INSTALL file in what I just extracted and it says the following:

```

run the following command in a terminal, for Confity to create a "Configure Unity" entry in the Control center : sudo setup.py install ; that's it.

```

To get it to do what it said it was going to do I actually had to enter:
```

sudo python setup.py install

```

Anyway, I haven't encountered any problems so far; however, what do I do with this Configure Unity entry, and what and where is this Control Center that is referenced?

What's the next step I should take so that Confity is an installed app that I can run from my launcher?

---

### Post by Frogs Hair on 2011-09-01
What used to be the control center is now system settings and  can be found by selecting the shut down button on the panel , it appears in the menu .
Not sure if this is what you want though .

---

### Post by eldonkr on 2011-09-01
> **Frogs Hair said:**
> What used to be the control center...


Yup, that was it. Thanks!

---

