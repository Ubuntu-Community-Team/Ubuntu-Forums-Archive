---
title: "Need to produce fullscreen &quot;ERROR&quot;, then shut down"
date: 2009-05-27
forum: General Help
---

### Post by doggbat on 2009-05-27
so here's what I need to do.

I am doing a presentation for an english class on an essay about how pencils are better than computers.  I'm going to have half the presentation on OOo, then have a fake "ERRROR" and a shutdown.  So far I have a GIF that flashes ERROR a few tiems then says "system shtuting down"... i have a bash script that runs this GIF in fullscreen, and I'm going to add "sudo shutdown -h +0.2" to it so it shuts down... but the problem is that I don't know how to execute this command from OOo.  I tried putting "bash (insert file path)" as a command linked to keys.

I am running Jaunty Jackalope, any help is greatly appreciated.  Thanks

---

### Post by Diabolis on 2009-05-28
Whats is OOo?

How about running everything inside the script? Something like:
```

Launch application
# sleep 10 minutes
sleep 600
flash gif
shutdown

```

---

### Post by cariboo on 2009-05-28
OOo = OpenOffice.org

---

