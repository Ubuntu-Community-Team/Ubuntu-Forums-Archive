---
title: "gnome-schedule"
date: 2008-10-13
forum: Desktop Environments
---

### Post by atheon on 2008-10-13
Hi,

I've written a shell script and used gnome-schedule to schedule it to run periodically. It works as intended when i hit the "run task" button but not when it's scheduled to.

Any idea what could be wrong? Thanks in advance.

---

### Post by prshah on 2008-10-13
> **atheon said:**
> 
I've written a shell script and used gnome-schedule to schedule it to run periodically. 

Well I don't know about gnome-schedule (just heard of it) but I run shell scripts periodically using cron; [here's a post that show how cron is used]("http://ubuntuforums.org/showpost.php?p=5243619&postcount=3").

Maybe this will help?

---

### Post by atheon on 2008-10-13
Thanks prshah for your prompt reply.

It's not working as well. From what I can tell is that the script is being executed but not all of it. The beginning and the end of the script was executed but skipped the middle part.

Also, i'm running the script with a wine command as well.

---

### Post by atheon on 2008-10-13
Here's a sample of the script that i wrote. Hopefully it will be some help.

```

if [ -f /media/cdrom0/software.exe ]
  then
    wine /media/cdrom0/software.exe
    eject
else
    echo "File not found."  #debug
fi

```

When I run it in terminal, it works fine.

---

### Post by atheon on 2008-10-16
bump.

Still can't get it working thru cron.

---

