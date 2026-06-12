---
title: "How Do I Run This Command in a Script? [SOLVED]"
date: 2013-03-12
forum: Desktop Environments
---

### Post by jakfish on 2013-03-12
echo 1 > /sys/devices/platform/eeepc/cpufv

To do this in console, I first need to enter "sudo -s"

How can I put "echo 1 > /sys/devices/platform/eeepc/cpufv" in a script?

Thanks,Jake

---

### Post by kuifje09 on 2013-03-12
Scripts cannot be run as root as with a regular executable. Would be an security flaw.
If you realy want to do it, you could use expect and put the passwd needed in the script. Which is also not recommended.
To run a script as root, you could make a wrapper for scripts, and put the scripts in a root-only directory.
Then that wrapper-program can run the script for you. We used such solution for years.

---

### Post by sanderj on 2013-03-12
> **jakfish said:**
> echo 1 > /sys/devices/platform/eeepc/cpufvTo do this in console, I first need to enter "sudo -s"How can I put "echo 1 > /sys/devices/platform/eeepc/cpufv" in a script?Thanks,Jake

I thought this could be done using the SETUID method ([http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)), but it is a long time ago that I used it, and I can't reproduce it now with a test script ...

EDIT:

I tried this:

```
-rwsr-xr-x 1 root root   8 mrt 12 20:01 wiebenik5*

```
but the 'whoami' in it still reports my own name (not root)


EDIT 2:

... doesn't work either:

```
sander@flappie:~/dad$ ll
total 48
drwxrwxr-x    2 sander sander  4096 mrt 12 20:16 ./
drwx--x---+ 168 sander sander 32768 mrt 12 20:15 ../
-rwsr-xr-x    1 root   root      41 mrt 12 20:16 dad-off*
-rwsr-xr-x    1 root   root      41 mrt 12 20:16 dad-on*

sander@flappie:~/dad$ ./dad-off
sysctl: permission denied on key 'net.ipv6.conf.wlan0.accept_dad'

sander@flappie:~/dad$ ./dad-on
sysctl: permission denied on key 'net.ipv6.conf.wlan0.accept_dad'

sander@flappie:~/dad$
```

---

### Post by SeijiSensei on 2013-03-12
> **jakfish said:**
> echo 1 > /sys/devices/platform/eeepc/cpufvTo do this in console, I first need to enter "sudo -s"How can I put "echo 1 > /sys/devices/platform/eeepc/cpufv" in a script?Thanks,Jake

Run the script with sudo.

If you're talking about a script that needs to run with root privileges during boot, put the commands in /etc/rc.local.  If you want the script to run as root on a schedule via cron, use "sudo crontab -e" to edit root's crontab, or put the entry in /etc/crontab.

> Scripts cannot be run as root as with a regular executable. Would be an security flaw.

I guess the dozens of scripts that I have run as root must not have worked.  Oh, wait, yes they did.

---

### Post by jakfish on 2013-03-12
Many thanks for all your responses.

Coming from puppy linux, this root stuff has been difficult.  The fact that I need to ask permission, and not even through sudo, but sudo -s, just to change a cpu frequency is...  If it were a a simple sudo command, I could at least put that in /etc/sudoers

If there were a way to make me superuser in all ways, shapes, and forms, I would appreciate the insight. I am a grownup, and am careful as such.

Thanks again for the help,
Jake

---

### Post by jakfish on 2013-03-12
I apologize for the bunched sentences of my reply.  For some reason, Chromium has chosen this format.  I have posted before, without this difficulty.Sorry again,Jake

---

### Post by schragge on 2013-03-12
> **jakfish said:**
> echo 1 > /sys/devices/platform/eeepc/cpufv To do this in console, I first need to enter "sudo -s"How can I put "echo 1 > /sys/devices/platform/eeepc/cpufv" in a script?Thanks,JakeYou mean a script that will run with regular user privileges and only invoke the elevated permissions for this particular line? 
```
sudo sh -c 'echo 1 >/sys/devices/platform/eeepc/cpufv'
```
If you're doing it manually from the command line (as opposite to from a script), consider also
```
echo 1|sudo tee /sys/devices/platform/eeepc/cpufv
``` as it will give you immediate visual feedback.

