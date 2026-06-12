---
title: "Please Help"
date: 2009-04-29
forum: General Help
---

### Post by elip89 on 2009-04-29
[IMG]http://i44.tinypic.com/34o1x0x.png[/IMG]????

---

### Post by spiderbatdad on 2009-04-29
it looks like you have added a ppa to your /etc/apt/sources.list. You need the key in a file, then add the key with sudo apt-key add filename.
Or comment out the entry in sources.list

---

### Post by mb_webguy on 2009-04-29
The fastest way would be to open the terminal and enter the command "sudo apt-get update".  You'll get an error message similar to the above.  Now copy the key id (the long string of letters and numbers starting with "FEFF") and enter the following commands, substituting your key id for *key_id*:```
gpg --keyserver keyserver.ubuntu.com --recv *key_id*
gpg --export --armor *key_id* | sudo apt-key add -

```
If you run "sudo apt-get update" again, you should no longer get the error.

---

### Post by elip89 on 2009-04-30
> **mb_webguy said:**
> The fastest way would be to open the terminal and enter the command "sudo apt-get update".  You'll get an error message similar to the above.  Now copy the key id (the long string of letters and numbers starting with "FEFF") and enter the following commands, substituting your key id for *key_id*:```
gpg --keyserver keyserver.ubuntu.com --recv *key_id*
gpg --export --armor *key_id* | sudo apt-key add -

```If you run "sudo apt-get update" again, you should no longer get the error.

Thanks men this method served me 100%

---

