---
title: "user directory's are missing"
date: 2010-10-02
forum: Desktop Environments
---

### Post by Hoopz on 2010-10-02
I am new to linux and have been learning new commands etc.  I am running ubuntu 10.04 at the moment.  Anyway I used the commands useradd and passwd to create a new user and went to log in as that user and I got several errors looked like a home directory wasn't set up for that user.  Isn't the useradd command suppose to take care of this?

---

### Post by Hoopz on 2010-10-02
Here are the errors when logging in as the user I created. I get three of them.

1st error: Could not update ICEauthority file /home/travis/.ICEauthority

2nd Error: There is a problem with the configuration server.  (user/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

3rd Error: Nautilus could not create the following required folder: /home/travis/Desktop, /home/travis/.nautilus

then I am left at a blank desktop background and have to hit the reset button or do control alt f2 to get to a command line to shutdown the system

So my best guess is that the program that creates the user directories isn't working right but I am new to linux and I am not sure how to fix this

---

### Post by ankspo71 on 2010-10-02
Hi,
I just glanced through the useradd man page and it says this:
> -m, --create-home
           Create the users home directory if it does not exist. The files and directories contained in the skeleton directory (which can be
           defined with the -k option) will be copied to the home directory.

           By default, no home directories are created.
You can see this information by typing **man useradd** in the terminal.

---

### Post by sisco311 on 2010-10-02
From **man useradd**:
```
useradd is a low level utility for adding users. On Debian/**Ubuntu**, administrators should usually use adduser(8) instead.
```

EDIT: D'oh! ankspo71 beat me to it. [noparse]:)[/noparse]

---

### Post by Hoopz on 2010-10-02
ah ha!!  Guess I need to learn to use the man command as well.   Thanks to both of you.

---

