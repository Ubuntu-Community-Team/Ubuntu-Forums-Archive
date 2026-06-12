---
title: "usermod -p will not run from crontab"
date: 2009-04-23
forum: General Help
---

### Post by johanneslandin on 2009-04-23
Ubuntu 8.04 LTS, crontab -e, usermod -p

I got this script to reset passwords for users. It works fine when I run it as root, but I have to sudo the usermod command to make it work from crontab. I guess it will work if crontab sudo the script as well. 

Is this a bug or is it security?    

#!/bin/bash
#...
UN="Username"
PW="`mkpasswd "Password"`"
#...
sudo usermod -p "$PW" "$UN"
#...

---

### Post by loomsen on 2009-04-23
Start the crontab editor prefixed with 

## Get root
sudo su -
## Edit your crontab
/usr/sbin/cron* -<options>
## Set it up, save it and exit rootshell again
exit
## You should be loged in as ur usr again and the tab should run without sudo

---

### Post by johanneslandin on 2009-04-23
Same result, I forgot to tell I was running crontab as root ...

I tried to add the usermod command directly in crontab with the same result, but sent the output to /root/test.log:
 
[INDENT]$ su -
$ crontab -e
* * * * * usermod -p "`mkpasswd "Password"`" "testuser" 2>> /root/test.log

$ cat test.log
/bin/sh: usermod: not found
### Looks like crontab is running the script with /bin/sh(!)?[/INDENT]

When I add sudo before usermod it works fine:
[INDENT]$ su -
$ crontab -e
* * * * * sudo usermod -p "`mkpasswd "Password"`" "testuser" 2>> /root/test.log

$ cat test.log
### No error, and password is "Password"[/INDENT]

Is sudo using roots default shell but crontab not? And if so, why is the shebang in the first line of the script ignored?

---

### Post by amac777 on 2009-04-23
I think the problem is that you don't specify the full path of the program usermod in the crontab file. You are relying on a PATH that doesn't exist in crontab. From your description, I would guess that using sudo somehow incorporates the path. Also, to answer your question of why the shebang in the first line of the script is ignored - it isn't being ignored, it just doesn't have anything to do with cron calling usermod. (That script is only executed when called by mkpasswd.)

Anyway, to solve your problems, you probably just have to use absolute paths in the crontab.

---

### Post by johanneslandin on 2011-10-13
Yes! I remember that full path solved the problem.

---

### Post by sisco311 on 2011-10-13
Please don't bump old threads.

Closed.

---

