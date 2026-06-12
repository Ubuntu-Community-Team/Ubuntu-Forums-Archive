---
title: "Application permissions"
date: 2006-06-17
forum: Desktop Environments
---

### Post by jaywatkins on 2006-06-17
Hello,

I have Xubuntu running on a Dell Optiplex GX-240 (P4 1.7GHz, 256MB, 20GB HDD) that I got for forty bucks!  I was trying to monitor the bar at the top by adding launcher items.  When mapping the launcher to the "executable" in the /etc directory, none of the items will launch due to permissions.  "Access denied" is the message returned.

How would one remedy that?  Edit sudoers?

TIA

---

### Post by x64Jimbo on 2006-06-17
You should look into chmod and chown to find out more about file permissions.
Just type man chmod and man chown

---

### Post by jaywatkins on 2006-06-17
I understand the commands, but I do not know what to do with them.  It seems like the only way to get things done is to log in a s root???  Apart of running everything from the terminal with su, but I am sure there is another way.

How am I able to just open the terminal from the menu and not get a permissions conflict?

TIA

---

### Post by jaywatkins on 2006-06-17
Where would all of the executables be found?  /etc or /bin?

TIA

---

### Post by Ramses de Norre on 2006-06-17
It could be me but I don't understand you.. could you explain what exactely your trying to do? Create launchers for applications? Can you run those applications from terminal as normal user? Are you using the user created by installation?

---

### Post by jaywatkins on 2006-06-17
[QUOTE=Ramses de Norre]It could be me but I don't understand you.. could you explain what exactely your trying to do? Create launchers for applications? Can you run those applications from terminal as normal user? Are you using the user created by installation?[/QUOTE]

I am just trying to add launchers to the panel at the top.

I am having trouble trying to link the launcher to it's intended application.  Mostly because I cannot find, or access is denied.

I can run the apps from the menu, but not the terminal (I really do not know how to do that).   I probably should though...

There is only one account on the system, the one that was created during setup.

TIA

---

