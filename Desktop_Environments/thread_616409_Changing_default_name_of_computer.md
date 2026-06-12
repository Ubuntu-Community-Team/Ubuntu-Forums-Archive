---
title: "Changing default name of computer"
date: 2007-11-18
forum: Desktop Environments
---

### Post by dascabins on 2007-11-18
I have a compaq computer and I want to change or stop the compaq name from being loaded how do I go about changing it?

---

### Post by rbalfour on 2007-11-18
> **dascabins said:**
> I have a compaq computer and I want to change or stop the compaq name from being loaded how do I go about changing it?

Are you talking about the logo when the computer first boots?
If so, you can't unless you reflash the bios. Highly NOT recommended for any computer.
Try a Google search for changing the BIOS.

---

### Post by tlayton_at_work on 2007-11-18
I believe your talking about the name that shows from the command uname.  If so, you need to change it in both /etc/hostname and /etc/hosts.  You must do it in both, otherwise I don't think Linux will boot properly.

---

