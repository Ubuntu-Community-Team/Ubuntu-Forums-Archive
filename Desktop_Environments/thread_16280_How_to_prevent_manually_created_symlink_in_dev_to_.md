---
title: "How to prevent manually created symlink in /dev to disappear on reboot?"
date: 2005-02-20
forum: Desktop Environments
---

### Post by istoyanov on 2005-02-20
I order to hear a sound from a radio tuner card I needed to create manually the symlink /dev/radio -> /dev/radio0.

After a reboot I was suprised to see that the newly created link do not exist anymore.

How can I make this link last longer?

---

### Post by Juergen on 2005-02-21
I'm no expert on udev, but /etc/udev/links.conf looks promising.

---

### Post by Juergen on 2005-02-21
I'm no expert on udev, but /etc/udev/links.conf looks promising.

---

### Post by piedamaro on 2005-02-21
You have to add a rule for udev here:
/etc/udev/udev.rules

see the other entries for example.

---

### Post by istoyanov on 2005-02-21
Thank you for the input!

However, I need some more advice on modifying /etc/udev/udev.rules.

I think that my entry should be similar to:
```

# /dev/cdrom symlink
BUS="ide", KERNEL="hd[a-z]", PROGRAM="/etc/udev/cdsymlinks.sh %k", SYMLINK="%c{1} %c{2}"

```

I suppose that in my case KERNEL="radio[0-9]", but I have really no idea what should be the "BUS" and the "SYMLINK" variables.

Any ideas?

Cheers!
---
Edit: On the Gentoo forum I found meanwhile the following:
```

# v4l devices
KERNEL="video[0-9]*",   NAME="v4l/video%n",     SYMLINK="video%n"
KERNEL="radio[0-9]*",   NAME="v4l/radio%n"
KERNEL="vbi[0-9]*",     NAME="v4l/vbi%n",       SYMLINK="vbi%n"
KERNEL="vtx[0-9]*",     NAME="v4l/vtx%n" 

```
Perhaps I have to append SYMLINK="radio%n" to the secong row?
I'll try this and post the results back.

---

### Post by piedamaro on 2005-02-21
KERNEL and NAME should be enough (I believe).

---

