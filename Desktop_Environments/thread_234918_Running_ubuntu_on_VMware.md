---
title: "Running ubuntu on VMware"
date: 2006-08-12
forum: Desktop Environments
---

### Post by section_32 on 2006-08-12
Hi i was wondering if you could help with a ubuntu question, I'm a complete linux virgin so decided to take a look using VMware workstation, it's up and running fine but i want to install the VMware tools for linux but haven't a clue how i do it. I tried the instructions from vmware but they were limited to say the least. When i double click the .pl file it asks whether i want to display, run in terminal or just run, nothing much seems to open on any option. Is there any help anyone can give me. I have a degree in IT so don't worry about tech terms just no experiance with linux

---

### Post by Bonez56 on 2006-08-12
Hi section_32,

What you actually need to do, is extract the VMWare tools tar.gz file using "Archive Manager"

Once it's done, there should be a folder on your desktop named something like "vmware-tools-dist" or something similar, I can't quite remember exactly what it's called!

Now, open a terminal from Applications > Accessories and type:

cd Desktop
cd name-of-vmware-tools-directory
sudo ./vmware-tools-config.pl (or whatever the actual .pl is called, I forget now)

If you do those exact commands, it will first ask for your password, then will continue to launch a text based script that asks you a bunch of questions.

It's quite safe to take the default answers all the way through (especially if you are a little new to Linux)

Once it's complete, restart your computer and you should have a nice new full-screen resolution and it should run a little nicer.

If I have confused you, please ask back and i'll try my best to help out.

Bonez

---

