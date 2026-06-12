---
title: "Start Oracle with Applications Launcher"
date: 2006-10-19
forum: Desktop Environments
---

### Post by stansaraczewski on 2006-10-19
I just installed Oracle and cannot use the Applications Launcher to start it. 

I get [I]"operation failed. stan is not a member of dba group"
[/I]
stan is the name of my host... 

I can start Oracle at the terminal prompt using the /etc/init.d/oracle-xe start command. 

How do I add a user to the dba group ? It would be nice to be able to use the Applications Launcher to start and stop the database.

---

### Post by marianom on 2006-10-20
1- Go to System->Administration->Users and groups.
Then select the "Group" tab, search for the "dba" group, click on properties and select your user moving from the pane on the left to the pane on the right. Accept the modification and you're done.
2- use usermod from a terminal to add your user to the group:
 sudo usermod -a -Gdba stan

Although I would recommend you keep starting and stoping the database with the oracle default user (just su - oracle in the terminal when you need to do it). It's like the concept behind the "sudo" command in ubuntu: you're protecting the user and yourself from mistakes, other people accesing your machine, et cetera.

---

### Post by stansaraczewski on 2006-10-20
Thank You ! 

I absolutely LOVE this forum and the people in it !

---