---

### Post by kuifje09 on 2013-03-12
double posted(deleted)

---

### Post by kuifje09 on 2013-03-12
Sorry, my mistake.

---

### Post by jakfish on 2013-03-12
Thanks again for such quick help. I'm writing this in Word and will cut-n-paste to try to get rid of the weird bunching.

sudo sh -c 'echo 1 >/sys/devices/platform/eeepc/cpufv'

This won&#8217;t work in a plain bash script. Is there something that I can put in /etc/sudoers that will allow its execution in a plain script in the home directory?

@kuifje09. Thanks for the help&#8212;how would I make an &#8220;echo&#8221; command fit into myscript, e.g.?

I put this in /etc/sudoers:%sudo ALL=NOPASSWD: /bin/echo

but no joy.

Thanks,Jake

---

### Post by jakfish on 2013-03-12
Thanks again for such quick help. I'm writing this in Word and will cut-n-paste to try to get rid of the weird bunching.

sudo sh -c 'echo 1 >/sys/devices/platform/eeepc/cpufv'

This won&#8217;t work in a plain bash script. Is there something that I can put in /etc/sudoers that will allow its execution in a plain script in the home directory?

@kuifje09. Thanks for the help&#8212;how would I make an &#8220;echo&#8221; command fit into myscript, e.g.? I put this in /etc/sudoers:

%sudo ALL=NOPASSWD: /bin/echo

but no joy.

Thanks, Jake

---

### Post by kuifje09 on 2013-03-12
Sorry I had to recover from my mistake...

But,

Create the script MyScript with this contend in your home directory:

#!/bin/bash
echo 1 >/sys/devices/platform/eeepc/cpufv

Script must be executable : chmod 700 /home/USERNAME/MyScript

Then edit the sudoersfile eventually with the visudo, but I prefer just vi /etc/sudoers

Enter the next line in the User privilege specification

USERNAME    ALL=(root)NOPASSWD:/home/USERNAME/MyScript

USERNAME must be you name...

 Then you would be able to run sudo /home/USERNAME/MyScript

---

### Post by schragge on 2013-03-12
It's not the echo command that needs elevated privileges here, it's redirection. As redirection is not a command you cannot put it into /etc/sudoers. Members of the sudo group already have the permission execute *any* command as root, *echo* included. This won't help you here. I don't understand why *sudo sh -c* won't work in a plain bash script. It will. If you don't like that it invokes /bin/sh replace it with bash:
```
sudo bash -c 'echo 1 >/sys/devices/platform/eeepc/cpufv'
```. Or, if you will that sudo automatically invokes the login shell of the current user, be it bash, zsh or something else:
```
sudo -s eval 'echo 1 >/sys/devices/platform/eeepc/cpufv' 
```

---

### Post by jakfish on 2013-03-12
You folks are great, many thanks.

@ schragge: sudo sh -c 'echo 1 >/sys/devices/platform/eeepc/cpufv'  I put that in, just the way you suggested, and it didn't change the frequency.  I'll recheck, tho the command did work in console, after I was prompted for root.  I was under the impression that any command that needed sudo, and needed to be executed in plain script, that command needed to be in sudoers.

