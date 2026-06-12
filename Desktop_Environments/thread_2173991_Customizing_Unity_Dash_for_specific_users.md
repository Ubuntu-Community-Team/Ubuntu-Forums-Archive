---
title: "Customizing Unity Dash for specific users"
date: 2013-09-12
forum: Desktop Environments
---

### Post by karthikesh on 2013-09-12
Hello,
If I don't want an application to be displayed in the Unity Dash or the applications menu then adding the below line in the
applications'  .desktop file will help.

          NoDisplay=true

Usually the *.desktop files are in /usr/share/applications folder.  And adding the above line affects all user sessions.

I have an admin user and a regular user. I am trying to mask this application only for the regular user. And the
admin user should still be able to see all the applications.

Question:
1. Is it possible to have different set of *.desktop files for every user instead of in the common folder /usr/share/applications ?

2. Is there any GUI app that could help me do this customization for every individual user ?

Thanks.

---

### Post by deadflowr on 2013-09-12
I don't know how to restrict the system wide use of /usr/share files.
But each user has it's own place for desktop files.
Look in the users .local/share/applications folder.

/home/user/.local/share/applications

You can place apps .desktop files in here and they will only be accessible by that user.

---

### Post by Jonathan Precise on 2013-09-12
> **karthikesh said:**
> Hello,
If I don't want an application to be displayed in the Unity Dash or the applications menu then adding the below line in the
applications'  .desktop file will help.

          NoDisplay=true

Usually the *.desktop files are in /usr/share/applications folder.  And adding the above line affects all user sessions.

I have an admin user and a regular user. I am trying to mask this application only for the regular user. And the
admin user should still be able to see all the applications.

Question:
1. Is it possible to have different set of *.desktop files for every user instead of in the common folder /usr/share/applications ?

2. Is there any GUI app that could help me do this customization for every individual user ?

Thanks.

1. I really don't know how to solve your first question.

[HR][/HR]2. Try to use the gnome classic session (if not there, install it) for the regular user. Run:

```
alacarte
```

as their user. Remove the application from his/her menu by viewing each sub-menu and finding the application and un-ticking the check-box next to it.

If this solved it, mark as solved by going to thread tools.

---

### Post by karthikesh on 2013-09-17
> **deadflowr said:**
> I don't know how to restrict the system wide use of /usr/share files.
But each user has it's own place for desktop files.
Look in the users .local/share/applications folder.

/home/user/.local/share/applications

You can place apps .desktop files in here and they will only be accessible by that user.



Thanks guys, this helped. I copied all the .desktop files from /usr/share/applications  to /home/user/.local.share/applications. 
And edited every single file whose app should not be displayed in the launcher and added  NoDisplay=true in its
[Desktop Entry] section.

Since there were more than 100 such files to edit it was painful. I wish there is a GUI tool to customize this.
alacarte doesn't help.

BTW, how do I close this as resolved ?

---

### Post by Jonathan Precise on 2013-09-17
Go to thread tools, as shown in the attached picture:
[ATTACH=CONFIG]246315[/ATTACH].

---

### Post by karthikesh on 2013-09-18
Thx Jon.

---

