---
title: "home directory turned into a file"
date: 2006-08-28
forum: Desktop Environments
---

### Post by chiefofthejojos on 2006-08-28
Hi all,
GNOME was acting strange and had slowed to a crawl so I rebooted my system.  But then gdm couldn't load correctly and I couldn't even login to the command-line (the error was invalid password).  My first thought was "did I just get hacked?", but then I booted the Knot1 live cd and an "ls -la" on the root directory of the offending installation showed me something interesting:

```
?---------   1 root  513 2424481272 1964-11-10 07:06 home
```

My home directory turned into a file that has lost all it's attributes.  Does anyone have any idea how to fix this?  I'm just extremely glad I had all my important data backed up, but a little frustrated that this happened.  It seems to me to be just a random filesystem glitch but who knows?  I'm going to try and do an fsck to see if it can do anything.  otherwise I guess I'll reinstall.

---

### Post by aysiu on 2006-08-28
When you look at /home in the GUI (Nautilus, Konqueror, whatever file browser you prefer), what happens when you click on it?

---

### Post by chiefofthejojos on 2006-08-28
> **aysiu said:**
> When you look at /home in the GUI (Nautilus, Konqueror, whatever file browser you prefer), what happens when you click on it?

nautilus tells me "Couldn't display /media/dapper/home" (/media/dapper is the mount point)

I have attached a screenshot.
How on earth did you reply so fast?

---

### Post by aysiu on 2006-08-28
It says home is 2.3 GB, though--that's too big to be a file. It's got to be your folder... how do we change it back to a folder...? You tried ```
ls -al
``` What happens when you try to *cd* into it? ```
cd home
``` What error do you get?

---

### Post by chiefofthejojos on 2006-08-28
```
ubuntu@ubuntu:/media/dapper$ cd home
bash: cd: home: Not a directory

```

fsck is finding a LOT of errors, so I'm fixing them.  Maybe that will fix it.  I don't know, though, a similar thing has happened to me before so maybe I have a bad hard drive... it is pretty old.

---

### Post by chiefofthejojos on 2006-08-28
hmmm... after running "fsck -cvy /dev/hda1", the home file/directory is now completely gone.  oh well.

---

### Post by asplode on 2006-08-28
You might consider checking in the lost+found directory, thats where fsck dumps files that it deems corrupted...

---

### Post by cptnapalm on 2006-08-28
Damn, wish I was here earlier...

What filesystem are you running with?

What I did in a somewhat similar situation was to make a new directory and then move everything into it.  I think some subfolders' contents had to be moved manually too.  But everything came out of it okay.

I once sung the praises of XFS... now, I'm having serious reservations about it...  Which sucks because it is damn fast.

---

