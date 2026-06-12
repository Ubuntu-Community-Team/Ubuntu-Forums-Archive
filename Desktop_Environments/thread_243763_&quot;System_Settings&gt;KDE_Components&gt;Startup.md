---
title: "&quot;System Settings&gt;KDE Components&gt;Startup Applications&quot; how work??"
date: 2006-08-25
forum: Desktop Environments
---

### Post by true_friend on 2006-08-25
i added an application to be started up in Startup Applications just like in gnome we add applications in sessions>startup command. but kde is giving error not a valid entry. some thing this kind.
the command is as follows.
'/home/ss/ntlmaps-0.9.9/main.py'
althoung session resotre does this always but i want to run ntlmaps to run in background.
is there anyother way to run it in background??? tried kcron also but could not enter correct command.
plz suggest me and thnx for reading message.
Regards
True_Friend

---

### Post by holy_bazooka on 2006-08-30
there is a much easier way to do this,


 ```
sudo apt-get install ntlmaps

```
ofcourse if you cant acsess the web how r u going to apt-get??. In that case use firefox(which deals with ntlm auth just fine) to go to packages.ubuntu.com, search for ntlmaps in dapper, download and install.
it will ask u about your account details and then set the whole thing to start at system startup via init.

good luck

---

### Post by holy_bazooka on 2006-08-30
there is a much easier way to do this,


 ```
sudo apt-get install ntlmaps

```
ofcourse if you cant acsess the web how r u going to apt-get??. In that case use firefox(which deals with ntlm auth just fine) to go to packages.ubuntu.com, search for ntlmaps in dapper, download and install.
it will ask u about your account details and then set the whole thing to start at system startup via init.

good luck

---

