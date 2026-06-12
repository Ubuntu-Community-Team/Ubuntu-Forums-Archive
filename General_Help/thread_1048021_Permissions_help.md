---
title: "Permissions help"
date: 2009-01-23
forum: General Help
---

### Post by bigtex79 on 2009-01-23
I'm still new to Ubuntu 8.10 and I am trying to get the permissions corrected or rather I want to make sure I have all the proper permissions.  The reason for this is I'm trying to install Cedega, when I choose multi-user install then designate /home/bigtex79/Cedega as the folder to install to it says the following:

Sorry, you don't seem to have the necessary permissions to continue. Please ask your administrator to perform this operation or re-run the program as a user with administrative privileges. Alternatively you may chose a single-user installation.

I read here [http://ubuntuguide.org/wiki/Ubuntu:Intrepid#User_Administration]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid#User_Administration") to get to the user administration section is located here:

System > Administration > User Management

However, I don't see any "User Management" all I see is "Users and Groups".  When I click on that and unlock it then go into my username I make sure that I'm apart of the admin group (which I am) but on that web link from above it says to also make sure you are apart of the adm and sudo groups.  But I don't see any adm and sudo groups.  Am I looking in the wrong area?  Any help would be greatly appreciated.

---

### Post by lykwydchykyn on 2009-01-23
When you enter the command to install cedega, put "sudo" in front of it.  This will prompt you for your password, and you'll be running it with administrative priveleges.

---

### Post by Yellow Pasque on 2009-01-23
> but on that web link from above it says to also make sure you are apart of the adm and sudo groups
IIRC that's deprecated/outdated information. Modern Ubuntu versions use the admin group to determine sudo/root privileges. The issue here appears to be that you're not launching the Cedega installer with root permissions.
How do you launch the Cedega installer?

---

### Post by bigtex79 on 2009-01-23
> **Temüjin said:**
> IIRC that's deprecated/outdated information. Modern Ubuntu versions use the admin group to determine sudo/root privileges. The issue here appears to be that you're not launching the Cedega installer with root permissions.
How do you launch the Cedega installer?

I launch it from Applications > Games > Cadega Gaming Service.  Well, I think I might have resolved the issue by just installing it using the "single user" option.  However, I have a new issue now (lol) after installing Elder Scrolls IV: Oblivion and I apply a NO DVD patch I have so I don't have to keep using the DVD it won't run.  I get to the Oblivion menu but when I click on PLAY the screen flickers once and then goes back to the desktop.  I'll play around with it some more to see if I can't fix it or find a solution on it.  If anyone has a suggestion please let me know.  Thanks.

---

