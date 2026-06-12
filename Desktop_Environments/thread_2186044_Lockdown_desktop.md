---
title: "Lockdown desktop"
date: 2013-11-05
forum: Desktop Environments
---

### Post by SaintJules on 2013-11-05
Hi everyone.
I'm planning to install Lubuntu on the 25 machines of a school computer lab. Given this specific purpose, it is essential for me to be able to lockdown the desktop so that students cannot alter any part of it, i.e. modify panels, change wallpapers, add/remove icons, etc. 
I know this can be quite easily achieved with gnome, but can I also do it on LXDE?
Thanks

---

### Post by TheFu on 2013-11-05
Can a guest user be used?  The guest login is generated on-the-fly at login and removed after.  I think that is part of core Ubuntu - including LXDE.  I don't logout too often and have too many windows open now, so won't be able to check it anytime soon.

Often it is good to let users have accounts, store some files, limit their storage using quotas, and not allow any programs to be installed. That can be handled using file/directory permissions.  Of course, PHB rules trump everything. ;)

There was someone else here last spring/summer with a similar requirement. Lots of good discussion in that thread too.

---

### Post by SaintJules on 2013-11-06
Thanks for your reply TheFu. What you suggest could definitely be a workaround, sure. If I don't find anything else I'll go with that. 
Sorry what do you mean by phb rules?
The ideal solution for me would be to prevent any customization for the user, so students don't get distracted by messing with the panels or changing the wallpaper. Disabling right-click on the desktop could be nice. Anyway, any chance to point me to that old topic you mentioned?

---

### Post by TheFu on 2013-11-06
[PHB]("https://en.wikipedia.org/wiki/Pointy-haired_Boss")

You could setup user001, user002, ... user999 accounts, have root take ownership of most of the directories - especially ~/.config/ and take away permissions for the user to modify anything.  You'll need to be really strong in understanding user/directory permissions to make this work.

Handing out or helping students create a USB flash drive Ubuntu to run without accessing the HDD might be a better answer. I don't know.  The specific requirements around your situation will dictate more than you can explain or I can guess here.

But ... at some point, each specific user will need write access somewhere.  Perhaps on a central NFS server - again with quotas. Or do you intend for users to retype everything in again from the start when they sit down?  What age are these students?

If the need is just to provide web access - then there are lighter methods than a full Ubuntu install.  A library setup might be easier to manage.

Or a centralized server that is carefully maintained with the tools, programs ... it isn't like Linux is Windows. Each computer does NOT need tools, compilers, IDEs ... just the server needs that stuff and it can be mounted over NFS or run remotely. On a LAN, there isn't much difference in performance either way for 30 workstations or less.

Then there is LTSP.

Lots-o-options.

---

### Post by ian-weisser on 2013-11-06
One key is understanding what students need to be able to do.
Do they need to log in?
Do they need access to shared storage? Account-based storage?
Do they need to save files to the local machine?
Do they need LAN access? Internet access?

You might look at how edubuntu ( [http://www.edubuntu.org/](http://www.edubuntu.org/) ) handles many of these problems. They have been solved before.

---

### Post by SaintJules on 2013-11-07
> **TheFu said:**
> [PHB]("https://en.wikipedia.org/wiki/Pointy-haired_Boss")

You could setup user001, user002, ... user999 accounts, have root take ownership of most of the directories - especially ~/.config/ and take away permissions for the user to modify anything.  You'll need to be really strong in understanding user/directory permissions to make this work.

Handing out or helping students create a USB flash drive Ubuntu to run without accessing the HDD might be a better answer. I don't know.  The specific requirements around your situation will dictate more than you can explain or I can guess here.

But ... at some point, each specific user will need write access somewhere.  Perhaps on a central NFS server - again with quotas. Or do you intend for users to retype everything in again from the start when they sit down?  What age are these students?

If the need is just to provide web access - then there are lighter methods than a full Ubuntu install.  A library setup might be easier to manage.

Or a centralized server that is carefully maintained with the tools, programs ... it isn't like Linux is Windows. Each computer does NOT need tools, compilers, IDEs ... just the server needs that stuff and it can be mounted over NFS or run remotely. On a LAN, there isn't much difference in performance either way for 30 workstations or less.

Then there is LTSP.

Lots-o-options.

The scenario you're describing is surely an ideal one given the educational context I'm working in. That's what I'll probably head to in the long run. But for the time being I just need a quick solution to install a new OS on the students' computers, that's it. I find it quite frustrating that LXDE does not provide anything as simple as disabling right-click or locking features through dconf-editor, but I'll find something. Up to now those PCs have been running Ubuntu 10.10 with a top gnome-panel which I locked down through gconf and Docky on the bottom, locked down in the same way. That's the kind of setup I'm trying to recreate on a new up-to-date distro.

---

### Post by SaintJules on 2013-11-07
> **ian-weisser said:**
> One key is understanding what students need to be able to do.
Do they need to log in?
Do they need access to shared storage? Account-based storage?
Do they need to save files to the local machine?
Do they need LAN access? Internet access?

You might look at how edubuntu ( [http://www.edubuntu.org/](http://www.edubuntu.org/) ) handles many of these problems. They have been solved before.

Students access their own computer but no personal files are meant to be stored on those machines. I used to make them also access a samba share set up on the teacher's computer. And yes, they need Internet access.

---

