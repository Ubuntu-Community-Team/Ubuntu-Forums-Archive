---
title: "gimp and libre office get lost in 12.04 lts"
date: 2012-09-19
forum: Desktop Environments
---

### Post by trev mesh on 2012-09-19
With gimp or LibreOffice (or both) running and then changing focus to somewhere else (eg a web browser), it's not possible to get back to gimp or LibreOffice via the launch bar. You have to minimise the  browser (or whatever) instead.  Changing to Ubuntu 2D on login avoids this problem.

Is this a bug?

---

### Post by newb85 on 2012-09-19
It's not normal behavior.

Before filing a bug report, make sure your system is up-to-date:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by trev mesh on 2012-10-15
This problem seems to have now been fixed. However, having used the Ubuntu 2D desktop for a while and now coming back, I notice a useful feature in Ubuntu 2D is missing in the main Ubuntu desktop: When you've got multiple files open in an application, clicking the launcher icon for the application displays the open documents along with the file's name (when you hover over it). It would be nice to add this 'hover' feature to the main offering.

---

### Post by trev mesh on 2012-10-15
Actually, there's still a problem with LibreOffice files. I just opened a .ods then saved it as a .csv  Couldn't then get back to it. Opened the original .ods then tried to save as .csv again: 'File already open...'

Back to Ubuntu 2D :-(

---

### Post by seaq on 2012-10-17
same issue here... :(

it seems related to this bug

[https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916](https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916)

---

### Post by papibe on 2012-10-17
or this one: [Bug #1033219]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1033219").

---

