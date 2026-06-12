---
title: "Uninstall update-manager"
date: 2012-01-25
forum: Desktop Environments
---

### Post by Carleas on 2012-01-25
I hate the update-manager application, and I use apt-get to run updates.  I turned off the automatic launching of the application, but it still pops up every time I run ```
apt-get update
```I thought maybe I could just uninstall it, but doing so threatens to remove ubuntu-desktop as well
```
$ sudo apt-get remove update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-desktop update-manager update-notifier
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 2,032 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```
Why is this?  Is there an alternative, more persistent way to tell update-manager to shut the hell up?

---

### Post by jerrrys on 2012-01-25
Ubuntu-desktop is nothing more than an empty mega package.  If it did remove the desktop it would be removing several hundreds megabytes, not just 2M.

I am currently running 11.10 with ubuntu-desktop update-manager update-notifier removed.  So far no side effects.

---

### Post by lolpenguin on 2012-01-26
ubuntu-desktop is a metapackage and is a list of basically what you get from a fresh install, so it is absolutely fine to remove it. No harm done.

---

### Post by mcduck on 2012-01-26
> **Carleas said:**
> I hate the update-manager application, and I use apt-get to run updates.  I turned off the automatic launching of the application, but it still pops up every time I run ```
apt-get update
```I thought maybe I could just uninstall it, but doing so threatens to remove ubuntu-desktop as well


How exactly did you turn off the automatic launching of the application? Just asking because I've turned it off (through dconf), and it most certainly doesn't ever pop up automatically...

Anyway, lolpenguin is right, ubuntu-desktop is just a empty metapackage and removing it will not break anything. However if you ever try to upgrade to a new Ubuntu release version, make sure you reinstall the ubuntu-desktop package beforehands

---

### Post by Carleas on 2012-01-26
Great, thanks jerrrys and lolpenguin!

mcduck, I tried to disable it through its own preferences; to my knowledge I don't have dconf, but I will consider getting it if it can resolve issues like this.

Thanks all.

---

### Post by mcduck on 2012-01-26
I'm pretty sure that the Update Manager's preferences only affect when to check for updates, and not actually how the Update Managwer should behave when there are updates available.

To stop the Update Manager from popping up when updates are available, you need to use gconf-editor or dconf-editor (depending on which Ubuntu version you are using). Gconf-editor is installed by default in 11.04 and older releases, while dconf-editor must be installed manually and is included in the [dconf-tools]("apt:dconf-tools") package.

...actually if you are running 11.10, then opening a terminal and executing the following command will also do the trick:

```
gsettings set com.ubuntu.update-notifier auto-launch false
```

If you have "Update-notifier" whitelisted in systray (once again done in dconf), this will give you a notification icon about available updates instead of popping up the Update Manager. If you don't want even that, just remove "Update-notifier from the whitelist. (the correct location in dconf is *com.canonical.unity.panel systray-whitelist*). I can't remember if it's included in the list by default or not, so you'll have to check that yourself.

---

