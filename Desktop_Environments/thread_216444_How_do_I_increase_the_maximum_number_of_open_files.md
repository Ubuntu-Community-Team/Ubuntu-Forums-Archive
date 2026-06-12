---
title: "How do I increase the maximum number of open files?"
date: 2006-07-15
forum: Desktop Environments
---

### Post by kentl on 2006-07-15
When I download files using KTorrent I get the above type of errors. The error message is "Error: Cannot open index file /*/*/index : To many open files".


I have understood that this is what it says and that a user has a limit of 1024 concurrent files open at any one time. How do I increase this number? And how much do you think that I should increase it? (I have a powerful computer.)

---

### Post by DavidFL on 2006-07-15
> **kentl said:**
> When I download files using KTorrent I get the above type of errors. The error message is "Error: Cannot open index file /*/*/index : To many open files".

[CENTER][CLICK FOR A SCREENSHOT OF THE PROBLEM]("http://thisistheurl.com/file/ktorrent.png")[/CENTER]

I have understood that this is what it says and that a user has a limit of 1024 concurrent files open at any one time. How do I increase this number? And how much do you think that I should increase it? (I have a powerful computer.)

Hello, I have never changed the limit myself so am limited in this knowledge but since no one else replied yet, I found this that presents some proposed solutions:

[http://sourceforge.net/tracker/index.php?func=detail&aid=811406&group_id=84122&atid=575154](http://sourceforge.net/tracker/index.php?func=detail&aid=811406&group_id=84122&atid=575154)

[http://www.ubuntuforums.org/showthread.php?t=214353](http://www.ubuntuforums.org/showthread.php?t=214353)

---

### Post by stoeptegel on 2006-07-16
This is a known (reported) problem, from coming version 2.0 KTorrent will deal with it by closing files on the fly plus a new feature: global connection limit.
For now you could try setting the connection limit per torrent lower and/or running less torrents at the same time. You could also set the standard ulimit of the system(1024) higher, but i don't know if this is recommended.

---

### Post by kentl on 2006-07-16
Thanks for all of your replies. Does anyone know why I wouldn't want to increase the maximum number to lets say 2048 instead of 1024?

---

### Post by kentl on 2006-07-18
Does anyone know how to increase the maximum number of concurrent open files? (I get no replies.)

---

### Post by stoeptegel on 2006-07-18
> **kentl said:**
> Does anyone know how to increase the maximum number of concurrent open files? (I get no replies.)

This is not covered by sudo, you have to be root and probably have to make the root account first:

*After some testing it seems this limit get reset after an exit, which makes my stuff in the code tags not correct*
In bash
```

sudo passwd root
Password: <specify user password>

```

Then login as root with
```

ctrl+alt+f2
root
Password: <specify user password>

```

And change the ulimit -n
```

ulimit -n 1200

```

After this is done, i would lock the root account (sudo -s -H would still be possible)
```

exit
ctrl+alt+F7
sudo passwd -l root

```


Personally i think such open file limit is there for a reason, and my mind says it's wise to be gentle with upgrading this number.

PS.There's a new KTorrent 2.0 ReleaseCandidate package released today on ktorrent.org which you might want to try out, it has lots of new features and comes with many polishments after the previous beta.

EDIT
I noticed for some reason above setting gets reset after an exit, i am lost here. If anyone has a good way doing this, please bump it.

---

### Post by stoeptegel on 2006-07-20
Ok, just forget above ulimit command.

Edit the file /etc/security/limits.conf
with sudo and add the following two line just before #end:

kentl    hard nofile  1300
kentl    soft nofile  1200

You might have to reboot to activate this setting.
The weird part is that this should allow the user kentl to increase the ulimit to the hard limit, but ulimit is not there for users.(?)
Anyway, this works.

EDIT
And again, nothing weird here, i was totally wrong :-# 
The user can just use ulimit without sudo after editing above limits.conf file.

I should stop thinking with this tropic weather here in the Netherlands... getting braindead somehow.

---

