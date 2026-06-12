---
title: "Tomboy Laptop Synchronization"
date: 2007-11-27
forum: Desktop Environments
---

### Post by rolodoom on 2007-11-27
How can I synchronize tomboy notes from my laptop to my desktop PC?? I read that is possible synchronize them to a server but don't know how. Any suggestions??

Thanks

---

### Post by atlas95 on 2007-11-28
+1, conduit can do it with methode for sync with backpackit website . But tomboy have native function to do it,but it requires a unknown server for me, i'm searching for this server, free...could you help me please?
sorry for my english
Best Regards

---

### Post by R Smit on 2007-12-30
Copy the *.note files from /home/xx/ .tomboy to the same directory of your other computer?

---

### Post by Krydahl on 2008-02-09
Just tried this on Gutsy and it seemed to work well.

If you have a drive both computers can access, simply create a folder in there - syncTomboy or something. Next, open tomboy on one machine, go to preferences -> Synchronization and browse to your new folder. Save. Go to tools -> synchronize and run the tool.

Repeat with your second computer. Seemed to work great. You don't need a remote server.

I'd like to be able to schedule the synchronization to run automatically somehow, but I haven't discovered a way to do that yet.

---

### Post by mark_k on 2008-02-12
If you want to go the webdav route, it apparently takes a little elbow grease. My ~/.tomboy.log file mentions

  2/12/2008 5:44:13 PM [DEBUG]: Unable to locate 'wdfs' in your PATH



[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/133656](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/133656)
  - mentions the package to download compile and install.

[http://blog.vaxius.net/?p=18#comment-466](http://blog.vaxius.net/?p=18#comment-466)
  - mentions some prerequisites that I ended up needing.


- Mark

---

### Post by mark_k on 2008-02-13
Looks like the more official set of instructions for getting this going are here

[http://live.gnome.org/SeanFritz/UbuntuGutsyTomboySync]("http://live.gnome.org/SeanFritz/UbuntuGutsyTomboySync")

---

