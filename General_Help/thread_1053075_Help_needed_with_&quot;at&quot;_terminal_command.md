---
title: "Help needed with &quot;at&quot; terminal command"
date: 2009-01-28
forum: General Help
---

### Post by sagesparrow on 2009-01-28
I need some help with the "at" command.   
As a test, I created a script to turn on a program - in this case gyachi.   The file is ~/gyachi.sh
When I run ~/gyachi.sh in terminal, it starts gyachi perfectly.

Now, in trying to use "at" to start gyachi in 1 minute, the following in terminal:

jk@ub:~$ at now + 1 minute
warning: commands will be executed using /bin/sh
at> ~/gyachi.sh
at> <EOT>
job 10 at Wed Jan 28 10:21:00 2009
jk@ub:~$ at -l
10	Wed Jan 28 10:21:00 2009 a jk
jk@ub:~$ mail
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/mail/jk": 8 messages 2 new 8 unread
 U  1 jk@ub              Tue Jan 27 16:21   20/930   Output from your job       
 U  2 jk@ub              Tue Jan 27 16:45   20/930   Output from your job       
 U  3 jk@ub              Tue Jan 27 16:48   18/679   Output from your job       
 U  4 jk@ub              Tue Jan 27 16:55   18/466   Output from your job       
 U  5 jk@ub              Tue Jan 27 17:13   18/466   Output from your job       
 U  6 jk@ub              Wed Jan 28 09:34   18/466   Output from your job       
>N  7 jk@ub              Wed Jan 28 09:37   17/456   Output from your job       
 N  8 jk@ub              Wed Jan 28 10:21   17/456   Output from your job  

As you can see, the command appears to be entered properly as it shows up using -l and I get a message sent (other messages are from previously failed attempts).  But the program doesn't start up.  Why not?

I also attempt the following which is more what I want to do after I figure out how to get the program to open after a minute:
 
at now + 1 minute -f /home/jk/gyachi.sh

When I run this command in terminal it yields the same results as above.  So it seems I'm missing some fundamental understanding about using "at".  Does this have anything to do with the bin/sh warning?  Is my syntax for the command correct? 

Ultimately what I would like to do is have a script which would include the "at" command in it, the "at" command would then start another script in one hour.  So that when the first script is run, a program is opened and after an hour a command is given to close that program.   Is this feasible?  Is there a simple way of doing this?

 Thanks.

---

### Post by pytheas22 on 2009-01-28
I'm not sure why 'at' isn't working for you, but as a workaround, you could use 'sleep' instead.  'sleep' basically just tells the computer to pause for a given amount of time.

For example, if you wanted to run a script in an hour, you could type:
```

sleep 1h; /path/to/script.sh
```

This probably isn't quite as 'clean' a solution as using 'at', but it would work.

---

### Post by sagesparrow on 2009-01-28
If that puts the entire system in sleep mode that won't help.  According to your understanding of "at" what I am entering should open the program?

---

### Post by HermanAB on 2009-01-28
At is a bugger to use.  Batch is the same thing, but with different syntax.  Try 'man batch'.

When using at and cron, remember to always specify the full path name to all binaries in the scripts, since the environment is limited for security reasons.  That is likely what is tripping you up.

Cheers,

Herman

---

### Post by sagesparrow on 2009-01-28
> **HermanAB said:**
> At is a bugger to use.  Batch is the same thing, but with different syntax.  Try 'man batch'.

When using at and cron, remember to always specify the full path name to all binaries in the scripts, since the environment is limited for security reasons.  That is likely what is tripping you up.

Cheers,

Herman


I'll take a swing at batch.  thanks.
with my current problem, using ~/filename or /home/me/filename doesn't make any difference, if that's what you meant.

---

### Post by sagesparrow on 2009-01-28
Batch doesn't seem to use a specified time period for starting a program. According to the man page it executes according to load levels.  Is there some way to specify time with batch?  If not, it looks like "at" is the right tool for this job, but . . . not working.

---

### Post by pytheas22 on 2009-01-28
> If that puts the entire system in sleep mode that won't help. According to your understanding of "at" what I am entering should open the program?

'batch' may be a better solution for you, but to be clear: 'sleep' doesn't put your whole computer to sleep.  It's just a way of telling a particular script (but not the machine as a whole) to pause for a given period of time before running the next command.  It has nothing to do with suspending or hibernating the machine.

---

