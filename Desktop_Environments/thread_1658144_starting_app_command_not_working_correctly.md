---
title: "starting app command not working correctly?"
date: 2011-01-02
forum: Desktop Environments
---

### Post by Shocker on 2011-01-02
Happy new year everybody!

One quick question. Can anyone tell me why this command:

/usr/bin/freepopsd -vv > /home/shocker/Desktop/Freepopsd.log

doesn't write the log in the Desktop folder?

It's written exactly like that in the Ubuntu startup program control panel and according to the ps command I understand it's correctly running:

$ ps aux | grep freepopsd
shocker   1676  0.0  0.1 227264  9128 ?        S    13:22   0:00 /usr/bin/freepopsd -vv > /home/shocker/Desktop/Freepopsd.log

What am I missing?
Thanks in advance for any suggestion!

Shocker

---

### Post by theozzlives on 2011-01-02
Try writing a script, make it executable and put it in your /etc/init.d folder.

```
#!/bin/bash
/usr/bin/freepopsd -vv > /home/shocker/Desktop/Freepopsd.log
```

---

### Post by Shocker on 2011-01-02
Hello, I tried your advice unfortunately with no results. This is what I made:

I copied your script into a new text file,
Saved it as freepopsd and made it executable through the props window.
I moved this file to the /etc/init.d and, after removing the service startup call from the startup programs, I restarted the PC.
Unfortunately after logging in I noticed that the program didn't even start up this time.
Trying to call it by the shell (/etc/init.d/freepopsd) made the program run again but it didn't start writing the log in my Desktop either...

There must be something strange in the command line...

Thanks for any further help!

Shocker

---

