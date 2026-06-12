---
title: "&quot;Users and Groups&quot; / user-admin does not prompt/run with administrator privileges"
date: 2009-02-23
forum: General Help
---

### Post by rnsc on 2009-02-23
The System / Administration / Users and Groups dialog has everything grayed out so that I cannot modify anything (Logged on to the account created during installation).  The "Help" button in the dialog talks about starting it from the command line, and indicates that it will prompt for the administrative password so that changes can be made.

Neither mode of starting (Menu or commandline) prompts for the administrator password.

Is this a bug?  How can I get around it?

Thanks.

---

### Post by mb_webguy on 2009-02-23
Is the Unlock button also disabled?

---

### Post by snova on 2009-02-23
Well, the Unlock button should do it, but if you can't, press Alt-F2 and type in:

```
gksudo users-admin
```

---

### Post by whoop on 2009-02-23
It's funny, it works for me but if I gksudo admin-users the unlock button is disabled and so is add user and the like.

---

### Post by rnsc on 2009-02-23
I, evidently, am blind.  How I I missed it, I can't imagine.  Thank you.

The help file DOES say "When you start Users Administration Tool, you will be prompted for the administrator password, this is necessary because the changes done with this tool will affect the whole system."

But given the "Unlock" button, this is immaterial, and I would argue probably a better design (One can browse without unlocking).

---

