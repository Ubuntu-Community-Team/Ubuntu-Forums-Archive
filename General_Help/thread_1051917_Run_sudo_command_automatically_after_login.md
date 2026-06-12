---
title: "Run sudo command automatically after login"
date: 2009-01-27
forum: General Help
---

### Post by Tumbot on 2009-01-27
Hi,
I'm building a headless media server using ubuntu 8.10 and mediatomb.  After the computer auto logs in I want it to run the command:

```
sudo mediatomb
```

I have tried using rc.local and mediatomb runs but the directories I want it to serve don't display. Same problem if I run it without sudo privileges after login.

I don't want to fiddle with the mediatomb settings since it works perfectly at the moment.

The machine is a media server with no connection to the internet, so no worries about security.  If it is possible, I would be happy to have it log on as root.

Thanks in advance.

---

### Post by geirha on 2009-01-27
Open a terminal and run
```
sudo visudo
```

Then add a line like this at the **end** of the file:
```
*username* ALL=NOPASSWD: /full/path/to/mediatomb
```

Of course changing *username* to the actual username of the user that automatically logs in, and you need to specify the full path to mediatomb, not just mediatomb. The following command should show you the full path:
```
which mediatomb
```

After that, that user should be able to run ```
sudo mediatomb
``` without supplying a password.

---

### Post by mb_webguy on 2009-01-27
Why do you want to run Mediatomb as root?  I've seen several tutorials that say to do it, but none say why.  As long as your user account has read access to all of the files you want to share with Mediatomb, I don't see any reason to run it as root.  I'm running Mediatomb right now without root privileges, and I haven't had any problems so far.

---

