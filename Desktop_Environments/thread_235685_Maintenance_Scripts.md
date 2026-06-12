---
title: "Maintenance Scripts"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Koori23 on 2006-08-13
Okay,

I know that Ubuntu keeps various things that waste space (i.e. keeping .deb files after installation), I want to know if anyone knows where I can either write or download a shell script that will do the following:

Clear the /var/cache/apt/archives folder. Currently, I **sudo rm -f /var/cache/apt/archives/*.deb**, can I make this a shell script and cron it or something? If so, how would I write that?

Also, I would like to make a script that empties the trash folder on it's own... I can't seem to figure out where exactly that folder is.

Anyway, I'm just very interested in automating maintenance tasks, any assistance would be helpful.

Thanks

---

### Post by chrisccoulson on 2006-08-13
My understanding with trash is that Nautilus doesn't store files in one single trash folder, but rather they are stored in hidden folders (one for each mounted device/user), with a name in the format .Trash-<user>

---

### Post by ardchoille on 2006-08-13
> **Koori23 said:**
> Okay,

I know that Ubuntu keeps various things that waste space (i.e. keeping .deb files after installation), I want to know if anyone knows where I can either write or download a shell script that will do the following:

Clear the /var/cache/apt/archives folder. Currently, I **sudo rm -f /var/cache/apt/archives/*.deb**, can I make this a shell script and cron it or something? If so, how would I write that?

Also, I would like to make a script that empties the trash folder on it's own... I can't seem to figure out where exactly that folder is.

Anyway, I'm just very interested in automating maintenance tasks, any assistance would be helpful.

Thanks

Yes, you can make that a shell script. It would be like this:

```

#!/bin/bash
rm -f /var/cache/apt/archives/*.deb


```

Create a new file with a filename of emptypkgs.sh or something. Add the above code to that file. Make that file executable with chmod u+x emptypkgs.sh and place it in a convenient location, I created a ~/.bin dir and I put all my scripts in there. You'll need to run the script with "sudo ./emptypkgs.sh" (you'll need the path I beleive) because that directory can only be emptied by root.

If you want to be reminded, or want the script to check for root privs, you can add some code to check for that:

```

#!/bin/bash

# check for admin privileges
if [ $UID != 0 ]
then
   echo "You need to be root to run this script. Please contact your administrator."
   exit
fi

rm -f /var/cache/apt/archives/*.deb

```

Lines 4 - 8 will check to see if the user running the script has admin privs (root, sudo, su, etc.) and, if not, print "You need to be root to run this script. Please contact your administrator." and exit the script.

---

### Post by GTvulse on 2006-08-13
> **Koori23 said:**
> 
Clear the /var/cache/apt/archives folder. Currently, I **sudo rm -f /var/cache/apt/archives/*.deb**, can I make this a shell script and cron it or something? If so, how would I write that?


Add this to your crontab (read the manual pages for crontab(1), crontab(5),  and man(1), that won't maim you):

```

@weekly  /usr/bin/aptitude clean

```

That line above will purge /var/cache/apt/archives every week. If your machine is not up at the time it should run, anacron will take care of the task as soon as you boot up your machine at any time after the scheduled time.

---

