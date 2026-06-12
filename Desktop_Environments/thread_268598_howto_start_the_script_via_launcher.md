---
title: "howto start the script via launcher ?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by cccc on 2006-09-30
hi

I have dapper drake with Gnome.
howto start the python script on the desktop using launcher ?

```

#!/usr/bin/python

# Password protector
import os, sys, sha, getpass

# Read in hash
hash_file = open("/home/ania/.password_protect", "r")
hash = hash_file.read()

# Get new hash
pwhash = ''
counter = 0
while pwhash != hash:
    pwhash = sha.sha(getpass.getpass("Password: ")).hexdigest()
    counter += 1
    if counter > 3:
        sys.exit()

os.system("/usr/bin/mozilla-thunderbird")
```


I have created a launcher on the desktop using this command:```

/home/user/mail.py
```
try a double click on the icon, but it doesn't work !

---

### Post by dcstar on 2006-10-01
> **cccc said:**
> hi

I have dapper drake with Gnome.
howto start the python script on the desktop using launcher ?
.......
I have created a launcher on the desktop using this command:```

/home/user/mail.py
```
try a double click on the icon, but it doesn't work !

Are the file permissions set to Executable?

---

### Post by cccc on 2006-10-01
> **dcstar said:**
> Are the file permissions set to Executable?

yep, but run in terminal solved this problem.

---

