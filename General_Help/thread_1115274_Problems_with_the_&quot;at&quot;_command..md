---
title: "Problems with the &quot;at&quot; command."
date: 2009-04-03
forum: General Help
---

### Post by ShaunG on 2009-04-03
Hey I am hoping that someone here will be able to help me the following.

I am having problems using the "at" command. When I run the command i get the following error message

> Can't open /var/run/atd.pid to signal atd. No atd running? ubuntu

I have no idea what this means and have been searching for sometime but have not come up with any fixes. The closest to a fix I have come across is at the following address but that fix appears to be for Suse.

[http://tinyurl.com/at-fix0]("http://tinyurl.com/at-fix0")

Any help is very much appreciated.

Thanks guys.

~ Shaun

---

### Post by spibou on 2009-04-03
When you run the at command it writes in a file information about what job you want to run and when you want to run it. The at daemon is a programme which periodically checks this file and at the right time starts the job. The daemon itself gets started when the operating system boots and continues to run for as long as the computer is on. Furthermore the file /var/run/atd.pid gets created and contains the process ID of the daemon. (If you don't know what a process ID is don't worry about it.)

It looks as if in your case the daemon was not started for some reason. To make sure do ```
ps -elf | grep atd 
``` and post the output.

---

### Post by ShaunG on 2009-04-03
Spibou, thank you for the speedy reply :)

Here is the output

> graysr@archimedes:~$ ps -elf | grep atd
0 R graysr   13170 13145  0  80   0 -   100 -      22:18 pts/3    00:00:00 grep atd


---

### Post by spibou on 2009-04-03
So the daemon indeed is not running. Do ```
sudo atd
``` After this there should be a /var/run/atd.pid file and you should be able to run at commands. The other question is why was the at daemon not started ? There should be an entry in the system start-up files which starts the daemon at boot time but I'm not very familiar with those so I'll let someone else chip in on this one. But if you want to explore on your own a starting point is the file /etc/init.d/README

By the way , after you start the daemon you might want to do again ```
ps -elf | grep atd
``` just so that you know what the output looks like when the daemon is running.

Oh , and archimedes is a cool name for a computer ;)

---

### Post by ShaunG on 2009-04-03
Thank you , I ran sudo atd, but the output from ls -elf | grep atd remains almost the same:

> graysr@archimedes:~$ sudo atd
graysr@archimedes:~$ ps -elf | grep atd
0 S graysr   14655 14502  0  80   0 -   751 -      22:45 pts/1    00:00:00 grep atd

Also the output after running at also remains the same:
> graysr@archimedes:~$ at now
warning: commands will be executed using /bin/sh
at> echo "Test"            
at> <EOT>
job 15 at Fri Apr  3 22:45:00 2009
Can't open /var/run/atd.pid to signal atd. No atd running?

And yes archimedes is a pretty good name, my other pcs are named after Norse Gods so i decided this one would be different :P

---

### Post by spibou on 2009-04-03
Did you get any error messages after ```
sudo atd
``` ?
Do ```
 ls -l /usr/sbin/atd
``` and post the output.

---

### Post by spibou on 2009-04-03
Since you ask in a different thread whether /var/run might have a problem do also ```
 ls -ld /var/run
``` and post the output.

---

### Post by ShaunG on 2009-04-03
No, no errors after sudo atd.

Output of ls -l /usr/sbin/atd:

> graysr@archimedes:~$ ls -l /usr/sbin/atd
-rwxr-xr-x 1 root root 16040 2007-02-20 13:41 /usr/sbin/atd


Output of ls -ld /var/run

> graysr@archimedes:~$ ls -ld /var/run
drwxr-xr-x 16 root root 680 2009-04-03 23:04 /var/run


---

### Post by spibou on 2009-04-03
Do ```
sudo atd -d
```

---

### Post by ShaunG on 2009-04-03
When i run sudo atd -d i get nothing at all and it just hangs.

---

### Post by spibou on 2009-04-03
You have 2 options. One is to reinstall the at package and repeat the steps we did. This may solve your problem immediately but sometimes installing stuff breaks things worse. The second option is to investigate the problem further as follows:
```
sudo bash
```
This will give you a root shell. Then you do
```
atd -d
```
Wait for a while and if you don't get any error messages start a new shell (under your normal account) and see if atd is running or if you can use the at command.

---

