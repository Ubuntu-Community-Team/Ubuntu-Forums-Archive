---
title: "Environment variables problem?"
date: 2010-01-03
forum: Desktop Environments
---

### Post by jluix on 2010-01-03
Hi.

I'm working with 9.10, and I've installed InstantClient libraries in order to access Oracle databases through Lazarus+ZeosDBO (FreePascal RAID compiler+DataBase objects).

Once I've compiled a simple example application, that only query a SELECT of a table, it works fine if I execute the program from console, but if I launch it clicking from Nautilus (for example), I get this error message: "None of the libraries can be found: libclntsh.so".

Of course, I've set the correct environment variables in ~/.bashrc:

export ORACLE_HOME=/usr/lib/oracle/11.1.0.1/client
export LD_LIBRARY_PATH="${ORACLE_HOME}/lib"
export TNS_ADMIN=/usr/lib/oracle/11.1.0.1/client

but it seems not to recognize them when launching the application graphically.

After reading a lot online, I've tried setting these variables (almost) everywhere: in /etc/environment (without export and writing the complete path in the second line), /etc/X11/Xinit.d/55gnome-session_gnomerc, /etc/profile, ~/.profile, ~/.gnomerc ... and so on but...

although the variables seems to be set (using env to check it), the answer is always the same error. So:


[LIST=1]
[*]Please, Can you help me?
[*]Can you tell me where to learn (for dummies) how Ubuntu (and general linux) manages the different rc files, because for a not expert like me is a bit confusing so many different configuration files?
[/LIST]
Thanks a lot.

---

### Post by pritamps on 2010-01-04
> **jluix said:**
> Hi.

I'm working with 9.10, and I've installed InstantClient libraries in order to access Oracle databases through Lazarus+ZeosDBO (FreePascal RAID compiler+DataBase objects).

Once I've compiled a simple example application, that only query a SELECT of a table, it works fine if I execute the program from console, but if I launch it clicking from Nautilus (for example), I get this error message: "None of the libraries can be found: libclntsh.so".

Of course, I've set the correct environment variables in ~/.bashrc:

export ORACLE_HOME=/usr/lib/oracle/11.1.0.1/client
export LD_LIBRARY_PATH="${ORACLE_HOME}/lib"
export TNS_ADMIN=/usr/lib/oracle/11.1.0.1/client

but it seems not to recognize them when launching the application graphically.

After reading a lot online, I've tried setting these variables (almost) everywhere: in /etc/environment (without export and writing the complete path in the second line), /etc/X11/Xinit.d/55gnome-session_gnomerc, /etc/profile, ~/.profile, ~/.gnomerc ... and so on but...

although the variables seems to be set (using env to check it), the answer is always the same error. So:


[LIST=1]
[*]Please, Can you help me?
[*]Can you tell me where to learn (for dummies) how Ubuntu (and general linux) manages the different rc files, because for a not expert like me is a bit confusing so many different configuration files?
[/LIST]
Thanks a lot.

If you go to the desktop file of your launcher for the graphical application (Right click on the menus, go to menu editor and find your application), there should be an option "Run in Terminal". Check that and your paths should be exported!

Another way is to edit the executable itself. This might in fact be the better way. Find your application as above, find what command it is using to launch. For example, lets say it's "xyz".

```
sudo gedit /usr/bin/xyz
```

And add the export lines to this file. This should work as well!

---

