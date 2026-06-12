---
title: "Ubuntu 18.10 - Snaps folder"
date: 2019-02-03
forum: Desktop Environments
---

### Post by yossicochen123 on 2019-02-03
Hello,
I would be happy to explain what this folder is (takes a lot of space). Can I delete it?

Thank you.

---

### Post by deadflowr on 2019-02-03
It's the snap package user configuration folder.
It can only be removed (or at least best to remove) if you have already removed any installed snaps and snapd.

The onus is on you to determine if any of the snap packages installed are ones you really need
(Quite a few have standard Ubuntu packages, but some are exclusively built as snaps
so you'll need to figure out whether you can easily replace the snap package with the normal package or find a different way)

You can see and remove installed snaps with
```
snap list
```
will list all installed snaps, 
then to remove run
```
sudo snap remove <snap-package-name-here>
```
repeat with each snap package installed until no more are listed.

Then to remove the snapd package just
```
sudo apt remove snapd
```
snapd is the program that runs snaps.

Once you remove the snap packages and snapd then go ahead and move the snap folder to the trash heap of history, if you want.

Depending on who you ask the snap directory is a design flaw that they have locked themselves into without a good way to easily fix it.
Here's the well established bug on that:
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1575053]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1575053")

---

