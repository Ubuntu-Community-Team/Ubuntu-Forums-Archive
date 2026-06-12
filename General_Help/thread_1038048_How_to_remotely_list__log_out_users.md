---
title: "How to remotely list / log out users?"
date: 2009-01-12
forum: General Help
---

### Post by Quaxo76 on 2009-01-12
Hello,
I have setup a file server in my home network. It's based on Ubuntu 7.04. I made some heavy customizations on it to reduce power consumption (because it's running 24/7) and to allow access to different partitions to different users. I also setup a few scripts that execute some periodic tasks, and then email me with the results.
As a failsafe feature, one of the scripts unmounts the data HDs and essentially puts the server to sleep in case any of the commands of the script return an error. This is to prevent data loss or further damage in case of troubles.
Now, here's my problem: this script is setup to be executed at 4am, when likely no one is connected.
But sometimes, rarely, someone is up and working at that time; if that's the case, fsck (one of the commands in the script) fails on the data drive because it's in use and the partition can't be unmounted.
So, what I would like to do, is to add a test that checks if there are other users logged on the server; and if there are, let them finish the file operation they're eventually doing, and then brutally "kick them out" before continuing with the rest of the script.
Basically, I would need a command that lists which users are remotely logged on, and a command that can wait for an user to be idle and then logs him out.
How can I do that? Are there such commands in Linux?

TIA
Cristian

---

### Post by heindsight on 2009-01-12
you can use ```
who -u
``` to get a list of all logged in users, their idle time and their session pids. so you could check the output of who, and log of idle users by killing their session. but, keep in mind that even if a user is listed as idle, they may still have open files with unsaved data. 

It may be a good idea to broadcast a message to all users (perhaps using wall) to warn them to save all their data, then perhaps wait a few seconds or minutes, before kicking everyone off.

---

### Post by Insightfill on 2009-01-12
A couple of pages that came up in searches...

