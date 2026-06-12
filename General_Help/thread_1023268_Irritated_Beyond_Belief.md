---
title: "Irritated Beyond Belief"
date: 2008-12-27
forum: General Help
---

### Post by cj100570 on 2008-12-27
I've been an Ubuntu user for years and I've been running Intrepid Ibex since release without a hitch. I restarted my machine this morning and upon reboot it said that there was some issue with the panel initializing Tomboy so and asked if I wanted to delete it. I said yes and moved on. Now I've noticed that when I load a page in Firefox that the back button no longer works. Not only that, but each time I start tvtime I have to go through the configuration again. I've also noticed numerous other programs such as lifrea, pidgin and boinc are also not working properly anymore. I have my machine set to automatically update and I'm wondering if an update occurred overnight that broke my machine. How do I go about finding out if my machine updated and what was installed?

---

### Post by cariboo on 2008-12-27
You may be running short of hard drive space. In a terminal type:

```
sudo apt-get autoremove
```

and just in case:

```
sudo apt-get clean
```

The first command should clean out /var/cache/apt/archives and leftover dependencies for programs that are no longer installed. The second command is just in case the first command doesn't clean out the archived packages in /var/cache/apt.

Jim

---

