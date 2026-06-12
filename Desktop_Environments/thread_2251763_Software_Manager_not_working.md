---
title: "Software Manager not working"
date: 2014-11-06
forum: Desktop Environments
---

### Post by Kyle_Ranallo on 2014-11-06
Kinda new to the forums so I apologize if I'm posting this in the wrong section.

I was installing drivers to play dvds on here and i messed up somewhere and Software Center will not open. I tried uninstalling it, which worked, but when I tried installing it it gave me this:

```
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 176, in <module>
    pathname, appinfo_dir=options.app_install_desktop_dir)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 1148, in rebuild_database
    cache.open()
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 261, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 155, in open
    self._list.read_main_list()
SystemError: E:Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

```

---

### Post by deadflowr on 2014-11-06
The medibuntu repositories no longer exist.
You need to remove those entries from the sources.list.d folder.

You can do so by opening the program "Software and Updates" then go to the section Other Software.
Look for the entries marked for medibuntu and uncheck them, or even simply remove them.

Of course, if this system has an entry for the medibuntu repos, then it is quite possible that this is 12.04.
If this is the case, you would need to open the program called "Update Manager" and go to the bottom left corner and click on the bottom marked settings. This will open the same window as the Software and Updates program does.

Once you have disable the medibuntu entry, you will then need to do a full system update.

In 12.04 simply click on the button marked Check and the system will refresh the list of updatable packages, then when it finishes that it'll list the new packages to update, click on Install updates, or whatever it says in the bottom right corner.

In 14.04 open the program called Software Updater, unlike 12.04's update manager, this program will automatically run a refresh.
As with 12.04's update manager, click on the install button to install the updated packages.

Once the system is fully up-to-date the script to install the dvd-playback package will be workable.
The reason you need to do this is because the location of the package was moved when the medibuntu repos were taken off line.
But that happened mid-release of 12.04, so un-updated 12.04 system's still have the medibuntu repos listed.

Hope this makes sense, and is not too confusing.

---

