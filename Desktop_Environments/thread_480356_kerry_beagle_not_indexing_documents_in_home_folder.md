---
title: "kerry beagle not indexing documents in home folder"
date: 2007-06-21
forum: Desktop Environments
---

### Post by brazzmonkey on 2007-06-21
hi there,
any kubuntu user in here who successfully uses kerry, this KDE beagle frontend ?
i'm having troubles with it because it doesn't index my documents at all, only contacts and emails from kdepim (kmail, kadressbook, kontact...).
actually i don't really care about searching email and kontact with kerry, because kontact already provides a search function. so basically, as kerry/beagle doesn't index my personal documents, it's useless to me.

kerry IS configured to index files in my home folder, i even tried to manually add every single subfolder. no luck.
man kerry/beagle backends ARE enabled, except a few useless one.
i'm running out of ideas...

i'd appreciate to get some feedback from kubunteros, either to give me some advices or to confirm they do encounter similar issues so that i can file a bug report.

cheers.

---

### Post by casanostra on 2007-06-22
I don't use kerry, but I've had the same problem as you describe. I found the solution, too - at least in my case, there were to beagle daemons started at login, namely a beagled and a beagled --replace . the latter replaces any existing beagled-process. I don't know where it came from in the first place, but deleting it from the startup process solved the problem.

Hope that helps.

---

### Post by brazzmonkey on 2007-06-22
where is this beagled --replace ? is it a startup script or what ?
thanks for helping !

---

### Post by casanostra on 2007-06-26
Just delete it from System > Preferences > Sessions. Only the Beagle daemon and the Beagle Search tray icon should be there. You may have to click edit to see which one to delete; there's probably two entries named Beagle daemon (or something similar). You should either restart beagled or do ctrl-alt-backspace before the change takes effect. After that Beagle will start reindexing things, and you should be fine again.

---

### Post by casanostra on 2007-06-26
Sorry, I gave you the GNOME approach.. I don't know my way around KDE, but I'm sure you'll be able to translate my instructions :)

---

### Post by brazzmonkey on 2007-06-26
thanks for trying to help, unfortunately i don't know the equivalent on kde...

---

### Post by brazzmonkey on 2007-06-26
finally i removed my ~/.kerry and ~/.beagle, restarted beagled manually, and it seems to index my files now... i hope this lasts...
somewhat you helped me casanostra, so thanks very much !!

---

