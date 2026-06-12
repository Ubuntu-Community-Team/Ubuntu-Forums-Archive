---
title: "Unity dash unable to find files, applications"
date: 2011-11-11
forum: Desktop Environments
---

### Post by Anayonkar.Shivalkar on 2011-11-11
Hi,

I'm having 2 issues here:

1) Recently, I was looking for a way to clean file history on Ubuntu 11.10 and found a way to remove zeitgeist database as below:
```

#! /bin/bash

DELPATH=$HOME/.local/share

rm $DELPATH/recently-used.xbel
touch $DELPATH/recently-used.xbel
rm $DELPATH/zeitgeist/activity.sqlite
sudo zeitgeist-daemon --replace

```

This worked pretty well and I could see recent files disappearing. However, after I opened few files, I could see those newly opened files in file history again, which was expected.

So far so good.

However, since last week, I am not able to see a single file in file history. Even after opening hundreds of files and rebooting/logging out numerous times, I don't see a single file in file history.

Is there any way to make file history work properly? It seems now that it has stopped working altogether (i.e. it is not adding any new files to file history).

2) Second issue is about applications in unity dash. Generally, when I want to find installed application, I simply hit super key and type the name of application in textbox. Further, when I want to check which application is available for install, I used super key + a. It then used to give me both lists : installed apps and apps available for install.
This also worked fine till day before yesterday.

However, now, it seems to be stopped working. Below is the testing scenario:

a) log in on unity 3d
b) hit super key and type application name. application is successfully found.
c) hit super key + a and type application name. not a single application is found. the pane is blank. it doesn't even show installed apps.
d) repeat step 2. now there also, not a single application is found. in short, super key works fine initially, but stops working after once super key + a is used.
e) super key + f also doesn't work. this is for file history and standard system folders like desktop, pictures etc. but now it doesn't show a single thing. just blank pane.

Please suggest what can be done here. I really liked the super key + a functionality where it showed both installed and installable apps, but now it doesn't show a single thing. more than that, it even affects other functionality (like simple super key).

Since I don't know command line option for each application, its being very painful to use unity now. I either have to resist myself from hitting super key + a, or log off and log in again after that.

Please suggest what can be done.

Thanks.

P.S. I update my system every day. Is it related to updates?

---

### Post by David006 on 2011-11-13
Get latest Zeitgeist and configuration manager:

```
  sudo add-apt-repository ppa:zeitgeist/ppa
  sudo apt-get update

  sudo apt-get install activity-log-manager
```

(look for 'Activity Log Manager', and open it.)
(set files/directory/activity to ignore)


clear history
```
  zeitgeist-daemon --quit

  ls -l ~/.local/share/zeitgeist/

  sudo rm ~/.local/share/zeitgeist/activity.sqlite.bck  (if present)
  sudo rm ~/.local/share/zeitgeist/activity.sqlite-journal  (if present)
  sudo rm ~/.local/share/zeitgeist/activity.sqlite
```


restart
```
  zeitgeist-daemon &
```

---

### Post by Pr0xY88 on 2011-11-22
Not Working. Unity Dash cant find Files


> 
jan@jan-linux:~$ zeitgeist-daemon --quit
jan@jan-linux:~$ ls -l ~/.local/share/zeitgeist/
insgesamt 8272
-rw-r--r-- 1 jan jan    1024 2011-11-22 09:19 activity.sqlite
-rw-r--r-- 1 jan jan 7984128 2011-11-18 09:23 activity.sqlite.bck
-rw-r--r-- 1 jan jan   32768 2011-11-22 09:22 activity.sqlite-shm
-rw-r--r-- 1 jan jan  387792 2011-11-22 09:22 activity.sqlite-wal
drwxr-xr-x 2 jan jan    4096 2011-11-18 09:38 bb.fts.index
-rw-rw-r-- 1 jan jan     324 2011-11-18 09:23 datasources.pickle
drwxr-xr-x 2 jan jan    4096 2011-11-17 18:01 fts.index
jan@jan-linux:~$ 
jan@jan-linux:~$ sudo rm ~/.local/share/zeitgeist/activity.sqlite.bck
jan@jan-linux:~$ sudo rm ~/.local/share/zeitgeist/activity.sqlite-journal
rm: Entfernen von „/home/jan/.local/share/zeitgeist/activity.sqlite-journal“ nicht möglich: Datei oder Verzeichnis nicht gefunden
jan@jan-linux:~$ sudo rm ~/.local/share/zeitgeist/activity.sqlite
jan@jan-linux:~$ zeitgeist-daemon &
[1] 3517
jan@jan-linux:~$ ** (zeitgeist-daemon:3517): DEBUG: utils.vala:58: DATA_PATH = /home/jan/.local/share/zeitgeist
** (zeitgeist-daemon:3517): DEBUG: utils.vala:71: DATABASE_FILE_PATH = /home/jan/.local/share/zeitgeist/activity.sqlite
** (zeitgeist-daemon:3517): DEBUG: sql-schema.vala:89: schema_version is -1
** (zeitgeist-daemon:3517): DEBUG: extension.vala:146: Loaded extension: ZeitgeistDataSourceRegistry
** (zeitgeist-daemon:3517): DEBUG: extension.vala:146: Loaded extension: ZeitgeistBlacklist
** (zeitgeist-daemon:3517): DEBUG: extension.vala:146: Loaded extension: ZeitgeistHistogram
** (zeitgeist-daemon:3517): DEBUG: ext-storage-monitor.vala:276: VOLUME ADDED: 381c6dd5-8cb1-4c0a-95e9-2975e46c30ea
** (zeitgeist-daemon:3517): DEBUG: extension.vala:146: Loaded extension: ZeitgeistStorageMonitor
** (zeitgeist-daemon:3517): DEBUG: extension.vala:146: Loaded extension: ZeitgeistSearchEngine
** (zeitgeist-daemon:3517): DEBUG: utils.vala:97: LOCAL_EXTENSIONS_PATH = /home/jan/.local/share/zeitgeist/extensions
** (zeitgeist-daemon:3517): DEBUG: ext-data-source-registry.vala:254: Zeitgeist.DataSourceRegistry.register_data_source: com.zeitgeist-project,datahub,gio-launch-listener, Launched desktop files, Logs events about launched desktop files using GIO
** (zeitgeist-daemon:3517): DEBUG: ext-data-source-registry.vala:254: Zeitgeist.DataSourceRegistry.register_data_source: com.zeitgeist-project,datahub,recent, Recently Used Documents, Logs events from GtkRecentlyUsed

** (process:3522): WARNING **: recent-manager-provider.vala:125: Desktop file for python was not found

** (process:3522): WARNING **: recent-manager-provider.vala:125: Desktop file for python was not found
** (process:3522): DEBUG: zeitgeist-datahub.vala:174: Inserting 54 events
** (zeitgeist-daemon:3517): DEBUG: notify.vala:170: Installed new monitor for :1.172

** (zeitgeist-daemon:3517): WARNING **: notify.vala:174: There's already a monitor installed for :1.172#/org/gnome/zeitgeist/monitor/1




---

### Post by seiflotfy on 2011-11-22
> **Pr0xY88 said:**
> Not Working. Unity Dash cant find Files

install gnome activity journal and tell me if you can see files in it...
also open files with gedit or totem and tell me what zeitgeist tells you...
last but not least please run the following script [http://pastebin.com/J0Rn1t86](http://pastebin.com/J0Rn1t86) and tell me the results

---

