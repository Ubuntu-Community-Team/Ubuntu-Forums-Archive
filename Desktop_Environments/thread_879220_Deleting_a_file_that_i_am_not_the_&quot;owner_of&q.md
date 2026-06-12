---
title: "Deleting a file that i am not the &quot;owner of&quot;"
date: 2008-08-03
forum: Desktop Environments
---

### Post by jmsgz on 2008-08-03
Hi folks
  [LEFT] Have just moved to Ubuntu from M$ and really like the performance increase as well as the obvious benefits of open source software. I have been moving all data over into comparable programs on Ubuntu. Recently downloaded Quasar Accounting to replace quickbooks and could not configure the db server. To make a long story short until i get more knowledgable in linux i figured i would remove the app. All files removed xcept some congfig files in 
/opt/quasar/config/quasar.log
in attempting to delete these i am informed i am not the owner. "quasar was original owner until i deleted that user" I have deleted quasar as owner and group from the system. But the system has assigned this directory and file to 1001/1001. I am unable to delete the file or the directory from mc or alter its permissions. Any suggestions as i think some of the config files altered during setup of quasar has caused installation db problems with its server configuation and ultimate use. 
reinstallation of quasar just uses the same old files.

[/LEFT]
i.e. need help in deleting the above directory and file. 
If i need to change to root user how do i do this and why would i if i am the main user?
thanks in advance
jmsgz

---

### Post by K2712 on 2008-08-03
Ubuntu uses the "sudo" command to grant temporary root access for a given command.  The default user account created during installation is a non-administrator account, for several reasons including security.

If you are getting permissions errors, that usually means you need root access to execute that command(i.e. use "sudo").

A regular user cannot usually delete files from the /opt directory, that's why the system wouldn't let you.

Now, I would execute the following with extreme caution, because once you enter a command with sudo, you can do all kinds of damage to your system.

In this case, you will probably be ok because I doubt you have any other programs that depend on that quasar program.  To remove the directory you provided in your post, open up a terminal and enter the following:

```
sudo rm -R /opt/quasar
```

That will recursively remove the quasar directory under /opt.

Again, be careful while using the sudo command, it is there to protect you from yourself.

---

