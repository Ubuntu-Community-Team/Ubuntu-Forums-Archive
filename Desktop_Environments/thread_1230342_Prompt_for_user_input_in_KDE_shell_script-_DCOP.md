---
title: "Prompt for user input in KDE shell script- DCOP?"
date: 2009-08-03
forum: Desktop Environments
---

### Post by hangfire on 2009-08-03
Currently I have a script that brings up a Konsole, and then uses dcop to start a few tabs with different names and run various commands in them. It saves me a lot of time. I run the scripts from icons on my 8.04 KDE desktop. It looks something like this:

```
konsole1=$(dcopstart konsole-script)
dcop $konsole1 konsole-mainwindow#1 resize 700 1000

session1=$(dcop $konsole1 konsole currentSession)
dcop $konsole1 $session1 renameSession SessionOne

session2=$(dcop $konsole1 konsole newSession)
dcop $konsole1 $session2 renameSession SessionTwo

dcop $konsole1 $session1 sendSession '/usr/bin/somecommand'
dcop $konsole1 $session2 sendSession '/usr/bin/someothercmd arg'
```

Sometimes I would like to vary the commands, that is, they won't always have the same arguments. I could just wait for input in the sendSession command, but it would be only for that session.

Is there a simple way to have the script pop up a window, accept an input string from the user, and then return that string for use in the launching shell script?

Thanks
-HF

---

### Post by hangfire on 2009-08-03
After searching for non-existent-in-the-repos xprompt and kdialog, I found and installed zenity. It does (with gdialog, apparently) exactly what I want:

```
ARG=$(/usr/bin/zenity --text="Please enter server name:" --entry)
echo "User entered: ${ARG}"
```

-HF

---

### Post by .nedberg on 2009-08-03
kdialog is installed on my Kubuntu 9.04. I think it was on 8.04 also.

Try 
```

kdialog --inputbox "Please enter server name:" "name.of.default.server"

```
and see what happens

---

