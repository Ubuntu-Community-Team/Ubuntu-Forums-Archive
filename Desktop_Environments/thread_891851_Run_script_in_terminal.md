---
title: "Run script in terminal?"
date: 2008-08-16
forum: Desktop Environments
---

### Post by AVT- on 2008-08-16
Hi,

I've got a script to start a Ventrilo server, and it's working, however, if I doubleclick the script to run, there's no terminal window, so I can't watch output, or stop the script later. How would I add a terminal window to it? The script:

#!/bin/sh
cd /etc/ventsrv
/etc/ventsrv/ventrilo_srv

---

### Post by WRDN on 2008-08-16
Right click on the .sh script, select Properties then the Permissions tab. Check the "Allow executing file as program" checkbox. Now, enter the terminal, change to the directory of the script and type:

```
./[name].sh
```

---

### Post by AVT- on 2008-08-16
> **WRDN said:**
> Right click on the .sh script, select Properties then the Permissions tab. Check the "Allow executing file as program" checkbox. Now, enter the terminal, change to the directory of the script and type:

```
./[name].sh
```

I think you've misinterpreted my post. 

I'd like the script to start in a terminal window on **doubleclick**, not by opening terminal, and running it from there manually. I can already do that.

---

### Post by caljohnsmith on 2008-08-16
If you want something you can double-click, pull up a terminal window, and run your script, then try the following:
[LIST=1]
[*]Create a desktop shortcut, "link to application", or whatever it is called in XFCE
[*]Where it asks for the command to run, use:
```
gnome-terminal -e 'bash -c "[COLOR="Blue"]/path_to_script/script.sh[/COLOR]; read -n1"'
```
[/LIST]
It may look a little complicated, but if you don't do something like above and run the script directly, you'll usually get a terminal window that will pop open for the duration of the script and then immediately disappear. The above command opens a terminal window, runs your script, and then instead of automatically disappearing, it will stay open until you press any key (the read -n1 part of it). Also make sure your script is executable by using chmod or setting the permissions through a file browser.

---

### Post by AVT- on 2008-08-16
> **caljohnsmith said:**
> If you want something you can double-click, pull up a terminal window, and run your script, then try the following:
[LIST=1]
[*]Create a desktop shortcut, "link to application", or whatever it is called in XFCE
[*]Where it asks for the command to run, use:
```
gnome-terminal -e 'bash -c "[COLOR="Blue"]/path_to_script/script.sh[/COLOR]; read -n1"'
```
[/LIST]
It may look a little complicated, but if you don't do something like above and run the script directly, you'll usually get a terminal window that will pop open for the duration of the script and then immediately disappear. The above command opens a terminal window, runs your script, and then instead of automatically disappearing, it will stay open until you press any key (the read -n1 part of it). Also make sure your script is executable by using chmod or setting the permissions through a file browser.

Thanks, but what would be the equivalent of this in xfce?

edit: it's xterm. Modified my script with this, and now it works the way I wanted. Thanks! The final script:

#!/bin/sh
cd /etc/ventsrv
xterm -e 'bash -c "/etc/ventsrv/ventrilo_srv; read -n1"'

---

### Post by caljohnsmith on 2008-08-16
Excellent, glad you got it working.

---

