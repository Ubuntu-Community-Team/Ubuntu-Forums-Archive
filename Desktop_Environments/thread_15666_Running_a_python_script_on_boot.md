---
title: "Running a python script on boot"
date: 2005-02-15
forum: Desktop Environments
---

### Post by schism on 2005-02-15
Sorry for being such a noob, but we all started somewhere.

All I'm trying to do is have a python script run when the system boots up. The script uses sockets so it has to be sudo'ed. Can somebody tell me or give me a tutorial how to run a command like this at boot?

```
sudo python /my/path/to/script.py
``` 

If it helps, the script I want to run is [edna](http://edna.sourceforge.net/)

---

### Post by evangelion on 2005-02-16
I'm attempting to run things at boot as well, in some other distros there is a /etc/conf.d/local.start file that gets executed at boot, but not Debian/Ubuntu.  Instead what I tried to do was create my own init script containing the commands I wanted to run like so;
```

cd /etc/init.d/
sudo pico -w local **you can really call this anything you want**
the top line of this text file needs to be
#!/bin/sh
so your script would be
------------------------------------
#!/bin/sh                                        
sudo python /path/to/script           

```
save the file then
```

sudo chmod a+x 
```
to make it executable,  and finally
```

sudo apt-get install rcconf
rcconf

```
press spacebar to put a X on "local" or whatever you named it and next time you reboot cross your fingers.
I have yet to reboot with my script but a simple sudo /etc/init.d/local start worked as I expected it to.

There is probably a better method for running commands on boot, but this was all I could think of and it seems to work.

---

