---
title: "I typed some command that made it so my system is inaccessible"
date: 2009-05-01
forum: General Help
---

### Post by szenith on 2009-05-01
Okay so I had this problem when I was logging on after installing and uninstalling a bunch of packages, it gave me a message that said 

"User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writeable by other users." 

so I looked up how to fix that and I went here

[http://ubuntuforums.org/archive/index.php/t-491591.html](http://ubuntuforums.org/archive/index.php/t-491591.html)

which led me to here

[https://answers.launchpad.net/ubuntu/+question/7296](https://answers.launchpad.net/ubuntu/+question/7296)

and so I did the commands in the post that said:

"No, enter

chmod 644 .dmrc
chmod 700 ~

~ represents the home folder."


so I typed "chmod 644 .dmrc" and "sudo chmod 700 /home" in the terminal, so I did that and logged out, but logging back in it gave me a message saying

"Your home directory is listed as: '/home/ivan' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session." 

and after I type in my password it gives me the "User's $Home/.dmrc file is being ignored." message as again, and after that it is just blank and won't load anything. no desktop, no programs, nothing. So I'm really unsure of what I did, and how to fix it. Is there a way to type some command through some restore mode to fix this? I'm using Jaunty 9.04 and it has a GRUB boot screen. I'm on another machine trying to figure out what to do with this. Well, any input, even just as to what is going on would be appreciated, thank you.

---

### Post by _Purple_ on 2009-05-01
~ represents **your** home directory. In your case which is /home/ivan, it is not /home.

---

### Post by geirha on 2009-05-01
Yes, only root has access to /home now, but it should be readable and executable to all users. Boot into recovery mode to get a root shell, then do
```
chmod 755 /home
```

---

### Post by sisco311 on 2009-05-01
restore the permissions of the /home dir:
```
sudo chmod 0755 /home
```
then:
[thread]976610[/thread]

---

### Post by szenith on 2009-05-01
Aweeesome, okay that command and the commands in the other thread fixed everything. Thank you:KS:):)!! :)

---

