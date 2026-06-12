---
title: "cvscedega error message!"
date: 2007-08-23
forum: Gaming &amp; Leisure
---

### Post by terencepae on 2007-08-23
Hello,

I've followed the guidelines and it successfully installed, made, and my cvscedega should be ready..

However, when I do this:

```
tpae@tpae-workstation:~$ cvscedega
```

it gives me following error message...

```
cvscedega Features:
Reinsert default registry: cvscedega --reregister
Install .reg with regapi:    cvscedega regapi <regfilename.reg>
Install .reg with regedit:   cvscedega regedit [regfilename.reg]
Install a .dll with regedit: cvscedega regsvr32 [filename.dll]
Start winecfg:               cvscedega winecfg
Log to file:                 cvscedega log <normal params>
         eg:                 cvscedega log -debugmsg=+ddraw,+err -- hl.exe -console
 
err:virtual:is_memory_manager_disabled could not retrieve the module file name (reason: 'bad module')
err:client:is_scheduler_disabled could not retrieve the module file name (reason: 'bad module')
Cedega CVS
Usage: /home/patro/.WineCVS/installs/cvscedega/bin/wine [options] [--] program_name [arguments]
The -- has to be used if you specify arguments (of the program)

Options:
   --debugmsg name  Turn debugging-messages on or off
   --dll name       Enable or disable built-in DLLs
   --dosver x.xx    DOS version to imitate (e.g. 6.22)
                    Only valid with --winver win31
   --help,-h        Show this help message
   --managed        Allow the window manager to manage created windows
   --version,-v     Display the Wine version
   --winver         Version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win20,win30,win31)
   --dt             Defer trace until Alt+F12
   --use-dos-cwd    Used to set the DOS current working directory for the process (needs a path)
   --cmdline        Specifies the application's command line
   --monitor-cdrom-eject        Activate monitoring of CD-ROM ejection requests
ERROR: wineserver exiting unexpectantly!
```

please help me! i've looked almost everywhere..

thank you in advance!

---

### Post by cogadh on 2007-08-24
Not that this will help with your problem, but is there a particular reason you are trying CVSCedega? It is actually very out of date, both retail Cedega and Wine have far better support for running games.

---

### Post by terencepae on 2007-08-24
well, i am new to ubuntu and somehow i typed "warcraft 3" and cvscedega came up first and i installed it :)

can you suggest me a great way to run warcraft 3 and be able to play on battle net?

---

### Post by cogadh on 2007-08-24
[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)
Scroll down on the page, it gives you detailed instructions on installing/running WC3 in Wine. It does require you to install Wine first. Follow the instructions here to install the latest Wine:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I would also humbly suggest you click on the "Stuff I've learned about Wine" link in my sig, it is a pretty good starting point for learning to use Wine.

---

