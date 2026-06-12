---
title: "Easiest way to email a file from the command line"
date: 2009-04-12
forum: General Help
---

### Post by Warpnow on 2009-04-12
I want to write a script which when ran tars up a directory and emails it to an email address, then promptly deletes the file to preserve space. 

I know how to do the rest but what's the best way to email a file from the command line?

---

### Post by lovinglinux on 2009-04-12
Use sendEmail.

Install:

```
sudo apt-get install sendemail
```

Usage:

```
sendEmail -f username@foo.com -t destination@foo.com -u "The Subject" -m "The message" -a /home/user/the_attachment.zip -s smtp.foo.com:25 -xu username -xp password
```

---

