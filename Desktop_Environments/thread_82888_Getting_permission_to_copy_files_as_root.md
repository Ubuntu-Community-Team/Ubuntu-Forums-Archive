---
title: "Getting permission to copy files as root"
date: 2005-10-27
forum: Desktop Environments
---

### Post by azur on 2005-10-27
i'm new to linux and i'm having troubles coping files to the root, i don't have premition

(sorry for the bad english)

---

### Post by mrtrick on 2005-10-27
You are trying to copy files to / ?

In Ubuntu you use 'sudo' in place of root. The command would be something like:

sudo cp file /path/to/destination/file

---

### Post by TimonVO on 2005-10-27
you have to perform the commands with the "sudo" command, like this:
**sudo mv /home/foo/bar.text /root**
in a terminal
or if you use the file browser do this:
**sudo nautilus**
in a terminal

if the sudo command asks you for you password, enter your user password you use to log in.

---

### Post by jeffreyvergara.NET on 2005-10-27
[QUOTE=TimonVO]
or if you use the file browser do this:
**sudo nautilus**
in a terminal.[/QUOTE]

I didnt know that until now... Thanks!

---

### Post by Qrk on 2005-10-27
You can also make a launcher on the panel (or add it in the menus) that runs the command:

gksudo "nautilus --nodesktop /" 

That starts you off in the / directory, and gives you root permissions. I have it on my panel with an icon of a swiss army knife.

---

### Post by azur on 2005-10-27
i'm tying to install panda antivirus
for doing that i have to past two briefcases in the root
when i drag form desktop to root it syas i dont have premition

edit:

not root but /

---

### Post by mostwanted on 2005-10-27
$ sudo nautilus

That should do it. You've been answered several times now you know :p

---

