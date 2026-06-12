---
title: "rsync, going out and grabbing info"
date: 2005-11-28
forum: Desktop Environments
---

### Post by afonit on 2005-11-28
in all of the documentation I have read so far, and having used rsync successfully for taking local data and pushing it to another computer - 


ie.) first example - rsync -a -e ssh /local directory/ [email]pigfat@pigfat.com[/email]:/destination server's directory/



I however cannot and cannot find documentation on how to use rsync to go out and grab data from another computer and back it up on a local drive.

I would like to know if anyone has used it to go out and grab data from a server and backed it up locally, and how they did it.

---

### Post by lnxconvrt on 2005-11-28
The form is rsync [options] source destination, so just put the remote server in the source place and your local box that you want to copy to in the destination position:

rsync -a -e ssh [email]pigfat@pigfat.com[/email]:/destination server's directory/ /local directory/

---

### Post by afonit on 2005-11-28
oh man, that is so simple, but works perfectly, thank you very much for the clarification that you provided me.

---

