---
title: "zeitgeist won't start"
date: 2011-04-25
forum: Desktop Environments
---

### Post by mpmackenna on 2011-04-25
So I removed zeitgeist before I realized all that it did.  I thought it just maintained recent document stuff.  I didn't realize that I would also lose the Unity Dock icons for Applications and Files and Folders.  So I reinstalled zeitgeist but now it won't start.  Any ideas on how I can better troubleshoot this issue?  Thanks, Mike

Removed via
```
sudo apt-get remove zeitgeist
```
Reinstalled via 
```
sudo apt-get install zeitgeist
```
Tried to reset using this command
```
rm ~/.local/share/zeitgeist/activity.sqlite
```
Then I tried the replace option it seems to go OK, but it just hangs at starting the daemon....
```

mike@ubox:~$ sudo zeitgeist-daemon -r
[2011-04-25 11:12:21,303] - DEBUG - singleton - Checking for another running instance...
[2011-04-25 11:12:21,314] - INFO - zeitgeist.sql - Using database: /home/mike/.local/share/zeitgeist/activity.sqlite
[2011-04-25 11:12:21,316] - DEBUG - zeitgeist.sql - Core schema is good. DB loaded in 2.32100486755ms
[2011-04-25 11:12:21,316] - DEBUG - zeitgeist.extension - Searching for system extensions in: /usr/share/zeitgeist/_zeitgeist/engine/extensions
[2011-04-25 11:12:21,317] - DEBUG - zeitgeist.extension - Searching for user extensions in: /home/mike/.local/share/zeitgeist/extensions
[2011-04-25 11:12:21,319] - DEBUG - zeitgeist.extension - No extra extensions
[2011-04-25 11:12:21,319] - DEBUG - zeitgeist.extension - Found extensions: [<class '_zeitgeist.engine.extensions.datasource_registry.DataSourceRegistry'>, <class '_zeitgeist.engine.extensions.gnome_activity_journal.ActivityJournalExtension'>, <class '_zeitgeist.engine.extensions.blacklist.Blacklist'>]
[2011-04-25 11:12:21,319] - DEBUG - zeitgeist.extension - Loading extension 'DataSourceRegistry'
[2011-04-25 11:12:21,320] - DEBUG - zeitgeist.datasource_registry - Loaded data-source data from /home/mike/.local/share/zeitgeist/datasources.pickle
[2011-04-25 11:12:21,320] - DEBUG - zeitgeist.extension - Loading extension 'ActivityJournalExtension'
[2011-04-25 11:12:21,321] - DEBUG - zeitgeist.extension - Loading extension 'Blacklist'
[2011-04-25 11:12:21,321] - DEBUG - zeitgeist.blacklist - No existing blacklist config found
[2011-04-25 11:12:21,322] - INFO - root - Trying to start the datahub
[2011-04-25 11:12:21,340] - DEBUG - root - Running datahub (/usr/bin/zeitgeist-datahub) with PID=6113
[2011-04-25 11:12:21,340] - INFO - root - Starting Zeitgeist service...

```
When I hit the interrupt key I get
```

^C[2011-04-25 11:13:42,086] - INFO - root - Shutting down Zeitgeist interface...
[2011-04-25 11:13:42,086] - DEBUG - zeitgeist.engine - Closing down the zeitgeist engine...
[2011-04-25 11:13:42,086] - DEBUG - zeitgeist.extension - Unloading all extensions
[2011-04-25 11:13:42,087] - DEBUG - zeitgeist.extension - Unloading extension 'DataSourceRegistry'
[2011-04-25 11:13:42,087] - DEBUG - zeitgeist.extension - Unloading extension 'Blacklist'
[2011-04-25 11:13:42,088] - DEBUG - zeitgeist.extension - Unloading extension 'ActivityJournalExtension'

```

Thanks in advance.

---

### Post by bcarlowise on 2011-04-25
I removed zeitgeist myself and then reinstalled only to find the same thing. I recently discovered that the reinstall of zeitgeist does not reinstall 2 apps for Unity. You will need to start the Ubuntu Software Center, do a search for Unity, select the line item that says "Interface designed for efficiency of space and interaction", click on more info and select the bottom two add-ons that are labeled "Application place for unity" and "File place for unity". Those two items will restore the "Applications" and "Files and Folders" launchers on the unity launch bar. You will need to log out and back in once they are installed before you will see them.

---

### Post by mpmackenna on 2011-04-25
Exactly what I was looking for, thanks!  Mike

---

