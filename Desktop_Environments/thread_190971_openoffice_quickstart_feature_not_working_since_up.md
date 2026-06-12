---
title: "openoffice quickstart feature not working since upgrade to dapper"
date: 2006-06-06
forum: Desktop Environments
---

### Post by tomaspineda on 2006-06-06
i upgraded to dapper, and now ooo2's quickstart doesn't work anymore.  in breezy i wasn't using any extra package, just the default checkbox in options / memory / quickstarter... and it worked, only that it started visible on startup (but it started and stayed resident).

since i upgraded to dapper, not only it doesn't load on startup, but if i load ooo2 and then close all instances, it doesn't stay resident.  i went to options / quickstarter and the checkbox isn't checked, but if i activate it, it forgets the setting afterwards.

i also tried to load it in the commandline with soffice -invisible and it does stay resident... problem is i can't open the program until i kill that process.

any tips?  thanks in advance,


tomas pineda
[email]tomas.pineda@gmail.com[/email]

---

### Post by jahtooth on 2006-06-07
This works for me, so you could try some of the following:

- go to System->Preferences->Sessions and, from the "Startup Program" tab, look for anything containing "ooffice" and delete it

- ensure that you exit all instances of ooffice you have running. Check in a terminal with "ps awx | grep office" that no instance is left running ... kill the offenders if need be)

- from a terminal, move aside your existing ".openoffice" and ".openoffice.org2" directories (all your preferences will be forgotten, but you can move the suff back if you need it):
```

% cd
% mv .openoffice.org2 .openoffice.org2-
% mv .openoffice .openoffice-

```

- Now start openoffice normally and go to tools->Options->Memory and, as you did before, check the box for "OpenOffice.org QuickStarter". Verify that all went well by going back to the System->Preferences->Sessions->Startup and you should find the following was added:
```

% ooffice -quickstart -nologo -nodefault

```

you could run this from a terminal or log off and log back in. The system tray icon should be back hopefully.

Hope this helps and good luck.
--
jahtooth

---

### Post by tomaspineda on 2006-06-10
thanks for your help jahtooth, but it didn't work... i did all you said (although i had already purged and reinstalled ooo2), but it still doesn't remember my quickstarting settings: the checkbox stays deactivated no matter how many times i change it.

i executed the command (ooffice -quickstart -nologo -nodefault) manually, then opened an instance of ooo2 and it did load faster... but as soon as i closed that instance, it removed itself from memory (so it's useless as a quickstarter).

any other ideas?  thanks again,


tomas pineda
[email]tomas.pineda@gmail.com[/email]

---

