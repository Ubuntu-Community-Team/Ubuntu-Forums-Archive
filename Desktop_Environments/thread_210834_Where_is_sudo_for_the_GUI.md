---
title: "Where is sudo for the GUI"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Morgen on 2006-07-07
Why doesnt Ubuntu prompt me for a root password when I try to do something I dont have permission to do? I am doing some very simple stuff trying to set up a HTPC and at every turn I am plauged by lack of permission. I know how to do it in terminal but if I already have something right in front of me it is a waste of time to back track and do it again in shell. I just want to have the same control over the os from both side. Doesnt seem like too much to ask.

I am trying to keep a positive attitude but as a new user I am having a very hard time at it. Just seems like the most mundane things are complex.

---

### Post by Blairboy on 2006-07-07
Go to /home/USERNAME/.gnome2/nautilus-scripts and make a file called "Open as root"  Then edit it and paste this into it:

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done


Then when you right click and go to scripts, there will be an open as root option.  You'll have to type in a password, but it's at least done graphically.  If you know you'll be needing to work with a bunch of files that you need permission for, type "sudo su" in console, and then whatever commands you type you won't be bugged about.

Hope this helps.

---

### Post by ed_agamemnon on 2006-07-07
```
gksudo
```

---

### Post by palmiter on 2006-07-07
responding with terminal commands doesn't really address the original post's concerns.

i think a gui for sudo is a great idea, and would love to see a file manager prompt (nautilus, thunar, whatever).

---

### Post by aysiu on 2006-07-07
[quote=palmiter]responding with terminal commands doesn't really address the original post's concerns.

i think a gui for sudo is a great idea, and would love to see a file manager prompt (nautilus, thunar, whatever).[/quote] ```
gksudo
``` **is** a GUI for sudo. Read this link for more details:

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Morgen on 2006-07-07
gksudo is also only half the anwser.

Thank you for the link Aysiu. It not only addressed my problem but explained why I was having a problem. Thanks again.

---

### Post by aysiu on 2006-07-07
Now, as to why that's not included by default--that's a policy decision, one I happen to not agree with.

Ubuntu developers generally feel that people shouldn't have to mess with systemwide configuration files. Maybe in a dream world that would be the case. As it is now, though, most people who use Ubuntu install it themselves... and, thus, have to mess with configuration files.

And most people who migrate to Ubuntu come from Windows and are used to having everything point-and-click.

So, I think a *gksudo nautilus* or *kdesu konqueror* button should come standard. As it is, Konqueror already has a right-click action called "Edit as root."

The ideal solution, of course, would be a warning when you try to edit a systemwide configuration file: "You appear to have administrative privileges. Would you like to edit the systemwide file with those privileges" and then a password box for you to enter your *sudo* password.

Right now, you just get "access denied."

---

