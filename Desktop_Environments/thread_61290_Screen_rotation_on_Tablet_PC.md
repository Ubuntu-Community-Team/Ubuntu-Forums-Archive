---
title: "Screen rotation on Tablet PC"
date: 2005-08-31
forum: Desktop Environments
---

### Post by andrewsawyer on 2005-08-31
Hey all,

I have an Acer tablet laptop, which in Windows allows you to rotate the screen through 90 degrees for reading ebooks etc.

Unfortunately in Ubuntu, I've found no way to do this.  I've got special keys on my laptop, however these don't work, and I've tried using xrandr however it gives the following error:

```
andrew@ubuntu:~$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
andrew@ubuntu:~$
```

I've also tried this using sudo but get the same error.  Can anyone help me with this?  Any ideas would be greatly appreciated.

Andy

---

### Post by moises on 2005-08-31
I've just found this: [http://keithp.com/~keithp/talks/randr/](http://keithp.com/~keithp/talks/randr/) : The X Resize and Rotate Extension - RandR

---

### Post by moises on 2005-08-31
The description of the libxrandr2 package says:
The X.Org X server does not yet support the rotation aspects of this extension.
...

---

### Post by andrewsawyer on 2005-08-31
So does this mean that it's not possible?

---

