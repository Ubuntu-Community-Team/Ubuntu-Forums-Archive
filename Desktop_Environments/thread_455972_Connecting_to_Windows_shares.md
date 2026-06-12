---
title: "Connecting to Windows shares"
date: 2007-05-27
forum: Desktop Environments
---

### Post by tailwindALWAYS on 2007-05-27
A little background ...
I have multiple computer labs my support team maintians and we have used Debian for years.  I decided to go with Ubuntu this time!  :)  I'm actually going to have it run virtually using VMware player installed on Windows using NAT'ed IPs.

We have been having trouble connecting to Windows file shares from the labs since the shares are on a different Windows AD domain, so we been hosting another Linux server just for these Linux shares.  In Ubuntu however, I was able to choose 'Places | Connect to Server' and connect to my Windows share.  I thought for sure it wasn't going to work.  A couple questions ... once I did that I wasn't able to find my share via command line; how does it mount it and how can I get to it?  Also, does anyone know what the command it runs is?  I would like to have this automatically mounted for the students if possible.

THANKS SO MUCH!

---

### Post by tailwindALWAYS on 2007-05-27
OK, i don't have it all figured out yet, but i'm close!

after following bmizer's awesome tutorial on mounting windows shares ([http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)) i was able to tweak the command and get it to work.  i'm current running the following command after installing smbfs:
   ```
mount -t cifs //server1/fileshare /localfolder -o username=myusername,password=mypassword,domain=mydomain
```

now the catch is, how can i mount the subfolders.  for instance on the server here's is what it kind of looks like:
[FONT="Courier New"]* sharename        [Windows Share]
--* user         [subfolder with no sharing emabled]
----* tsmith    [example user i wish to have auto mounted][/FONT]

i tried adding the /share/user/tsmith to the command but it's not working.  any ideas?  thanks a bunch!!!!

EDIT: wow, can this be true?????  you can't mount sub folders of shares?  any ideas on what's the best way to automount user accounts then?  i don't want to drop users into the main share then have them navigate to their account.

---