This one: [http://webtools.live2support.com/linux/users.php](http://webtools.live2support.com/linux/users.php) simply lists the users online.

This one: [http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html](http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html) has some good commands for listing CPU usage by user, etc.

However: it's hard to tell when a user has 'logged off', depending on the usage of the system.  If you're running a LTSP, for example, the users may have simply disconnected and have left a running desktop.  However, if you're running a simply FTP/HTTP/SFTP server, it's more reliable.

---

### Post by Quaxo76 on 2009-01-12
Thanks for the replies. I'll make some experiments. Warning users of imminent logout is pointless here, because mostly the computers will be running unattended.
Let's say that I care more about not corrupting the server's file system than not loosing user data (users usually only store finished work on the server, so they always have local copies): how would the command "umount -l" work? That should be safe (i.e. not corrupt the filesystem), right?

---

### Post by scorp123 on 2009-01-12
> **Quaxo76 said:**
> How can I do that? Are there such commands in Linux Who's logged in: ```
 w
```

What sessions are still running and since when:
```
last
```

Examples:
 ```
> w
 20:48:14 up  3:07,  2 users,  load average: 0.07, 0.04, 0.04
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
sysadm      tty7     :0               17:41    2:07   3:52m  0.12s x-session-manager
sysadm      pts/0    :0.0             20:46    0.00s  0.12s  0.00s w
```

Use "grep" to filter users who are still active:
```
> last | grep still
sysadm      pts/0        :0.0             Mon Jan 12 20:46   still logged in   
sysadm      tty7         :0               Mon Jan 12 17:41   still logged in
```

Find all processes owned by a specific user and terminate them; thus extremely extremely likely killing the login session of this user:
```
sudo pkill -U nameOfUserHere
```

It should be easy to combine these commands, e.g. via *if..then..else* loops. Or even easier: warn all users to logoff (e.g. via "**wall**" command), wait 30 minutes ("sleep" command), and then mercilessly kill all user sessions (e.g. via *pkill -G nameOfUserGroupHere* ... e.g. **sudo pkill -G users** ... that would kill all sessions of anyone belonging to the "users" group ... [COLOR="Red"]use with caution! Depending on the groups you yourself belong to a command like this one might easily kill your session too![/COLOR])

I hope these commands were useful to you.

---

### Post by Quaxo76 on 2009-01-14
A further question... I'm experimenting and I noticed that the 'last' command only lists users who actually logged onto the server machine. But most users here just access their shares on the server, using their login username and passwords. Is there a way to see those users too? 'last' doesn't report them...

---

### Post by heindsight on 2009-01-15
If they're accessing these shares through Samba, then you could look at running smbd processes. Samba creates an smbd process for each user accessing the server. So if you use a combination of ps and grep (or pgrep) you could get a list of all smbd processes not owned by root, and the owners of those processes will be the users who are currently accessing your samba server.

---

### Post by Quaxo76 on 2009-01-28
I made some tries but I'm not sure I know what's actually going on... After reading the man page for ps, I tried logging in as 3 different users to the server, via samba. All three users can browse the server, so they're actually logged. But if in a terminal I type ```
sudo ps -eF | grep smbd
``` what I get is this: ```
cristian  7323 17763  0  3721  4056   0 23:10 ?        00:00:00 /usr/sbin/smbd -D
cristian  7389  7243  0   751   760   0 23:17 pts/0    00:00:00 grep smbd
root     17763     1  0  2795  2760   0  2008 ?        00:00:00 /usr/sbin/smbd -D
root     17766 17763  0  2795  1032   0  2008 ?        00:00:00 /usr/sbin/smbd -D

```
Several things aren't clear to me: OK, the two root processes are the "server side" of Samba. One of the two lines with user "cristian" is the process of the above command; but why isn't it owned by root (I sudoed it)?
Second: Where are the other two users? They are logged in, they should have a process... or not? Or is only the first logged user creating a process, and the others use that?

---

### Post by heindsight on 2009-01-29
> **Quaxo76 said:**
> I made some tries but I'm not sure I know what's actually going on... After reading the man page for ps, I tried logging in as 3 different users to the server, via samba. All three users can browse the server, so they're actually logged. But if in a terminal I type ```
sudo ps -eF | grep smbd
``` what I get is this: ```
cristian  7323 17763  0  3721  4056   0 23:10 ?        00:00:00 /usr/sbin/smbd -D
cristian  7389  7243  0   751   760   0 23:17 pts/0    00:00:00 grep smbd
root     17763     1  0  2795  2760   0  2008 ?        00:00:00 /usr/sbin/smbd -D
root     17766 17763  0  2795  1032   0  2008 ?        00:00:00 /usr/sbin/smbd -D

```
Several things aren't clear to me: OK, the two root processes are the "server side" of Samba. One of the two lines with user "cristian" is the process of the above command; but why isn't it owned by root (I sudoed it)?
Second: Where are the other two users? They are logged in, they should have a process... or not? Or is only the first logged user creating a process, and the others use that?

I'm no samba expert, but I'm quite sure that there should be an smbd process for each active connection (and it has to be owned by the username the client is connecting as in order to have correct permissions).

I would guess that your other two users did not really have 'active' connections at the time you ran ps. Perhaps the client does something like connect to retrieve a directory listing and then disconnecting again immediately. One way you could perhaps get a better idea of what's going on is to use ```
watch "ps -eF | grep smbd"
``` If you start this command before establishing any connections as other users and keep an eye on the output it should give you a better indication of what smbd processes are created as a user connects to the server.

As for your grep command in the ps output, when you run:
```
sudo ps -eF | grep smbd
``` then ps is run as root, but grep is run as your normal user. You shouldn't need to use sudo for running ps though, it should work just fine running it as a normal user.

---

### Post by Quaxo76 on 2009-01-29
Well, it seems to be a bit weird: say there are 3 users A,B and C. If A logs on the server, I can see the smbd process belonging to A. And that doesn't go away. If then B logs in... then I can only see the process belonging to B.Same happens when C logs in.
But then, if C logs out, I can again see the process belonging to B. And when B logs out, there appears the process belonging to A. I'm not at home now so I can't check the "watch" command, I will as soon as I get back home!

Cristian

Edit: Might it be that it's because I log in, as the 3 different users, from the same physical machine?

---

