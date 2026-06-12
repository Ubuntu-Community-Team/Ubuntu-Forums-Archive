---
title: "Issue running VMware"
date: 2009-04-28
forum: General Help
---

### Post by RebelsAreWe on 2009-04-28
Intrepid
Gnome

I downloaded and installed VMware2 and have run through the configuration and everything seems like it went through ok, but when I try to run it I get

micah@micah:~$ vmware
Launching VMware Web Access using /usr/bin/xdg-open
Error showing url: Failed to execute child process "/home/micah/Desktop/firefox/firefox" (No such file or directory)


Any ideas? :confused:

---

### Post by doas777 on 2009-04-28
are you trying to access it via web?
otherwise go to your Applications -> System Tools -> VMWare Workstation shortcut and give that a try. I'm not at home so I can't confirm the path, but it obiviously trying to connect online, so unless thats what you want to do, i think your running the wrong binary.

---

### Post by RebelsAreWe on 2009-04-28
I could be wrong, but it was my understanding the newest release of VMware was broswer based.

Either way, I have no program in my "system tools" or "other" menus.

---

### Post by doas777 on 2009-04-28
ok, you are probably using server. disregard my previous comment, as i know nothing about vmware server.

you might wanna reinstall, but i am mighty curious why it thinks firefox would be in a folder on your desktop, rather than at /usr/bin/firefox

good luck

---

### Post by dcstar on 2009-04-29
> **RebelsAreWe said:**
> Intrepid
Gnome

I downloaded and installed VMware2 and have run through the configuration and everything seems like it went through ok, but when I try to run it I get

micah@micah:~$ vmware
Launching VMware Web Access using /usr/bin/xdg-open
Error showing url: Failed to execute child process "/home/micah/Desktop/firefox/firefox" (No such file or directory)


Any ideas? :confused:

There might be many in the Virtualization forum where all VM issues are posted.

---

