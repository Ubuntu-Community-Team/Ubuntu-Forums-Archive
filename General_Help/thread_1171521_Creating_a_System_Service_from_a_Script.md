---
title: "Creating a System Service from a Script"
date: 2009-05-27
forum: General Help
---

### Post by Aysah on 2009-05-27
After successfully migrating from Redhat and testing every custom script we use on a daily basis I was wondering what would I have to do to register a bash script to be a system service that sits constantly in the background.  In Redhat I was able to do it from the gui so i never actually learned what happens in the background.

Any help would be appreciated.  This service script is modified from time to time and sometimes needs to be restarted if that helps.  

Thank You

---

### Post by baseface on 2009-05-27
> **Aysah said:**
> After successfully migrating from Redhat and testing every custom script we use on a daily basis I was wondering what would I have to do to register a bash script to be a system service that sits constantly in the background. In Redhat I was able to do it from the gui so i never actually learned what happens in the background.
 
Any help would be appreciated. This service script is modified from time to time and sometimes needs to be restarted if that helps. 
 
Thank You
 
to make it always running there, you need to add a loop like "while 1, while x != whatever, etc etc
basically you need to learn shell scripting... or whatever language your script is in.

---

### Post by Aysah on 2009-05-27
Well the scripts are looped right now once I started it up manually but I would like to have them start up with the system and then be able to run something like  "service namehere [restart,start,stop]" on a need to need basis.

---

### Post by maheshasolkar on 2009-05-27
> **Aysah said:**
> After successfully migrating from Redhat and testing every custom script we use on a daily basis I was wondering what would I have to do to register a bash script to be a system service that sits constantly in the background.  In Redhat I was able to do it from the gui so i never actually learned what happens in the background.

Any help would be appreciated.  This service script is modified from time to time and sometimes needs to be restarted if that helps.  

Thank You

* Session : If this is a user level script, you can add it to your session startup programs (System -> Preferences -> Sessions).

* Upstart : If you script runs forever by default, you can use upstart (upstart scripts are under /etc/events.d) to control it. I've found this very convenient, personally.

  [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

* Init Scripts : If this is a system level script, you can put it along side others in /etc/init.d and symlink it into appropriate /etc/rcN.d.

* Cron: If this is a script that does not run forever - i.e., starts, does its job and finishes - you can set it as a cron job so that it is run periodically. For more info:

```
  man crontab
```

---

