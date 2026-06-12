---
title: "[SOLVED] scheduling with the 'at' command"
date: 2008-12-20
forum: General Help
---

### Post by patmanpato on 2008-12-20
Hi everyone. 

I'm having trouble getting the 'at' command to work. For example, i type:

at 17:53  <enter>
echo "hi" <enter>
ctrl+d 

yet "hi" never gets printed. if i replace the command 'echo "hi"' with something like  'firefox', still nothing.

I checked that the task is indeed scheduled with 'at -l' and after the time has passed, the task has been removed from the list. I also checked to make sure atd was running - which it was.

All the tutorials for 'at' seem to imply that what I entered should work.

Does anyone know why it's not working or have a simpler alternative solution? My goal is to be able to easily(quickly) do things like:
at 00:00 wget <big file>  for example. 


Any help greatly appreciated :popcorn:

---

### Post by dcstar on 2008-12-20
> **patmanpato said:**
> Hi everyone. 

I'm having trouble getting the 'at' command to work. For example, i type:

at 17:53  <enter>
echo "hi" <enter>
ctrl+d 

yet "hi" never gets printed. if i replace the command 'echo "hi"' with something like  'firefox', still nothing.
.......

You have not specified where the output should go, the system cannot guess that for you.

---

### Post by patmanpato on 2008-12-20
> **dcstar said:**
> You have not specified where the output should go, the system cannot guess that for you.

Yeah I thought that might be an issue, but the 'firefox' command wouldn't execute either, nor any other command I give it (eg touch /home/patman/testFile)

It's weird... there are no errors or warnings (beside the "warning: commands will be executed using /bin/sh").

Any ideas?

---

### Post by RealPSL on 2008-12-20
I tried the following and it worked for me:

```
$ at 09:51AM
warning: commands will be executed using /bin/sh
at> echo "Hi" > /tmp/hi.txt
at> <EOT>
job 3 at Sat Dec 20 09:51:00 2008

```

The file /tmp/hi.txt was created with the correct output. Are you sure your atd is running?

```
$ ps -ef | grep atd
daemon    9444     1  0 09:53 ?        00:00:00 /usr/sbin/atd

```

I think it is on by default. The other thing you can check is all these jobs are stored in /var/spool/cron/atjobs as files so you can just cat them to make sure it is executing what you think you told it to. One thing I noticed when I checked mine is that the job will exit if /var/spool/cron is not accessible. 

Last thing to check is make sure the user you are running the at job as is not in the /etc/at.deny file. You can check with ```
cat /etc/at.deny
```

---

### Post by patmanpato on 2008-12-20
ah. That worked. Thanks. I can echo "hi" > someFile.txt, 

However, I can't get it to do something like open up a program such as firefox or gimp etc. 
I tried just 'firefox', and also '/usr/bin/firefox', nor can I run a simple bash script that would normally open up a regular program if I ran it like './someScript.sh'

I don't have normal access to /var/spool/cron/atlist, and when I schedule a task, no file is created in /var/spool/cron/atlist. 

However a file is created when I run at at as root. Yet still I cannot run a simple program (eg amarok, firefox, gimp, etc.)


Am I missing something silly? 
Thanks for your help :guitar:

---

### Post by RealPSL on 2008-12-21
For gui programs you some how have to tell them which display to run on otherwise it will not work. I did the following for a GUI application:
```
$ at 00:46AM
warning: commands will be executed using /bin/sh
at> DISPLAY=:0.0 /usr/bin/gedit
at> <EOT>
job 5 at Sun Dec 21 00:46:00 2008
```

---

### Post by patmanpato on 2008-12-21
thanks, works like a charm :)

---

