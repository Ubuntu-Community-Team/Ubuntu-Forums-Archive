---
title: "FTP backup"
date: 2009-01-03
forum: General Help
---

### Post by Eviltechie on 2009-01-03
I found a ftp backup script, and modified it to my liking.
```
#!/bin/sh
USERNAME="your-ftp-user-name"
PASSWORD="anonymous"
SERVER="192.168.2.50"

# local directory to pickup file
FILE="/home"

# remote server directory to upload backup
BACKUPDIR="/ivan-ubuntu"

# login to remote server
ftp -n $SERVER <<EOF
user $USERNAME $PASSWORD
cd $BACKUPDIR
mput $FILE
quit
EOF
```

I have two questions about this script though. 1)What exactly will it do? 2)How will I make it work.

---

### Post by cybiko123 on 2009-01-03
That basically takes every file in your home directory and backs it up to /ivan-ubuntu on the server. As for making it work, what happens when you try it now?

---

### Post by pizmooz on 2009-01-03
When you do authentication for FTP in a script you need to use the 'quote' command for it to work:

```

# login to remote server
ftp -n $SERVER <<EOF
quote USER $USERNAME
quote PASS $PASSWORD
cd $BACKUPDIR
mput $FILE
bye
EOF
```

If possible I would suggest using rsync over ssh for remote backups.  It is easier to script, more robust and more much more secure than ftp.

---

### Post by HermanAB on 2009-01-03
FTP is mostly useful for Windows machines.  On Linux you should use rsync over SSH. Here are some things that may help:
[http://aeronetworks.ca/windows-backup.html](http://aeronetworks.ca/windows-backup.html)
[http://aeronetworks.ca/rsync-ssh-howto.html](http://aeronetworks.ca/rsync-ssh-howto.html)

Cheers,

Herman

---

