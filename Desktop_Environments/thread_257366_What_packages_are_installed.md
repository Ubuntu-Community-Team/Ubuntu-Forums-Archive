---
title: "What packages are installed?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by crag277 on 2006-09-14
I'm thinking about giving my laptop a fresh install of Ubuntu for a variety of reasons, but I've installed tons of packages along the way, and there's no way I remember all of them.

Is there a way for Synaptic, or some other program, to generate a list of all packages that I've installed on this system so I know what to install after the fresh OS install?

Thanks.

---

### Post by wrob on 2006-09-14
```
dpkg --list >> packages
```

this will create a file called "packages" with a list of all the packages installed

---

### Post by crag277 on 2006-09-14
Excellent, thank you.

---

### Post by skymt on 2006-09-14
Synaptic can save a "markings" file that contains the install state of every package on the system. It's in the file menu. Just make sure to check the box that tells it to save the full state, not just changes.

Then just open the file on your new system and hit run!

---

### Post by llamakc on 2006-09-14
> **crag277 said:**
> I'm thinking about giving my laptop a fresh install of Ubuntu for a variety of reasons, but I've installed tons of packages along the way, and there's no way I remember all of them.

Is there a way for Synaptic, or some other program, to generate a list of all packages that I've installed on this system so I know what to install after the fresh OS install?

Thanks.

sudo dpkg --get-selections > packages-to-reinstall

...

Reinstall (after emailing the file 'packages-to-reinstall' to yourself somewhere safe, or storing in another fashion).

...

dpkg --set-selections < packages-to-reinstall

...

dselect (press 'i' to install the software)

---

