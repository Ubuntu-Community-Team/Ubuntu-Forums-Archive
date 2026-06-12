---
title: "X11R6: cannot open localhost:0.0"
date: 2008-11-17
forum: Desktop Environments
---

### Post by halfant on 2008-11-17
Suppose I want xeyes to pop up on another ubuntu PC on my home network. "xeyes -display othername:0.0" doesn't work even though I've invoked "xhost +" on the target machine. In fact I can't use localhost to pop it up on my own display (although it works if I just omit the -display option).

Is this an issue of permissions, or has GNOME remapped the syntax for identifying a display? Is there a utility that will print identification suitable as an argument to the -display switch?

Please be explicit in your answer, preferably giving one or two examples -- I used Unix years ago and was a novice then.

Thanks,
Matthew

---

### Post by hictio on 2008-11-17
Does the box you want to export the xeyes have an sshd server running? Do you have an account on that box?

Then, connect from your Ubuntu box, like this, from a Terminal:

```

ssh -X -l username.here ip.other.Ubuntu.box (ENTER)

```

Once connected to the remote Ubuntu box, on the same Terminal, type 'xeyes; and it should open on your own box, but exported from the other one, and the best thing, the whole thing will be encrypted.

---

### Post by halfant on 2008-11-18
Thank you for your reply. Although it didn't solve my original problem, it has proven useful in other ways.

---