### Post by ShaunG on 2009-04-03
Unfortunately doing the above still leaves it hanging :(

I will try a re-install and see what happens.

EDIT: Trying a re-install is not an option methinks. It means I will also have to remove ubuntu-standard and I would rather not do that.

---

### Post by spibou on 2009-04-03
> **ShaunG said:**
> Unfortunately doing the above still leaves it hanging :(

What is the output of ```
ps -elf | grep atd
```while it's "hanging" ?

---

### Post by ShaunG on 2009-04-03
Output of ps -elf | grep atd

(At this point I would just like to point out how funny it is to type a command where you can ps on an elf. )

> graysr@archimedes:~$ ps -elf | grep atd
4 S daemon   24288 24264  0  80   0 -   496 -      01:12 pts/1    00:00:00 atd -d
0 R graysr   24314 24293  0  80   0 -   752 -      01:13 pts/2    00:00:00 grep atd

---

### Post by spibou on 2009-04-03
Ok so the daemon is running then. Does the file /var/run/atd.pid exist ? Can you create at jobs ?
> **ShaunG said:**
> 
(At this point I would just like to point out how funny it is to type a command where you can ps on an elf. )
I've be using the command for years , strange I've never noticed that before. Although I guess it is a bit of leap to go from ps to p*s*.

---

### Post by ShaunG on 2009-04-03
> **spibou said:**
> Ok so the daemon is running then. Does the file /var/run/atd.pid exist ? Can you create at jobs ?

The file /var/run/atd/pid does not exist.

While the command atd -d is running I can create at jobs, but they are never executed.
Also I am not sure how at jobs work but currently atq shows no jobs,  yet if I run at the new job number will be 20..should it not go back to 0 if there are no jobs?


> I've be using the command for years , strange I've never noticed that before. Although I guess it is a bit of leap to go from ps to p*s*.

I never said anything about p*s* :P:P

---

### Post by spibou on 2009-04-03
> **ShaunG said:**
> The file /var/run/atd/pid does not exist.
It's /var/run/atd.pid , did you check for the correct file ?
> While the command atd -d is running I can create at jobs, but they are never executed.
How do you know they are not executed , what exactly did you try ?
>  Also I am not sure how at jobs work but currently atq shows no jobs,  yet if I run at the new job number will be 20..should it not go back to 0 if there are no jobs?
I'm not sure what job number you're referring to.

---

### Post by ShaunG on 2009-04-03
> **spibou said:**
> It's /var/run/atd.pid , did you check for the correct file ?

Yes sorry, typo. It doesn't exist.

> **spibou said:**
> How do you know they are not executed , what exactly did you try ?
I tried: (note the time used was a future time)

```
graysr@archimedes:~$ at 02:11
warning: commands will be executed using /bin/sh
at> echo "test"
at> <EOT>

```

> **spibou said:**
> I'm not sure what job number you're referring to.
When I run at I'm assuming each task is given a job number. Well when all at commands have run their course should the job numbers go back to 0 or keep incrementing? 

Sorry I'm having difficulty explaining some things, and thank you for your patience in helping me thus far.

---

### Post by spibou on 2009-04-03
You do know that the output of at jobs does not appear on the screen , yes ? Both stdout and stderr get emailed to you assuming you have an email service running. If not then they get lost for eternity. Try the following
```
at now + 1min
touch /tmp/some-file-which-does-not-exist

```
and after 1 minute check whether /tmp/some-file-which-does-not-exist actually exists.

How at numbers jobs is at's business , it is not something which gets exposed to the user. It may not even be just a number , on Solaris 8 you get a longish string.

---

### Post by ShaunG on 2009-04-03
Yes that worked. :) 

But it only works if I keep a terminal open with following command running:

 ```
sudo atd -d
```

Otherwise I still get the following message:

> Can't open /var/run/atd.pid to signal atd. No atd running?

---

### Post by spibou on 2009-04-03
Kill the atd which is running now and from a root shell do
```
atd&
echo PID > /var/run/atd.pid
```
where PID is the process ID of atd. Now you can exit the root shell and things should work. But there is still the question of why wasn't atd started at boot time ?

---

### Post by ShaunG on 2009-04-03
Ok when I run that in a root shell I get:

> root@archimedes:~# atd&
[1] 11157
root@archimedes:~# echo 11157 > /var/run/atd.pid
[1]+  Exit 1                  atd

So I'm pretty sure that that's not right :S because when I run the at command now I am getting:

> graysr@archimedes:~$ at now + 1min
warning: commands will be executed using /bin/sh
at> touch ~/Desktop/testAt.test
at> <EOT>
job 27 at Sat Apr  4 03:10:00 2009
Warning: at daemon not running

---

### Post by spibou on 2009-04-03
Use ps -elf to see if atd is running. Check the file /var/log/messages to see if there are any messages relating to atd.

---

### Post by ShaunG on 2009-04-03
ps -elf | grep atd after running in root shell atd&:

> graysr@archimedes:~$ ps -elf | grep atd
0 R graysr   12284 12205  0  80   0 -   751 -      03:18 pts/2    00:00:00 grep atd


Contents of /var/log/

> graysr@archimedes:/var/log$ ls | sort
acpid
acpid.1.gz
acpid.2.gz
acpid.3.gz
acpid.4.gz
apparmor
apt
aptitude
aptitude.1.gz
aptitude.2.gz
aptitude.3.gz
aptitude.4.gz
auth.log
auth.log.0
auth.log.1.gz
auth.log.2.gz
auth.log.3.gz
boot
bootstrap.log
.
.
. SNIPPED


---

### Post by spibou on 2009-04-03
But I didn't ask for a listing of /var/log , I suggested that you check /var/log/messages  But actually that was wrong , check instead /var/log/syslog and see if there are any messages related to atd.

---

### Post by ShaunG on 2009-04-03
Apologies :(

There are messages related to atd. Each message is pretty much the same as the following:

> Apr  4 03:10:58 archimedes atd[11651]: Error redirecting I/O: Permission denied

---

### Post by spibou on 2009-04-03
Try atd& once more from a root shell and see if there are any atd related messages in /var/log/syslog with a time stamp after your latest effort.

---

### Post by ShaunG on 2009-04-03
The newest log relating to atd is:

> Apr  4 03:52:16 archimedes atd[14762]: Error redirecting I/O: Permission denied

---

### Post by ShaunG on 2009-04-04
Bump, please still have not fixed this problem. 

Any help is really appreciated.

---

### Post by ShaunG on 2009-04-04
Really beginning to do my head in :(

Can anyone else try and help?

---

### Post by ShaunG on 2009-04-06
Solved:

/dev/null and /dev/urandom and /dev/random had incorrect permission. Lord only knows how.

---

### Post by satrapes on 2011-04-11
Can you please elaborate on how to change the permissions and how was that the problem?

---

