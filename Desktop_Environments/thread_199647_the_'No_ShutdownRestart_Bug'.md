---
title: "the 'No Shutdown/Restart Bug'"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Luke771 on 2006-06-19
This happened twice:
First when I upgraded from Breezy to Dapper, and then againg when clean installing Dapper for the first time (repartitioning and reformatting / )

The lower half of the Shut Down dialog only showed the "Hibernate" button, no Shut down or Restart buttons were visible.
I posted a help request and one of the answers was something like  'this can happen if you have both Gnome  and KDE installed', but I didn't have any KDE. Unless...

I did have *some* KDE apps, though not the whole desktop environment, and I also had the Enlightment Xwindows Manager and Fluxbox, that I installed to check them out.

I have my OSes (Dapper and WinXP) on relatively small partitions and I store the data on a couple of FAT32 partitions that will be still be there no matter how many times I format and reinstall OSes, so I thought OK, let's try that again.
This time I was more careful when choosing what packages to install with Synaptic: No alternative Xwindows managers, no KDE stuff, and this time I see all the buttons I'm supposed to see in the shut down interface.

I'm posting this thread because I got quite some "me too" answers thread where I first described the problem, and I'm hoping that someone would fill the bug report because I'm too lazy to try to figure out how those bug report tools work (don't say it, I know)

BTW one nice suggestion to temporary solve the 'no buttons problem' was to open the terminal and run```
sudo reboot
``````
sudo halt
```

---

### Post by dolphinsonar on 2006-09-19
Go throught these steps first, it might be this simple:

System > Administration > Login Window .... [x] Show Actions menu (check this)

[IMG]http://static.flickr.com/86/247725707_ac81551db9.jpg?v=0[/IMG]

---

### Post by dentaku65 on 2006-09-19
> **dolphinsonar said:**
> Go throught these steps first, it might be this simple:

System > Administration > Login Window .... [x] Show Actions menu (check this)

[IMG]http://static.flickr.com/86/247725707_ac81551db9.jpg?v=0[/IMG]

It is not the problem that there is not the logoff menu, but that it hangs if you choose Reboot or Logoff

---