@ kuifje09: many thanks for the detailed myscript instructions.  Have shut down the eee (it's late here) and am posting on another machine to try and prevent bunching.  But will try all help again tomorrow.

Thanks again,
Jake

---

### Post by schragge on 2013-03-12
Well, if you want to do it *without being prompted for password* then do like **kuifje09** suggested.

---

### Post by kuifje09 on 2013-03-12
My pleasure, altough I sometimes make a mistake.
I was unaware scripts could be run via sudo.

My suggestion to make it a bit more secure, place the script i.e in   /root/scripts/YourScript
The /root/script directory has to be created.

Then change the sudoers entry for the script into   ....  /root/scripts/YourScript

You then can change it when you like, but cannot be altered too easily.

---

### Post by SeijiSensei on 2013-03-13
Might I humbly suggest you read my posting again?

If you want to have this command run every time the computer boots, just put it in /etc/rc.local.  It will run with root privileges after all other startup scripts are run at boot.

---

### Post by jakfish on 2013-03-13
@SeijiSensei--thanks for weighing in again.  I can't put the script in /etc/rc.local because I need two scripts that will toggle back and forth between the two cpu speeds.  So I imagine if I put both scripts in nrc.local, they would fight.

@schragge and kuifje09: Despite the fine suggestions/advice, I never did get any joy with trying to override a sudo &#8211;s command in a plain bash script.  These are the various attempts in /etc/sudoer, and obviously, I experimented within them, playing with the &#8220;%&#8221; and admin vs. jake and switching the called directories.
 
jake ALL=NOPASSWD: /home/jake/Documents/Performance
jake ALL=NOPASSWD: /home/jake/Documents/PowerSave
%admin ALL=NOPASSWD: /root/scripts/Performance
%admin ALL=NOPASSWD: /root/scripts/PowerSave
 
The closest I ever got was a successful execution when sudo-ing in PCManFM, going all the way to /root/scripts and working with the two cpu files there.  A big hassle.  I could never successfully keystroke the scripts in openbox&#8217;s rc.xml (this was the whole point).  In /home/jake/Documents/, I got no response; in /root/scripts/, a keystroke produced a &#8220;permission denied&#8221; error.
 
[These are the commands that have worked in /etc/sudoer, so I&#8217;m hoping my syntax was okay:
 
%sudo ALL=NOPASSWD: /usr/bin/cpufreq-set
%sudo ALL=NOPASSWD: /usr/sbin/pm-suspend
%sudo ALL=NOPASSWD: /sbin/poweroff ]
 
Finally, I found and used this sudoer command:
 
jake ALL = NOPASSWD: ALL
 
All is well now.  The scripts work in the home directory via keystroke and I no longer have to beg the OS for permission to use other commands in other scripts.
 
The underlying problem may have been that a cpu change required &#8220;sudo -s&#8221; and perhaps that wasn&#8217;t ever going to play nice in /etc/sudoers.  Such determinations are above my pay grade, but nothing ever worked, despite all your fast, kind help.
 
At any rate, should I mark this solved?  Or is my solution a little heavy-handed to recommend?
 
Many thanks again,
Jake

---

### Post by schragge on 2013-03-13
Glad you've solved it, but I'm still curious as to what are the file permissions of your scripts?
```
ls -l /root/scripts
```

---

### Post by kuifje09 on 2013-03-13
Ah, they are read and run by root and only by root.

So keep the directory closed but for root. Also for the dirs below.

drwx------ 28 root root 4096 2013-03-13 12:09 /root
drwx------ 2 root root 4096 2013-03-12 22:52 /root/scripts
-rwx------ 1 root root 27 2013-03-12 22:52 /root/scripts/YourScript

And you run the script as :   sudo /root/scripts/YourScript

Oh the question about running at boot, from rc.local,   then you don't this at all.
Just put the lines in /etc/rc.local.   But that wasn't the question in the first place.

---

### Post by kuifje09 on 2013-03-13
Hellojakfish  , in respons to you post #5,   When you are in the admin group ( /etc/group) , what will be done when you gave yourself or another admin permission in the "users and groups" gui,  then "he" could become root all the time with sudo su -.
But make shure you know the root passwd , for in case of....  Even for maintanance mode you need it. Maby also for  just a root shell  from the boot menu. ( i did not check it ).
(I must admit, it is more secure when you always need a cd to become root when you lost or don't know the root paswd.)

---

### Post by jakfish on 2013-03-13
jake@semplice:~$ ls -l /root/scriptsls: cannot access /root/scripts: Permission denied
[EMAIL="jake@semplice:~$"]jake@semplice:~$[/EMAIL] sudo ls -l /root/scriptstotal 8-rwx------ 1 jake jake 65 Mar 13 07:54 Performance-rwx------ 1 jake jake 64 Mar 13 07:54 PowerSave

While beyond my ken, the responses to this thread have been wonderful. I've learned a huge amount about security, thank you.

Stepping back, philosophically, I'm really opposed to the hoops Deb/Ub/others make users jump through. I feel that when you log-in as root, you are root. Obviously, the majority of users feel differently, but I'm a single user and Linux is hard enough--when you deal with scripts, etc--without being asked for permission in a million different ways.

On the other hand, you can get great help at this forum :)Jake

---

