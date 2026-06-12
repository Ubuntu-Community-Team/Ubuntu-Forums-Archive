---
title: "sudo command in scripts"
date: 2006-08-09
forum: Desktop Environments
---

### Post by faulkner132 on 2006-08-09
How do you execute a command you need to run as root in an (unattended) automated script?

For example, execute:
```
sudo rm /path/to/file/to.delete
```
in a scheduled script?

---

### Post by cstudent on 2006-08-09
```

echo yourpassword | sudo rm /path/to/file/to.delete

```

---

### Post by faulkner132 on 2006-08-09
That was the first thing I tried. It doesn't work as it still prompts for your password.

Any other suggestions?

---

### Post by deeek on 2006-08-09
> **cstudent said:**
> ```

echo yourpassword | sudo rm /path/to/file/to.delete

```

That should actually be:

```

echo yourpassword | sudo -S rm /path/to/file/to.delete

```

Note the -S.  Check the man page for sudo for more info.

---

### Post by cstudent on 2006-08-09
Not when it is run from inside a script.

---

### Post by cstudent on 2006-08-09
Thank you Deeek for correcting me. I forgot about the -S switch.

---

### Post by deeek on 2006-08-09
> **cstudent said:**
> Not when it is run from inside a script.
It works for me.

EDIT:

> Thank you Deeek for correcting me. I forgot about the -S switch.

No problem.  ;)

---

### Post by faulkner132 on 2006-08-15
Beautiful.
Thanks so much guys.

---

### Post by Tomosaur on 2006-08-15
Can't you just run the script as sudo?

---

### Post by Ramses de Norre on 2006-08-15
Running the script with sudo looks safer to me too.. Or otherwise turn off read permissions for everyone because otherwise your password is pretty easy to retrieve..

---

### Post by huygens on 2006-08-29
If you want to try perhaps a safer way (not puting the password in the script), you could watch here: [http://ubuntuforums.org/showthread.php?t=245618](http://ubuntuforums.org/showthread.php?t=245618)

---

