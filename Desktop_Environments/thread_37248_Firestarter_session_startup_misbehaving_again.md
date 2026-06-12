---
title: "Firestarter session startup misbehaving again"
date: 2005-05-26
forum: Desktop Environments
---

### Post by Rehevkor on 2005-05-26
In the process of installing and setting up eterm, I somehow reproduced the error with firestarter where, during session startup, it insists that it must be run with root privaleges. I get the error window for that, but firestarter appears to be running anyway. So annoying :-x 

I have the correct entry for firestarter in the sudoers file, I have it added to my session startup programs with "sudo firestarter --start-hidden" and I've changed the start order of it a dozen times. Nothing I've tried will get rid of this stupid error message.

So what can I do, short of uninstalling the dumb thing?

---

### Post by stevenyu on 2005-05-26
when Gnome ask do you want to save the current gnome session, select no, otherwise it will try to open another firestarter for you when you login the next time

---

### Post by Rehevkor on 2005-05-26
When I tried to fix eterm I saved the session once, and firestarter was running. How can I fix that?

---

### Post by Rehevkor on 2005-06-02
It seems as if firestarter is starting normally from where I added it to my startup programs, but it's also trying to start from somewhere else without sudo.

Does anyone know how I can fix this?

---

