---
title: "Making a script executable everywhere"
date: 2009-03-19
forum: General Help
---

### Post by Prometheus7 on 2009-03-19
I downloaded the eclipse source and followed these instructions to the letter ([http://www.ubuntued.com/?p=40](http://www.ubuntued.com/?p=40)). My problem is that I can only execute eclipse by going to my /bin directory and either saying "./eclipse" or "sh eclipse". When I try to run just "eclipse" the eclipse script is not run. When I echo my path I get the following: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games.

How do I get this script to run from everywhere? Shouldn't I just have to put a link to the script in /bin?

---

### Post by hikaricore on 2009-03-19
Personally I just put a symlink in /usr/bin

> cd /usr/bin
sudo ln -s locationoffile/filename

Make sure you also:

> chmod +x eclipse

If you've not done so already

---

### Post by Tek-E on 2009-03-19
lol. already fixed it before I got my chance lol.

---

### Post by Prometheus7 on 2009-03-19
Thanks for the help, but I've already done that!

In /usr/bin I have my eclipse script which is the following...

```

#!/bin/sh
#export MOZILLA_FIVE_HOME="/usr/lib/mozilla/"
export ECLIPSE_HOME="/opt/eclipse"
$ECLIPSE_HOME/eclipse $*

```

If I cd to /usr/bin and do the following...

/usr/bin$ eclipse          <-- this won't run
/usr/bin$ ./eclipse        <-- this will run correctly

And obviously if I try to run execute from any other directory, it won't work!

---

### Post by Nano_ext3 on 2009-03-19
All you have to do is this:

```

sudo cp MYSCRIPT /usr/local/bin
cd /usr/local/bin
chmod +x MYSCRIPT

```

Now, cd back to rout and do \:

```
user@laptop:/$ MYSCRIPT 
```

Even MY then TAB should autocomplete to confirm.  Make sure if its a drive mount script or anything to run as root.  I use this method to mount my local Server Shares.  :)  I could fstab the entries but me is lazy.

Cheers!

-Nano

---

