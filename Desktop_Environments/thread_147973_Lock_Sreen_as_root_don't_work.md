---
title: "Lock Sreen as root don't work"
date: 2006-03-21
forum: Desktop Environments
---

### Post by peterbras on 2006-03-21
When click "Lock Sreen" as root, there is no reaction. How to fix?

---

### Post by ajgreeny on 2006-03-21
Do you mean you are logged in to root in a gui environment such as gnome or kde?  If so why?  If not then I don't quite see what you mean as you won't be root anyway.  More info please.

---

### Post by yanik on 2006-03-21
The application that locks the screen is xscreensaver, which doesn't run as root.

---

### Post by ardchoille on 2006-03-21
It doesn't need to be run as root. If you are logged into the desktop environment as root user, then that is a very bad idea.

---

### Post by yanik on 2006-03-21
sorry about that, I was refering to my RHEL workstation, might be different on Ubuntu, I'll look into it when I get home.

Here's what RHEL says:
```

xscreensaver: This is probably because you're logging in as root.  You
              shouldn't log in as root: you should log in as a normal user,
              and then `su' as needed.  If you insist on logging in as
              root, you will have to turn off X's security features before
              xscreensaver will work.
```

---

