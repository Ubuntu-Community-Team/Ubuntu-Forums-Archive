---
title: "installing apache"
date: 2006-01-29
forum: Desktop Environments
---

### Post by Zarkan on 2006-01-29
Hello. I'm using Ubuntu linux with GNOME, and I'm having problems installing a web server.

Ok, so I want to install apache on my computer. I can't find it in the "Add Applications" list, and I can't install it by writing **apt-get install apache** in the terminal (it denies me access to the **/var/lib/apt/lists/lock - open**, whatever that is). I'm not logged in as root, and I don't know how to. I have the root password, but I can't log in with "root" as username. I've installed applications before, using the "Add Applications" thingie, but apache doesn't seem to be on the list.

Any suggestions?



/Zarkan

---

### Post by moephan on 2006-01-29
There are a few things going on here. You should be able to get apache running easily.

1. You need to add the repositories that have apache in them. First, make sure that you close your add/remove programs app. Then open go system->administration->synaptic. When synaptic opens, go settings->repositories. When the repositories window opens, click the Add button. When the add dialog opens, turn on "community" and " non-free". Click ok on everything until you are back to synaptic and you can see it downloading the new lists. After it's done, search for "Apache" and you should be able to install it easily. Synaptic will start it up for you and configure your computer to run it automatically on startup.

2. The reason you couldn't apt-get was that apt-get and the add new programs app use the same files. You probably left add new programs open, which locked the repository list file. Apt-get wouldn't run becuause it couldn't get a lock on the file.

3. In Ubuntu, you don't log in as root. Instead, you use the "sudo" command before you do any commands that require root level permisions. For example "sudo apt-get install someprogram". Then you put in your user password. This words because the first user created is automatically given admin privledges, but doesn't run as admin. This means that malicious apps can't hijack your user account, and you can't accidentally hork you system doing something absent mindedly while running as root.

Cheers, Rick

---

