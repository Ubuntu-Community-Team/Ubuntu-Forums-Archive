---
title: "Start program after WM starts"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Gentist on 2006-09-17
I don't normally use preconfigured distros like these, so I never really bother with any DM (GDM/KDM/XDM)... Now, I'm running a lightweight Window Manager which lacks the ability to start programs upon starting itself. Since the system is running GDM, I can't/shouldn't really use .xinitrc to start additional programs.

Which file(s) should I edit if I want to start additional programs after the session with the WM has been initialized? If possible, I only want to start these programs if that particular WM is selected.

---

### Post by lagagnon on 2006-09-17
This is a rather difficult question to answer when you have not told us what window manager you are actually using. Each window manager has a different method of doing this task! It is usally a file in ~/.windowmanagername and is often called "startup" or something along those lines....

Another way to do it is to search for the GDM files that startx points to - the actual script file that starts the window manager. I am not at my Ubuntu machine but you can probably find it by using  locate. The startup script file will end with the command "exec windowmanagerexecutablename". You simply add the programs you want started before this line.

---

