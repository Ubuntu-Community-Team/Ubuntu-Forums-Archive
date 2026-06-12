---
title: "Package manager failed"
date: 2009-03-13
forum: General Help
---

### Post by girishsdca on 2009-03-13
I recently ran the Package Manager to update using the update icon. I received an error telling me to manually run dpkg --configure -a, which said: dpkg: parse error, in file `/var/lib/dpkg/status' near line 12832 package `libpulse0': newline in field name `/usr'.

I tried editing /var/lib/dpkg/status at that location but it didn't help, just keep getting more such errors. Then I copied status-old to status but it also had similar errors that my editing didn't help.

How can I solve this problem?

---

### Post by komputes on 2009-03-14
The following commands may help:

```
sudi apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by girishsdca on 2009-03-14
> **komputes said:**
> The following commands may help:

```
sudi apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```


The first command fails part way through and says to run the second command. The second command has the same error as my original post. The third command fails immediately and says to run the second command.

---

