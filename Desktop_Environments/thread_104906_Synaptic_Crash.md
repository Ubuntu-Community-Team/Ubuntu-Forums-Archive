---
title: "Synaptic Crash"
date: 2005-12-17
forum: Desktop Environments
---

### Post by davehard on 2005-12-17
Hi,
I open Synaptic Package Manager and it stays open for a bit, and then just closes after a second or two. I really have no idea why it is doing this.

I also don't know of anything I can paste here that will give you any information to help solve the problem but I will paste in a reply when advised.

---

### Post by kaamos on 2005-12-17
Try opening synaptic from the terminal by
```
sudo synaptic
```
My guess is the error message is "Segmentation fault" :(

---

### Post by davehard on 2005-12-17
Yep it seems to be Segmentation Fault:

When i type *sudo synaptic*:
```

(synaptic:10822): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:10822): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Segmentation fault

```

:???: Anything I can do to solve this?

---

### Post by kaamos on 2005-12-17
Do you have SCIM installed?

It seems someone resolved this by uninstalling it. [http://www.ubuntuforums.org/showthread.php?t=90028&page=2&highlight=synaptic+Segmentation+fault](http://www.ubuntuforums.org/showthread.php?t=90028&page=2&highlight=synaptic+Segmentation+fault)

You could also look here [http://www.ubuntuforums.org/showthread.php?t=98039&highlight=synaptic+Segmentation+fault](http://www.ubuntuforums.org/showthread.php?t=98039&highlight=synaptic+Segmentation+fault)

Try searching the forums, I hope someone has come up with a solid answer.

---

### Post by davehard on 2005-12-17
Thanks very much. The second link you gave me sorted the problem.

I had to clear the apt cache .bin files in /var/cache/apt/.

**For anyone with the same problem I advise to use this command:**
```

sudo rm /var/cache/apt/*.bin

```

Thanks very much for your help.

---

