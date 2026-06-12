---
title: "The case of the lost crontab file"
date: 2005-09-19
forum: Desktop Environments
---

### Post by Galoot on 2005-09-19
Following the Guide's instructions for [refreshing my IP address](http://ubuntuguide.org/#assignhostnametodynamicip) in the DynDNS Database, I've run across this command in step 6.```
export EDITOR=gedit && sudo crontab -e
```
My question is *where the heck did that file get saved?*

Not to /etc/crontab. It doesn't contain the line I added. And the locate command doesn't find any other crontab files floating around. Typing crontab -e at the command line gives me "no crontab for galoot - using an empty one"

*Where the heck did that file get saved?*

Running the same command a second time brings up the file, with my edit intact, but I don't know where it's grabbing this file from. (The gedit titlebar isn't helpful. It says /tmp/crontab.j8H7128 or something like it.)

What's up? Please enlighten the newb.

---

### Post by Galoot on 2005-09-23
I'm going to start a list of stupid questions, and add this one to it.

Note to self: Do NOT skim man pages.

Note to everyone else: Thanks for not laughing.

---

### Post by jzimmerman on 2008-03-17
The user crontabs get stored in /var/spool/cron on ubuntu.  For some reason this doesn't seem to be mentioned in the man pages.

---

