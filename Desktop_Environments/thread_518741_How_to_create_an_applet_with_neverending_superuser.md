---
title: "How to create an applet with neverending superuser rights?"
date: 2007-08-06
forum: Desktop Environments
---

### Post by krugman on 2007-08-06
Hi guys!

Well, since I have some suspend problems, I have "created" an applet for KDE
which runs the following command: "sudo s2ram -f". Then, it asks for my password, and suspend works!
However, I was wondering whether there would be a way to make the applet a kind of permanent superuser, so that I don't need to enter my password each time I click on the applet to enter Sleep mode.

Thanks for your help!

---

### Post by krugman on 2007-08-07
Wow, it's the first time I have posted here and didn't get an answer:(

Is that because: (i) nobody knows, (ii) nobody cares or (iii) my question was not clear enough???

Basically, I want to create an applet that runs the command "sudo s2ram -f" but without the need to enter my password each time, but only once I create the applet.

---

### Post by weblordpepe on 2007-08-07
Dude I'm still figuring out why the system requires me to have root access to reboot on the command line, but in the GUI I can just hit reboot.

I'd be interested in a little 'sudo' window as well. something that stays in the task tray all day long. Like having a terminal there in a root shell, but not in the way.

---

### Post by happysmileman on 2007-08-07
You need to make it so the file will be run as root, no matter who runs it?

So you would need to run
```
sudo chmod 4755 *file*
```

That would make it so that when the file is run it runs as a process controlled by the root user.

---

### Post by krugman on 2007-08-08
Thank you for the info, but, sorry if this sounds dumb, when you I run this command and on what?
The only thing I have is an icon on my taskbar, which, when I click on it, runs the "sudo s2ram -f" command in a terminal. Do I have to had a sudo chmod command before my command?

---

### Post by miggols99 on 2007-08-08
You could just create a bash script, put an applet into kicker as a command
```

./<insert name of script>.sh

```
The script should include:
```

#!/bin/bash
sudo s2ram -f

```
Then chmod it:
```

sudo chmod 4755 <insert name of script here>

```

---

### Post by krugman on 2007-08-09
Thanks for this info, but I may have misunderstood something since it does not work.

Here what I have done:

1. open Kate, write the code, save under the name Suspend.sh in my home directorysudo
2. chmod it
3.  Then, create an applet for a non KDE application; under "Command line arguments" I wrote  
```

./Suspend.sh
```

and didn't tick the "Run in a terminal" box. However, it does not work.
What went wrong? I must add that when I run the Suspend.sh file in a terminal, it does work.

Thanks:)

---

### Post by salamba on 2007-08-09
Rather than changing permissions on files,  better to just stop sudo prompting you for a password when you run that specific command.
This requires editing the control file for sudo.

From the console run
```
sudo visudo
```
Despite the name it'll probable use nano as the editor.
At then end of this file append a line
```
yourusername   ALL=NOPASSWD:/path/to/your/command
```
Save the file (ctrl-x in nano), start a new console and try your command
```
sudo /path/to/your/command
```
You shouldn't be prompted for a password.

---

