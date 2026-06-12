---
title: "How can I make a command at Startup?"
date: 2005-07-31
forum: Desktop Environments
---

### Post by rogeriovinhal on 2005-07-31
I have recently changed from Slackware to Ubuntu and I'm loving it, but there are some little things that I can't figure how to set up.

I have a NForce2 mainboard with an AthlonXP processor, and there is a command line that makes the processor cool while not being fully used. This one right here:

> setpci -v -H1 -s 0:0.0 6F=$(printf %x $((0x$(setpci -H1 -s 0:0.0 6F) | 0x10))) 

But there are two problems with that command line on Ubuntu.

I want to do that command everytime Ubuntu launches, in Slackware I used a file named rc.d that had a lot of commands that would be executed BEFORE login, so it would execute it fine everytime the computer started, but I failed to find a similar file to Ubuntu.

The second problem is that since I don't have a file to do this command before login, the command always ask to be superuser to execute it.

Is there a file that can do this? I just want to execute this command line every startup, don't want to make a whole script and a dozen of symbolic links just to do that.

Also, if anyone knows how to install amsn 0.95b in Ubuntu, i would appreciate.  :)

---

### Post by poofyhairguy on 2005-07-31
Not the place for questions. Moved.

---

### Post by KLineD on 2005-07-31
Make a text file with the following:

```

#!/bin/sh

echo 'Configuring Cooldown Processor Parameter...'
setpci -v -H1 -s 0:0.0 6F=$(printf %x $((0x$(setpci -H1 -s 0:0.0 6F) | 0x10)))

```

Now name the file something like cooldown_command or anything you like and move it to /etc/init.d so you have /etc/init.d/cooldown_command (you have to use sudo to move the file to this directory)
```

sudo mv cooldown_command /etc/init.d

```

Make the file executable and owned by root:
```

sudo chown root:root /etc/init.d/cooldown_command
sudo chmod 744 /etc/init.d/cooldown_command

```

And last, to make it execute at startup cd to /etc/rcS.d and make a symbolic link to the file setting a suitable execution number:
```

cd /etc/rcS.d
sudo ln -s /etc/init.d/cooldown_command S60cooldown

```

I don't know about the S60 number, if someone sees a problem with this post it!

---

### Post by rogeriovinhal on 2005-07-31
That worked. Thanks a lot!  :)

---

