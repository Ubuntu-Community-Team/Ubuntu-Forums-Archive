---
title: "changing ownership"
date: 2009-05-30
forum: General Help
---

### Post by StOoZ on 2009-05-30
I have several directories on my computer , which belongs to a different user ( which I created, for a ftp access). now , I want to remove them , but , when im logged to my user...
I have the ftp's user name + password.
I tried several ways , but to no avail...

---

### Post by merlinus on 2009-05-30
Running nautilus as root should let you delete them.

In a terminal:

```

gksudo nautilus

```

---

### Post by x33a on 2009-05-30
if you want to use nautilus, then don't move the files to trash, instead delete them straight. because, otherwise the files will be sent to the root trash and not to the normal trash.

or, use sudo rm.

---

### Post by StOoZ on 2009-05-30
ok thanks , but apparently I wasnt so clear ..
How do I run a command as another user , without logging of from the current user???
I meant that I want to delete the ftp's user files , as the user itself , without logging off my user and signing in as the user ftp.

thanks a lot!

---

### Post by x33a on 2009-05-30
yes, you can achieve that with

```
sudo -u <username>
```

but, you might have to edit sudoers to achieve this. i am not sure, cause i haven't tried this myself. please, post the result.

---

