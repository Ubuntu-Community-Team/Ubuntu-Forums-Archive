---
title: "sudo restrictions, allow GUI app installation"
date: 2007-08-31
forum: Desktop Environments
---

### Post by Prowleritus on 2007-08-31
Hello!

I'm deploying an linux class room, consisting of 21 machines running Ubuntu Feisty Fawn.

Giving them full rights would leave me cloning the machines a few times a month,
not what I want :(

So I'm thinking I could jail the members of the group admin to install, remove and configure packages by modifying /etc/sudoers with visudo.

This is what I've done this far:

# add the student to the admin group
gpasswd -a student admin

# modified %admin ALL=(ALL) ALL to:
%admin ALL=/usr/bin/apt-get, /usr/bin/apt-cache, /usr/sbin/synaptic,/usr/bin/tasksel, /usr/bin/gnome-app-install,/usr/bin/update-manager, /usr/bin/software-properties-gtk

This actually works as far as installing with the CLI-cmds (apt-get install e.g),
but the GUIs still fail.

When trying to install something with Add/Remove, the "Checking installed and available applications" pops up, finished the Checking dependencies state, than simply dissapears, leaving the to-be installed package uninstalled.

I'm probably something obvious, can't figure it out tho'.

Any thoughts, hints, idea's?

***
Also, another thing, when I sudo apt-get install, it ignores my proxy settings (the env-var http_proxy=*), do I have to add this to ~/.bashrc ?

---

### Post by Lord Illidan on 2007-08-31
Why not just don't give them admin rights?

---

### Post by Prowleritus on 2007-08-31
because they screw the system up, mbr, disks, they're pretty 'special' people.

---

### Post by Lord Illidan on 2007-08-31
So, don't add them to admin group?

---

### Post by Prowleritus on 2007-08-31
because I want them to be able to install packages?

---

