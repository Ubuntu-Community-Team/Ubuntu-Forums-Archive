---
title: "Update manager"
date: 2009-06-22
forum: General Help
---

### Post by gandalf458 on 2009-06-22
For some while update manager has stopped notifying me of updates. When I run update manager it first of all tell sme my system is up-to-date but when I click Check it usually finds a whole host of updates. Settings are to check daily. Also, although I OpenOffice 3.1 is available this has not been offered.

Any ideas please?

---

### Post by aesis05401 on 2009-06-22
Do you ever find the update manager program running in the background on your desktop?  

Jaunty changed the default way that users are notified when updates are available - the system now opens the update manager, but does so without giving the new window focus, so it may just be hanging out somewhere. 

My understanding is that this command will change back to taskbar icon notification:
gconftool -s --type bool /apps/update-notifier/auto_launch false

As for newer versons of program suites, have you checked to see if it is in the jaunty repo yet?

---

### Post by Johnny B on 2009-06-22
they changed it so it only opens update manager once a week...
i like the old behavior too

---

### Post by gandalf458 on 2009-06-23
Thanks. I haven't noticed anything running but then I don't often see the desktop as I have my browser open most of the time.

How do I check the repo?

---

### Post by gandalf458 on 2009-06-23
> **Johnny B said:**
> they changed it so it only opens update manager once a week...

Even when the settings are set to daily?

---

### Post by utnu on 2009-06-23
[COLOR="White"].[/COLOR]
maybe bug? 

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)

[COLOR="White"].[/COLOR]

---

### Post by aesis05401 on 2009-06-23
> **gandalf458 said:**
> Thanks. I haven't noticed anything running but then I don't often see the desktop as I have my browser open most of the time.

How do I check the repo?

The easiest way is probably to launch synaptic: 

System/Administration/Synaptic Package Manager

Enter 'openoffice' in the 'QuickSearch' box to view a list of OO related packages (there are a bunch).

Note the columns of data that are available including the version of each package that you have installed, and the latest version in the repositories.

There are many ways to search repos including the use of 'apt-cache search' from command line, but synaptic can do the same things if you are more comfortable with a graphical application.

Edit: If you are looking for ease of installation you should wait for repo versions to propogate downstream from the deb repos.

---

### Post by drs305 on 2009-06-23
You can change how often update-manager runs for normal (non-security) updates. It can be done from within gconf-editor or via the command line. Security updates will always show up when they become available.

System Tools, Configuration Editor: apps > update-notifier
Enable "autolaunch" and set the interval in "regular...". A value of 0 will launch when updates become available.

Via CLI:
```

gconftool -s --type boolean /apps/update-notifier/auto_launch "true"
gconftool -s --type integer /apps/update-notifier/regular_auto_launch_interval  0

```
You can see the note about the "0" setting in the lower panel.

---

### Post by gandalf458 on 2009-06-26
> **aesis05401 said:**
> The easiest way is probably to launch synaptic: 

System/Administration/Synaptic Package Manager

Enter 'openoffice' in the 'QuickSearch' box to view a list of OO related packages (there are a bunch).

Edit: If you are looking for ease of installation you should wait for repo versions to propogate downstream from the deb repos.

Many thanks. I installed OOo 3 on Intrepid so Synaptics didn't seem to realise it was installed. Looks like the repo only has 3.0.1 anyway.

---

