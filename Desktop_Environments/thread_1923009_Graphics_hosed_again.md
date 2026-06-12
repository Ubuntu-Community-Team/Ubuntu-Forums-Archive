---
title: "Graphics hosed again"
date: 2012-02-09
forum: Desktop Environments
---

### Post by UltimateCat on 2012-02-09
About 2 to 3 weeks ago my graphics were gone after an update.

I found out that I had a fglrx installed but not configured to use it.
so I tried
```
ati config --initial

```And rebooted but that didn't fix anything as the Catalyst Control Center error message said:
```
NO ATI driver is installed or ATI driver is not functioning properly

```so I went to file  /etc/X11/xorg.conf and tried to copy it into the xorg.conf-backup-120122162143/etc/X11/xorg.config and that didn't work So I opened a terminal and tried this command
```
cp/etc/X11/xorg.conf-backup-120122162143/etc/X11/xorg.config

```Anyway the command that finally solved the problem and gave me my graphics back was:
```
   sudo cp /etc/X11/xorg.conf-backup-xxxxxxxxxxxx/etc/X11/xorg.conf
   
        
```Now since my friend played Grand Theft Auto on my Windows partition side and the game hung up and the only way to stop it was to shut down my tower manually and reboot.  Since that game hung up yesterday I don't have graphics today.

Does anyone have an idea of what is going on here?
And would all of the commands that solved the problem be the answer for this one?
Any advice and input is always appreciated as this has been a repeated issue for many-

---

### Post by UltimateCat on 2012-02-11
The command that solved this graphics issue was:
```
sudo apt-get remove fglrx

```
Than a fresh restart

---

