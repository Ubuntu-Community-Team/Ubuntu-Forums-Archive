---
title: "bash script permissions problem"
date: 2009-04-14
forum: General Help
---

### Post by colsandurz on 2009-04-14
Hello,  
this may need to be moved, I wasn't quite sure where to put this one. Anyways.

I am trying to write a script to generate an html file, then scp it over to a server.  I also want to automate the process using cron.

Here's my script, it's called cal_backup:
```

rem -p | rem2html > sched.html
#chmod 744 tmp_sched.html
scp -p sched.html user@server:path_to_sched.html
#rm tmp_sched.html

```

When I uncomment the chmod and rm and run the script in home it works fine.  When I move it to /usr/local/bin and do
```
$cal_backup
```
I get a permission denied error.  I think this is because /usr is owned by root.

Could I get around this just by making the user who runs the script root in my crontab file?  If that's the case, would I have to generate a new ssh key for that user?  (currently, I am using passwordless ssh with the server I am trying to scp to)

Or is there just some better approach to doing this?  Maybe using rsync??

---

### Post by sigmarhophi on 2009-04-14
> **colsandurz said:**
> Hello,  
this may need to be moved, I wasn't quite sure where to put this one. Anyways.

I am trying to write a script to generate an html file, then scp it over to a server.  I also want to automate the process using cron.

Here's my script, it's called cal_backup:
```

rem -p | rem2html > sched.html
#chmod 744 tmp_sched.html
scp -p sched.html user@server:path_to_sched.html
#rm tmp_sched.html

```

When I uncomment the chmod and rm and run the script in home it works fine.  When I move it to /usr/local/bin and do
```
$cal_backup
```
I get a permission denied error.  I think this is because /usr is owned by root.

Could I get around this just by making the user who runs the script root in my crontab file?  If that's the case, would I have to generate a new ssh key for that user?  (currently, I am using passwordless ssh with the server I am trying to scp to)

Or is there just some better approach to doing this?  Maybe using rsync??

if you can chmod the file, then try:

sudo chmod ugo+x cal_backup

this makes it executable by everyone, but not modify it.

---

### Post by Alekz_ on 2009-04-14
Hey!

Try this one:

```
rem -p | rem2html > /tmp/sched.html
#chmod 744 /tmp/tmp_sched.html
scp -p /tmp/sched.html user@server:path_to_sched.html
#rm /tmp/tmp_sched.html
```

You probably have permission denied couse you're trying to save a file into /usr (as you said).

[]'s

Alekz_

---

### Post by askreet on 2009-04-14
Your assumption is correct about chmod.  Your user can't chmod anything inside of /usr, you will need to run the script as root.

When you do that, you will need to move the config/key to the root .ssh directory.

To do this the "correct" unix way, your script should:
- live in /usr/local/bin
- be run as root
- create an .html file in /tmp/something.html
- *not* chmod this file
- scp the file
- delete the file

HTH
- askreet

---

### Post by colsandurz on 2009-04-14
ahhh using the /tmp directory did it.  Thanks everyone.

here's how the script is now, if anyone is curious.

```

#!/bin/bash
rem -p | rem2html > /tmp/sched.html
scp -p /tmp/sched.html user@server:path_to_sched.html
rm -f /tmp/sched.html

```

Thanks again!

---

