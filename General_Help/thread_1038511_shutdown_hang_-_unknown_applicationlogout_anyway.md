---
title: "shutdown hang - unknown application/logout anyway?"
date: 2009-01-12
forum: General Help
---

### Post by wynneth on 2009-01-12
Alright, I've got ubuntu Intrepid Ibex pretty much stock installation with conky and a few net apps. I'm having an issue with an application not ceasing when I try to shutdown. I imagine someone can tell me a quick way to list what all is running right then to analyze and find the issue, but I'm very new to linux. I know for a fact that at the point this happens I have conky running, but beyond that I'm not sure. Obviously I could just list what's in system monitor:processes, but I don't think that's where I need to be looking, at least not the smart way to go about it. The last time this happened there were actually two 'unknown application's listed in the 'logout anyway' dialog box. Thanks in advance.

---

### Post by drs305 on 2009-01-12
For your apps/processes:
```

ps -u *yourusername*

```

For all running processes:
```
ps aux  # various switches, see 'man ps'
```

Or:
```

htop  # an advanced form of 'top'

```

Or if you prefer gui:
System, Administration, System Monitor. Processes.

---

### Post by wynneth on 2009-01-12
Wow this is the second this has happened on the forums here. I said I KNOW how to use system monitor, but that will not tell me which app in particular is causing the shutdown hang. I need to know WHICH running processes is causing the shutdown to hang and leave me with the cancel, logout anyway, etc.

---

### Post by drs305 on 2009-01-12
When I read the following I thought you wanted a list and knew it wasn't conky. I edited my post after a few minutes to include how to use System Monitor so others could see how to get there. Sorry I misunderstood your question.
> **wynneth said:**
> I imagine someone can tell me a quick way to list what all is running right then to analyze and find the issue, but I'm very new to linux. I know for a fact that at the point this happens I have conky running, but beyond that I'm not sure. 

You might be able to get some information or see an error message if you try to logoff via the command line. (sudo shutdown or sudo reboot)

---

