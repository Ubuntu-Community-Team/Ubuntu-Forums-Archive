---
title: "OpenOffice stopped working"
date: 2006-03-04
forum: Desktop Environments
---

### Post by evilregis on 2006-03-04
I was having an issue getting OpenOffice to load.

When I click on an OOo icon I was getting the "Starting OpenOffice" notification in the taskbar and would then get an error that the application failed to load.  I wish I could remember exactly what it said.  However, I was looking up that error and saw suggestions about upgrading OOo to 2 from 1.9 so I tried that.

Now I get no error at all, but it will not load up.  I click an icon (Calc, for instance) and I get the "Starting OpenOffice" and then it disappears.  Nothing else happens.  No errors come up.

I'm new to Linux and was wondering which log file might be a good place to check for anything that might be going awry.

---

### Post by arctic on 2006-03-04
Please open a terminal. Then run oowriter. Are there any error messages? Will it start again if you delete the hidden OpenOffice file from your home-folder? (/home/username/.openoffice.org2)

---

### Post by evilregis on 2006-03-04
```
[Java framework] Error in function createUserSettingsDocument (elements.cxx).jav aldx failed!
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeExce ption'
/usr/lib/openoffice2/program/soffice: line 233: 10777 Aborted                 "$ sd_prog/$sd_binary" "$@"
```

That was the error message displayed in the terminal when I ran Writer.

After removing that .openoffice.org2 directory from my home folder did the trick.  Thanks very much.

Any idea why this would have occurred?

---

### Post by arctic on 2006-03-04
It seems that the java-config files got changed somewhere from version 1.9 to 2.0, thus causing a crash. If config-files run into a conflict of some kind, applications simply will not start. As the config-files are stored in the user account, they can always be removed or renamed, thus writing fresh and default config files for the app without affecting the base system.

---

