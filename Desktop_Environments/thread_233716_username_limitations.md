---
title: "username limitations"
date: 2006-08-10
forum: Desktop Environments
---

### Post by crumbs516 on 2006-08-10
I have been using linux for several years now. Regardless of the distribution I've always used the same username. **My username has an underscore in it.** Recently I decided to give Ubuntu a try. I downloaded the alternate i386 disk and installed it in vmware.

After the install I tried to configure my standard user name and **the Ubuntu user/groups editor gui reported the following error**:

**"User name has invalid characters"**

Ubuntu is the first distribution to balk at my user name. In fact I can change the username at the command line using "usermod" but I do not know how to change the home directory after the fact to match the username without using the gui.

[I]How do I change the user home directory location from the command line?

Why does Ubuntu care if I have an underscore in my username?
[/I]

---

### Post by Ramses de Norre on 2006-08-10
```
usermod -d directory -m username
```
will change the home dir of *username* to *directory* and the -m option tells usermod to include all contents of the current home dir.

---

### Post by crumbs516 on 2006-08-10
The gui's error can be circumvented in the following way...

Use usermod to change the user name back to something acceptable by the gui. Then use the gui to change the home path to the desired path matching the invalid user name.

From the command line as root the desired user home directory can be created with the correct owner and group (chown). The old and new home directories can then be synced using rsync before removing the original path.

Then use usermod to change the user name to the name with the underscore.

---

### Post by crumbs516 on 2006-08-10
looks like I should have read the man page for usermod

Thanks for the help

---

### Post by Ramses de Norre on 2006-08-10
I got it from the man page too, man pages are the number one resource for questions about commands ;)

---

