---
title: "Gnome-terminal run command"
date: 2009-01-21
forum: General Help
---

### Post by Streeterer on 2009-01-21
I am trying to create a command that will run a series of commands in a gnome terminal using the --command argument and then leave the terminal open so that I can open another command. I run the terminal on my desktop using [this]("http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop") tutorial. this is the command I have to run at login: ```
gnome-terminal --window-with-profile=DesktopConsole --command="sh /bin/sleepupgrade.sh"
```

The contents of this script is:
```
#!/bin/bash

sleep 13s 
sudo apt-get update 
sudo apt-get upgrade

```

It will run properly, but once the script runs, the terminal stays open but no new commands can be entered. It does not run with the normal streeter@streeter-laptop:~$ prompt either. Any way I could get it to run as me in a standard terminal? Also, I have modified the sudoers file so that sudo does not require a password for apt-get. I am running the latest build of Jaunty. 

Thanks,

--Streeterer

---

### Post by Streeterer on 2009-01-22
Thoughts?

---

### Post by vanadium on 2009-01-22
Add the command "bash" at the end of the script.

---

### Post by Streeterer on 2009-01-22
Thanks a ton!

I think every question I have ever asked on the Ubuntu forums has been solved by one post :)

---

### Post by vanadium on 2009-01-23
Must be that you are asking good precise questions and have been lucky ;)

---

