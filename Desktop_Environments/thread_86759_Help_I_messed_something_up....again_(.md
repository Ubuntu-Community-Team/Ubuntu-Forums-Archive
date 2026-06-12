---
title: "Help I messed something up....again :("
date: 2005-11-06
forum: Desktop Environments
---

### Post by Darrin on 2005-11-06
I have two seperate logins for ubuntu. I messed something up in mine. My login icon is gone and when I type in my login password and press enter I get message stating the following:

[B]Your $HOME/.dmrc file has incorrect permissions & is being ignored. This prevents the default session & language from being saved. File should be owned by 
user and have 644 permissions.[/B]

How do I fix this. It all happened after I was messing with [this]("http://ubuntuguide.org/#changefilesfolderspermissions")

---

### Post by Kyral on 2005-11-06
That error is VERY common in our Linux lab, and actually can be ignored for the most part. Heck we have been having it for a couple months and I haven't noticed ANY effect. (The labs are running Gentoo BTW)

---

### Post by Darrin on 2005-11-06
How do I get rid of it. Very annoying. Im unable to change login image as well.

---

### Post by Kyral on 2005-11-06
```
sudo chown <Your Username> .dmrc 
```

This will make you owner (shouldn't need sudo, but its just in case somehow root became owner)

```
chmod 644 .dmrc
```

This SHOULD fix it

---

### Post by Darrin on 2005-11-06
Didnt seem to work. Maybe I did something incorrectly.

I typed in
```
sudo chown darrin .dmrc
```

Then
```
chmod 644 .dmrc
```

Logged out and logged back in and have the same issues.

---

### Post by Darrin on 2005-11-06
Got it working now. The answer for me was found in a [previous post]("http://ubuntuforums.org/showthread.php?t=77627&highlight=.dmrc"). Basically I had to do the following.

```
sudo chown myusername /home/myusername
sudo chgrp myusername /home/myusername
``` 
Now it works fine. :D 
Thanks.

---

