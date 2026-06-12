---
title: "Script file"
date: 2009-01-09
forum: General Help
---

### Post by mercerm on 2009-01-09
I have a server setup with ubuntu 8.10. I am running vsftpd and have a user chrooted so all the files they upload goes to their home folder. Is there a way to create a script that will check this folder every hour and if a file is found send the file to a shared folder on a windows server?

Thanks

---

### Post by strider1551 on 2009-01-10
Yes, that would be fairly simple with a quick bash script setup on a cron job.  Alternatively, if you used python and pyinotify, the script could monitor a directory and activate as soon as a file is uploaded.  As a disclaimer, I've never worked with a windows share, but I assume that you already have a simple way to move files there (scp?).

The only thing I can think of that may be a real problem is if a file is in mid transfer.  I don't know if a partially uploaded file appears in the destination folder or if it is uploaded to a temporary folder and simply moved once the upload is complete.  You can see where I'm going: something large is being uploaded, the script wakes up at the top of the hour and moves half of it.  The dirty fix would be to look at the time on the file and avoid anything that was last modified in the last ten minutes or so.

If I can find the time later today, I'll check on how vsftpd transfers files, and probably whip up a script for you.

---

### Post by strider1551 on 2009-01-10
As it turns out, partially uploaded files do indeed appear in the destination directory.

Here's something to get you started.  Please note that this will grab the files under /home/username for *every* user.  Also, I didn't put in the command to actually move the file.  Like I said, I have no experience with a windows shared folder, so I don't know if it can be mounted and a simple 'mv' will work, or if you need something like 'scp'.

Play around with it, see if you can make it work for your particular setup.

```

#! /bin/bash

# Find every file within a user's home directory that has been modified more
# than ten minutes ago.  If you wish to find subdirectories in addition to
# files, remove "-type f".
FILES=$(find /home -maxdepth 2 -type f -mmin +10 -print)

for f in ${FILES}; do
    # Just echo each filename for testing purposes.
    echo ${f}
    #mv ${f} /somewhere/else/
done

```

Let me know if that can help you, or if you need anything else.

---

### Post by mercerm on 2009-01-12
Wow thanks alot! I'll give it a try.

---

