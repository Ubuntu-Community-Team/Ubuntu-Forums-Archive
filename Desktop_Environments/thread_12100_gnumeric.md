---
title: "gnumeric"
date: 2005-01-21
forum: Desktop Environments
---

### Post by jaguar on 2005-01-21
How do I install it .....???

---

### Post by merinda on 2005-01-22
Here's how to install gftp
[http://www.ubuntuguide.org/#gftp](http://www.ubuntuguide.org/#gftp)

You can install gnumeric by that way too.

---

### Post by jaguar on 2005-01-25
well here's what I tried.......unsuccessfully though.....as you can see.......


$ sudo apt-get install gnumeric
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Package gnumeric is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
scrollkeeper
E: Package gnumeric has no installation candidate
$


I only have the CD repository.....[SIZE=7]Help[/SIZE]...

---

### Post by Viro on 2005-01-28
You need to follow [these](http://www.ubuntuguide.org/#extrarepositories) instructions to add additional repositories. Once that is done, do a "sudo apt-get update". This step is very important.

Now you should be able to install gnumeric.

---

