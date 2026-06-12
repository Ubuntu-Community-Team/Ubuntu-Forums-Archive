---
title: "What is the best way to automate this?"
date: 2010-02-15
forum: Desktop Environments
---

### Post by Maconvert on 2010-02-15
Hello Everyone,

I've just installed Twonky on my Ubuntu file server PC and it's working great.
However, each time I restart the computer I have to go to the terminal and type in a bunch of commands to start Twonky.

Here's the command sequence:


[INDENT]username@ComputerName:~$ sudo -s

<  ENTER ROOT PASSWORD AT PROMPT   >

root@ComputerName:~# cd /usr/local/twonkymedia

root@ComputerName:/usr/local/twonkymedia# chmod 700 twonkym*

root@ComputerName:/usr/local/twonkymedia# route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0

root@ComputerName:/usr/local/twonkymedia# /usr/local/twonkymedia/twonkymedia[/INDENT]



What I really need is to have my PC do all of this automatically at startup.

Although I have some idea of how to accomplish this, I'd like to hear everyone's opinion on the best way to go about it.

Please let me know.

Cheers.

---

### Post by Maconvert on 2010-02-15
Don't everybody reply at once!!!
LOL
Just kidding.
Whenever you're ready.

;)

---

### Post by warp99 on 2010-02-15
Just place the commands inside of your rc.local file like this:

```
sudo gedit /etc/rc.local
```

Then add the following between "this script does nothing" and "exit 0"
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[b]chmod 700 /usr/local/twonkymedia/twonkym*

route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0

/usr/local/twonkymedia/twonkymedia[/b]

exit 0
```

This assumes that network services have already started, which they should unless you start them some time later in the boot cycle.

---

### Post by Maconvert on 2010-02-18
Thanks. That worked perfectly!

Cheers!

---

