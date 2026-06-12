---
title: "scripts with sudo command"
date: 2009-06-16
forum: General Help
---

### Post by arron on 2009-06-16
I have some code in a script, but i get permission errors, this is what i want to do:

```

sudo echo "Test text" >> /var/log/testlog

```

All i want to do is append some data to a file that is only sudo access.  But when I run this i get permission errors.  I think "echo" is running as sudo, but the >> is under normal user power.  Yes the file exists.

How can I do this is a shell script?

---

### Post by sdennie on 2009-06-16
Try:

```

sudo sh -c "echo foo >> bar"

```

The output redirection doesn't get the sudo privileges otherwise.

---

### Post by arron on 2009-06-16
thanks, worked like a charm, just needed a \, ie

```

sudo sh -c "echo \"foo\" >> bar"

```

Thanks!

---

