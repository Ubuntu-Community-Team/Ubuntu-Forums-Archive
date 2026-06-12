---
title: "Nautilus doesn't autorefresh"
date: 2010-06-19
forum: Desktop Environments
---

### Post by nariknahom on 2010-06-19
Hi,

I am using Ubuntu 10.04 x86_64 and have a problem that the file browser does not refresh automatically. This is what I notice. 
[LIST=1]
[*]open a file browser
[*]create a folder or touch a new file from a terminal window.  
[*]In the already opened file browser, I expect the new file or folder to show up on its own. It doesn't unless refresh button is pressed
[/LIST]

Could someone help?

Thanks,
Kiran

---

### Post by doas777 on 2010-06-19
interesting. mine does autoupdate, though i had expected it wouldn't. 's kinda cool.
there is a bug filed on the Lucid Release canidate about it:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/573160](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/573160)

I did a quick look though gconf editor, and didn't see any pertinent settings. one guy on the bug thought it had somthing to do with having a DVD disk in the drive unmounted. doesn;t make a lot of sense to me, but bugs can be bizarre. 
hth

---

### Post by nariknahom on 2010-06-19
how can I run nautilus in debug mode?
where in gconf editor can i find nautilus configurations?

I think this has something to do with "dropbox" [https://www.dropbox.com]("https://www.dropbox.com").

---

### Post by doas777 on 2010-06-19
well, I don't know about debug mode, but if you launch nautilus from a terminal, all the debugging messages will appear in the terminal. or you can perform the actions that fail, and then immediatly run 
```
dmesg | tail
``` to display the last 10 lines of the dmesg log. 
you can access the other logs via the log file viewer at system-> log file viewer.

as I said I didn't see anything in gconfeditor, by searching for update, refresh, etc. there. usually for nautilus I go to Apps->Nautilus->...

---

