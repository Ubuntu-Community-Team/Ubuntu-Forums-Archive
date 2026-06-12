---
title: "Process status check fails in CRON"
date: 2015-06-04
forum: Fedora/RedHat and derivatives
---

### Post by andrew102 on 2015-06-04
Ok, so I have a job that runs and depends on files in Dropbox. Essentially I have a checkpoint to make sure that dropbox isn't downloading new files before running the job.

Here's the code:

```

CUR_STATUS=$(dropbox status)

if [ "$CUR_STATUS" = "Up to date" ]; then
        echo "$CUR_STATUS" > $DIR/test.log
else
        echo "dropbox isn't updated" > $DIR/test.log
        echo "status is : +$(/usr/bin/dropbox status)+" >> $DIR/test.log
        echo "running is : +$(/usr/bin/dropbox running)+" >> $DIR/test.log
        echo "whoami: +$(whoami)+" >> $DIR/test.log
        echo "debug early exit" >> $DIR/test.log
        exit_flag=1
fi

```

There's a few extra lines for debugging purposes but essentially this WORKS when running the script manually in terminal. AND it also ran under cron in a Ubuntu machine until we decided to move over to CentOS where it has now broken.

I think the problem lies in CRON but cannot work out why or how?

Andrew

---

### Post by andrew102 on 2015-06-04
To clarify:

Run manually - status is "Up to date"
Under CRONTAB - status is "Dropbox isn't running!"

I have the package nautilus-dropbox installed (Version     : 2015.02.12
Release     : 1.fc10)

And dropbox looks to be v3.4.6 - ~/.dropbox-dist/dropbox-lnx.x86_64-3.4.6/

---

### Post by matt_symes on 2015-06-05
Hi

```
CUR_STATUS=$(dropbox status)
```

Use the full path to dropbox and whoami.


Cron has a sanitised environment for security reasons and will not contain many of your environmental variables including your PATH variable so use full paths otherwise cron will not know where to look for executables.

**EDIT:**

I think that it may be missing a number of paths including the path to your home directory for ~/.dropbox-dist/dropbox-lnx.x86_64-3.4.6/

My point is, look at your cron's PATH and other environmental variables that dropbox may need when run from cron.

Kind regards

---

### Post by andrew102 on 2015-06-11
Thanks for your reply.

This code is extracted from the script, so the PATH= is there but not shown in this thread.
I already had /usr/bin and /home/user/Dropbox.
Adding /home/user/.dropbox-dist did not make a difference.

dropbox status returns "Dropbox isn't running!"
dropbox running returns 0

Still haven't worked it out. All I know is it was working fine in Ubuntu before. So figured maybe there are some extra "features" of CentOS that prevent cron from working as expected.

---

### Post by andrew102 on 2015-06-11
I think I found the solution:

HOME=/  [change this to /home/<my-user>]

Add:
USER=<my-user>

to /etc/crontab

Now dropbox status says "Up to date" - yay!
dropbox running still returns 0 but this isn't so important as we can just equate on the string.

---

