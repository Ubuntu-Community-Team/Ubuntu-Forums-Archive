---
title: "VNC on startup/boot"
date: 2009-06-02
forum: General Help
---

### Post by warnox on 2009-06-02
Hey!

So I want to add a script to startup to start up 'vncserver'.

I did the following.

1. Created the script in /etc/init.d/:

```
#!/bin/bash
echo "before" >> /home/gregor/Documents/logfile
#vncserver
#/bin/su - gregor -c "/usr/local/bin/vncserver :2"
/bin/su - root -c "/usr/local/bin/vncserver :2"
echo "before" >> /home/gregor/Documents/logfile
```

Tried all of the commented out lines above and neither one works.

2.

```

sudo chmod +x vncstartup
```

3.

```
sudo update-rc.d vncstartup defaults
```

---

When I restart the machine the log file ends up with:

> before
after
before
after

but it's as if the 'vncserver' command is not even run!?

If I run the script manually it also executes two times :S

Anyone have any idea why the script doesn't start up vncserver on startup? and why the script is run twice?

Thanks,




Gregor

---

### Post by dcstar on 2009-06-02
> **warnox said:**
> Hey!

So I want to add a script to startup to start up 'vncserver'.
..........
Anyone have any idea why the script doesn't start up vncserver on startup? and why the script is run twice?

Thanks

Gregor

There are already numerous HOWTOs on setting up vncserver in these forums (as well as elsewhere), please search them out.

---

