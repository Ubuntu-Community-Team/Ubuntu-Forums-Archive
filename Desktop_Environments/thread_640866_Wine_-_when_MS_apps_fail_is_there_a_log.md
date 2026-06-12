---
title: "Wine - when MS apps fail is there a log?"
date: 2007-12-14
forum: Desktop Environments
---

### Post by johnbl on 2007-12-14
I have been attempting to install an accounting program - MYOBPlus V17 - with zip results. Install from setup.exe appears to go ok but ends shortly in a frozen blue screen of death with the intended app name as a header. Only way out is to either log out or reboot. Just like %$#@! windows itself.... 

Am running the latest version of wine. Other apps - Lotus - install and run without a hitch.
 
Am wondering if there is an ability to log an install under wine so as to be able to, maybe, be able to figure out where an app install hangs / crashes / freezes?

Any ideas out there guys?

Johnbl

---

### Post by ajmorris on 2007-12-14
As far as i know, wine by default does not keep a log, you could start a new app report on the app database on winehq with the full output of the CLI when trying to install this app, and see if someone comes back with fixes for it.

---

### Post by MrFSL on 2007-12-14
> Am wondering if there is an ability to log an install under wine so as to be able to, maybe, be able to figure out where an app install hangs / crashes / freezes?

Any ideas out there guys?

Johnbl

Sure... when installing using wine just type from a terminal:
```
wine Application.exe
```
Obviously where Application.exe is the name of the installer.

---

### Post by johnbl on 2007-12-18
Well I've done that and thanks for the suggestion. Any idea where wine stores these log files?

Thanks

John

---

### Post by johnbl on 2007-12-20
> **ajmorris said:**
> As far as i know, wine by default does not keep a log, you could start a new app report on the app database on winehq with the full output of the CLI when trying to install this app, and see if someone comes back with fixes for it.

And " CLI " means ...? Sorry you've lost me. What is CLI and were do I find it so as to be able to provide it?

John

---

### Post by VictorR on 2007-12-20
Try this in terminal:
```

export WINEDEBUG=1 ; wine 'your application name with (possibly) full path'

```

---

### Post by MrFSL on 2007-12-20
> And " CLI " means ...? Sorry you've lost me. What is CLI and were do I find it so as to be able to provide it?


CLI - command line interface ... aka run the application from terminal and copy / paste the output which is displayed in terminal.

---

### Post by johnbl on 2007-12-21
> **VictorR said:**
> Try this in terminal:
```

export WINEDEBUG=1 ; wine 'your application name with (possibly) full path'

```

Thank you, tried that and have posted the output - all double dutch to me - to 

[http://groups.google.com/group/comp.emulators.ms-windows.wine/topics](http://groups.google.com/group/comp.emulators.ms-windows.wine/topics)

Cheers & A Merry Xmas to one & All

Johnbl

---

