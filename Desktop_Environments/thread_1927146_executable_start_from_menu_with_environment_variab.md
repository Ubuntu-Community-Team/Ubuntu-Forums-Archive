---
title: "executable start from menu with environment variables"
date: 2012-02-17
forum: Desktop Environments
---

### Post by legendbb on 2012-02-17
10.10 Maverick x64

I have an executable which requires some startup scripts to run.

Set in .bashrc and start from shell work fine. But if I can the shortcut added in menu. It's not working, symptom is obviously missing environment variables.

Added those starup scripts in /etc/environment. The menu item starts with different behavior. Don't understand why.

Current using walkaround is using startup script set environment variable and start executable in one.

Please comment,

---

### Post by Copper Bezel on 2012-02-18
The simplest way would be to change the launcher itself. In /usr/share/applications, you'll find a series of files that are the launchers (.desktop files) for your installed applications. You can open them with gedit (right-clicking them in Nautilus won't give you anything, but you can drag and drop them into a gedit window or use gedit's Open dialogue.) Find the one for the misbehaving application.

Now, copy the file to ~/.local/share/applications. .desktop files in this location will override the system-wide ones for your user. Open this new copy in gedit and find the line that starts with Exec=.

This line is the command that's actually sent when the application is launched. What you want to do is to replace the command that's there now with the path to your startup script. 

Once you do, any GUI method of launching the application will use that .desktop file and run your startup script instead of running the application command directly. 

Does that work for your situation?

---

### Post by legendbb on 2012-02-22
Thank you for the recommendation. I learnt some thing about launcher.
Exec="" in launch is the line I added to menu command line: "bash /${my_startup_script}"; so I still have to use my startup script.

I guess I will have to use the startup script, unless I can flat out all the environment variable in the /etc/environment, or add the start up script to system boot script.

Don't really have time to dig deeper, I will live with the startup script.

Thank your for your knowledge.

---

