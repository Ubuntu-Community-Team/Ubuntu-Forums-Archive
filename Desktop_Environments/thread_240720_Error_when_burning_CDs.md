---
title: "Error when burning CDs"
date: 2006-08-21
forum: Desktop Environments
---

### Post by chloraldo on 2006-08-21
Hello

I can't burn CDs anymore. I tried K3b which says it can't find the right sort of device. Serpentine just gives an error and stops. CD/DVDcreator also just gives an error. They don't say what the problem is.

I have a thinkpad laptop (t43p) and a removable internal DVD-burner. I have used the slot for a second battery recently but now it's in there and it recognizes the empty CD.

BTW, nothing is burned on the CD, it still recognizes it as empty.

If I open the disks manager, then I see the CDROM there...

I really have no idea what to do...
Any help?

---

### Post by encompass on 2006-08-21
can you open ordinary cd's with the drive.
Secondly, try rebooting with the burner in the computer.
And lastly, try runningthe burner from the console... sometimes it geives better errors then...
and another thing... you could try checking the rights... run k3b as root.
sudo k3b
worth a try.

---

### Post by chloraldo on 2006-08-21
> **encompass said:**
> can you open ordinary cd's with the drive.
Secondly, try rebooting with the burner in the computer.
And lastly, try runningthe burner from the console... sometimes it geives better errors then...
and another thing... you could try checking the rights... run k3b as root.
sudo k3b
worth a try.
Thanks for your reply...

I tried with **sudo k3b** and it works!
Then I tried **k3b** without sudo and I get these messages in the terminal:
```
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Error: "/tmp/ksocket-chloraldo" is owned by uid 0 instead of uid 1000.
Link points to "/tmp/ksocket-chloraldo"
Error: "/tmp/ksocket-chloraldo" is owned by uid 0 instead of uid 1000.
Created link from "/home/chloraldo/.kde/socket-thinkpad" to "/tmp/ksocket-chloraldoXQ85ie"
Error: "/tmp/kde-chloraldo" is owned by uid 0 instead of uid 1000.
Link points to "/tmp/kde-chloraldo"
Error: "/tmp/kde-chloraldo" is owned by uid 0 instead of uid 1000.
Created link from "/home/chloraldo/.kde/tmp-thinkpad" to "/tmp/kde-chloraldo1FFXyO"
kbuildsycoca running...
chloraldo@thinkpad:~$ ICE default IO error handler doing an exit(), pid = 25178, errno = 0
kdeinit: Shutting down running client.
DCOP aborting (delayed) call from 'k3b' to 'klauncher'
kbuildsycoca running...
Launched ok, pid = 25320
```
I don't understand this though...

---

### Post by kpkeerthi on 2006-08-21
[http://ubuntuforums.org/showthread.php?t=217472&highlight=CD+Burning](http://ubuntuforums.org/showthread.php?t=217472&highlight=CD+Burning) might help

---

### Post by encompass on 2006-08-21
> **kpkeerthi said:**
> [http://ubuntuforums.org/showthread.php?t=217472&highlight=CD+Burning](http://ubuntuforums.org/showthread.php?t=217472&highlight=CD+Burning) might help
Did this one work for you dude?
If so thank for asking your question.  Could have been better to search the forums.  He used CD Burning in his search feild.:)

---

