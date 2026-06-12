---
title: "Tracker error: Index corrupted"
date: 2009-05-08
forum: Desktop Environments
---

### Post by fa2k on 2009-05-08
I get an error message in a small window:
```
        Tracker Applet
Tracker
There was an error while performing indexing:

Index corrupted
[ Reindex all contents ] [ Cancel ] [ OK ]
```
When I click OK or cancel, the error window closes, then reappears immediately. 
When I click "Reindex all contents", I get a message that the indexing may take a long time, then it starts indexing. The error message reappears at once. If I then click OK, the error window closes.

The error reappears on reboot, and randomly other times. 

Another, probably related, issue is that processes are running at 100% all the time. I first assumed that this was the indexer, but now the processes have used a combined 1466 minutes (more than 24 hours) of CPU time. While this is only a 1.8GHz laptop, this seems excessive for anything other than an infinite loop.
The processes are ```
tracker-indexer
python
dbus-daemon
trackerd
tracker-applet
```
All these processes have CPU usage of the same order (which is strange, normally only one process would be like this).

When I click "reindex all contets", the processes are killed, but they appear later. There is virtually no CPU or disk activity after I click [ Reindex all contents ].

I'm sorry if this post is confusing, but this error is really confusing to me. I suppose it could be a file that gives the indexer trouble, but I don't know how I would check that.

---

### Post by Isfrid on 2009-05-08
I have the same problem. Can somebody help us please.. ?

---

### Post by greerd on 2009-05-08
Check the 'owner' & 'group' for your .dbus directory and all files within it. The .dbus directory in your home directory. If they have been switched to 'root' change them back to your user name. This helped me with a number of issues including tracker and panel issues.

Regards,
Doug

---

### Post by fa2k on 2009-05-08
> **greerd said:**
> Check the 'owner' & 'group' for your .dbus directory and all files within it. The .dbus directory in your home directory. If they have been switched to 'root' change them back to your user name. This helped me with a number of issues including tracker and panel issues.

Regards,
Doug

Thanks, but my .dbus was owned by me. I tried to remove any files owned by root (in my /home), but no luck.

---

### Post by sarutv on 2009-05-08
As per suggestion in [bug#361560]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560"), I did:
```
sudo apt-get install tracker-utils
tracker-processes -r # --hard-reset

```

Terminal output looks something like:
```
saru@amma:~$ tracker-processes -r
Found 160 pids...
Found process ID 3878 for 'tracker-applet'
  Killed process 3878
Found process ID 3956 for 'tracker-indexer'
  Killed process 3956
Found process ID 4890 for 'trackerd'
  Killed process 4890
Setting database locations
Checking database directories exist
Checking database version
Checking database files exist
Removing all database files
  Removing database:'/home/saru/.local/share/tracker/data/common.db'
  Removing database:'/tmp/tracker-saru/cache.db'
  Removing database:'/home/saru/.cache/tracker/file-meta.db'
  Removing database:'/home/saru/.cache/tracker/file-fulltext.db'
  Removing database:'/home/saru/.cache/tracker/file-contents.db'
  Removing database:'/home/saru/.cache/tracker/email-meta.db'
  Removing database:'/home/saru/.cache/tracker/email-fulltext.db'
  Removing database:'/home/saru/.cache/tracker/email-contents.db'
Setting index database locations
Checking index directories exist
Checking index files exist
Removing all database index files
  Removing database index:'/home/saru/.cache/tracker/file-index.db'
  Removing database index:'/home/saru/.cache/tracker/email-index.db'

```

The above kills the tracker processes and cleans up the tracker related directories. If you restart and login, tracker should reindex without problems. 

I couldn't be bothered to restart so I ran:
```
tracker-applet&
/usr/lib/tracker/trackerd&
```

---

### Post by bluebook on 2009-05-09
This is exactly the issue I'd been having. The info above worked for me for about 2 minutes. After restarting the tracker the CPU went down to 50% or so for both processors then 1-2 mins later it climbed back up to 100% for each processor and it has stayed there since. I haven't gotten the "index corrupted" message quite yet (just did this) but I bet I will soon...

---

### Post by fa2k on 2009-05-10
> **sarutv said:**
> As per suggestion in [bug#361560]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560"), I did:
```
sudo apt-get install tracker-utils
tracker-processes -r # --hard-reset

```


Thank you, this fixed the problem for me. Great!

---

### Post by Nullexe on 2009-05-17
Awesome thanks for this!

---

### Post by RodneyRodgers on 2009-05-19
Hey,  Just joined the forums to say thanks for this fix!

---

### Post by jheaton5 on 2009-05-20
Thanks for this tip.

---

### Post by thilinaVithanage on 2009-05-27
thanks for the help guys .. had the same eissue ..

---

### Post by karagiozakos on 2009-05-27
same problem here, thanks sarutv for the solution.

---

### Post by ledzepjes on 2009-06-11
I found this solution to work for me, in cmd line I typed:

sudo apt-get purge tracker && sudo apt-get install tracker

this code is from this thread:

[http://ubuntuforums.org/showthread.php?t=1144718](http://ubuntuforums.org/showthread.php?t=1144718)

after I typed this in the terminal I was able to close the error box and it stopped popping up again after that

---

