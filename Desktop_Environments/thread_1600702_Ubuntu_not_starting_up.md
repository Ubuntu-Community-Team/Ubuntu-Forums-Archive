---
title: "Ubuntu not starting up"
date: 2010-10-19
forum: Desktop Environments
---

### Post by sojiabolarin on 2010-10-19
Hi guys,
Im a freshman ubuntu user and i have been enjoying it till this morning. I installed filezilla ftp client software this morning and it worked. I later restarted my laptop and the boot process was normal until it was to show the log in screen. At that point, the screen remained blank. its been 3 hours and 10 restarts later and im still here...:( :(

---

### Post by chessnerd on 2010-10-19
Well, you could just hold down the power button until the system turns off and then start it up again, but I'm guessing you tried that.

Can you get access to a virtual terminal with Ctrl-Alt-F2? If so, you'll know that the issue is with the login and not a bigger problem. Login there and then you can use the command line to work on fixing the problem.

First, update your software to the latest version with: ```
sudo apt-get update && sudo apt-get upgrade
```
Then, I would recommend trying to reinstall the login manager with: ```
sudo apt-get --reinstall install gdm
```

If that doesn't work, then you should try a different login manager. An example would be slim or xdm. ```
sudo apt-get remove gdm && sudo apt-get install slim
``` 

If that doesn't work, then we have a bigger problem.

---

