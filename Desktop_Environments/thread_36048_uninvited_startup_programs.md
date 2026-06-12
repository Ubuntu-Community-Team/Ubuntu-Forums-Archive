---
title: "uninvited startup programs"
date: 2005-05-21
forum: Desktop Environments
---

### Post by bobgreen5s on 2005-05-21
a couple programs (that I didn't ask to startup)  startup when ubuntu starts up:


[IMG]http://www.isoquad.com/startupprogs.png[/IMG]


the only programs that are specitafied for startup in sessions are netdaemon, netapplet, and xbindkeys

any help is appreciated  :smile:

---

### Post by tread on 2005-05-21
Are you saying everything in that screenshot starts when you login? You prolly saved the session when you logged out before .. 
Goto System->Preferences->Sessions to reset that.

---

### Post by Xian on 2005-05-21
Since you didn't mention it, let's do the basic thing first:

From the main panel:
System > Preferences > Sessions

Make sure that you do not have this ticked:
'Automatically Save Changes To Session'

Close the running programs in your screenshot.

When you log out of your current session don't tick 'Save Current Setup'.
Log back in.

Do the applications re-appear?

---

### Post by bobgreen5s on 2005-05-21
yeah, automatic saving is unchecked and I am not checking saving changes when I logout

---

### Post by Xian on 2005-05-21
Do any of those applications occupy a notification area spot?
If so then just closing the main window won't prevent a startup at login.

---

### Post by bobgreen5s on 2005-05-21
[QUOTE=Xian]Do any of those applications occupy a notification area spot?
If so then just closing the main window won't prevent a startup at login.[/QUOTE]
 only gaim occupies a spot but 9 other applications startup that dont occupy a notification area

and I dont save changes so that shouldn't matter


:(

---

### Post by Xian on 2005-05-21
Okay, let's try to work on just one of those programs.
Humour me as I'm not familiar with this problem.

Do these steps:

1. Close Gaim (any and all instances)
2. Bring up the Logout session box
3. Tick the box to _SAVE_ Current Setup
4. Logout
5. Login

Does Gaim restart now?

---

