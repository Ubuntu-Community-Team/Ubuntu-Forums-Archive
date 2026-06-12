---
title: "automatic backups in /var/archives - how to switch off?"
date: 2009-05-17
forum: General Help
---

### Post by Heliooos on 2009-05-17
Hi all,
I found out that the problem with full disk after few days is because there are probably some backups generating in /var/archives (home, etc ... - up to 2GB files), which cause me than many problems.

However, I did not find out which app is doing this and how is it possible to switch it off. Any advice?

thanks

PS: maybe particular solution could be if something could automatically delete all files in /var/archives before system shutdown. Is this possible? I do not want to force my visually impaired sister to perform some complicated operations via console each time before system shutdown - I want to make it as much comfortable for her as possible.

---

### Post by geirha on 2009-05-17
It's apt. Whenever you install an application using apt (Add/Remove..., synaptic, apt-get, update-manager, etc...) It first downloads the package to /var/cache/apt/archives/, then it installs it. It will not automatically remove the package file afterwards.

The command ```
sudo apt-get clean
``` will clean out /var/cache/apt/archives.

EDIT: If you want this to run at every reboot, add it to root's crontab.

```
sudo EDITOR=gedit crontab -e  # (replace gedit with your favorite editor if you like) 
``` 

Add a line at the end that reads
```
@reboot /usr/bin/apt-get clean
```

Note that it will run during boot, not during shutdown.

---

### Post by Heliooos on 2009-05-19
> **geirha said:**
> It's apt.

So, problem seems to be solved. The "offender" is not APT but Backup-manager. The guys from Czech forum helped me ;)

The big files were in /var/archives/ and not in /var/cache/apt/archives/. I proved this by putting ```
sudo backup-manager
``` in Terminal - new files were immediately created in /var/archives/, but it also told me, that it is using etc/.backup-manager.conf which finally my brother edited to switch off this feature. ):P

---

