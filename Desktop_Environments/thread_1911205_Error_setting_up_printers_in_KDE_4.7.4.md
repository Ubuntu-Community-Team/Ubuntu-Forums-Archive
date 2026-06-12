---
title: "Error setting up printers in KDE 4.7.4"
date: 2012-01-18
forum: Desktop Environments
---

### Post by jtappin on 2012-01-18
With the KDE 4.7.4 from oneiric-proposed, any attempt to configure printers using either the control centre or the printer applet give the following error:
```

Configure local and remote Printers

The service `Printer Configuration` does not provide an interface
`KCModule` with keyword
`system—config—printer-kde/system-config-printer-kde.py` The factory
does not support creating cornponents of the specified type

Possible reasons
·An error occurred during your last KDE upgrade leaving an orphaned
control module 
·You have old third party modules lying around
Check tnese points carefully and try to remove the module mentioned in the error message if this fails,
consider contacting your distributor or packager

```

The files in /usr/share/kde4/apps/system-config-printer-kde are:
```

total 516
-rw-r--r-- 1 root root  18369 2011-05-20 14:19 authconn.py
-rw-r--r-- 1 root root  12396 2012-01-17 08:55 authconn.pyc
-rw-r--r-- 1 root root   2882 2009-04-15 04:26 ipp-browse-dialog.ui
-rw-r--r-- 1 root root  31556 2009-04-15 04:26 new-printer.ui
-rw-r--r-- 1 root root  15096 2011-05-20 14:19 options.py
-rw-r--r-- 1 root root  13413 2012-01-17 08:55 options.pyc
-rw-r--r-- 1 root root   7942 2009-04-15 04:26 optionwidgets.py
-rw-r--r-- 1 root root   6618 2012-01-17 08:55 optionwidgets.pyc
lrwxrwxrwx 1 root root     43 2012-01-14 09:52 ppdippstr.py -> ../../../system-config-printer/ppdippstr.py
-rw-r--r-- 1 root root   5847 2012-01-17 08:55 ppdippstr.pyc
lrwxrwxrwx 1 root root     39 2012-01-14 09:52 pysmb.py -> ../../../system-config-printer/pysmb.py
-rw-r--r-- 1 root root   5794 2012-01-17 08:55 pysmb.pyc
-rw-r--r-- 1 root root   2882 2009-04-15 04:26 smb-browse-dialog.ui
lrwxrwxrwx 1 root root     40 2012-01-14 09:52 smburi.py -> ../../../system-config-printer/smburi.py
-rw-r--r-- 1 root root   2744 2012-01-17 08:55 smburi.pyc
-rw-r--r-- 1 root root 179501 2011-05-20 14:19 system-config-printer-kde.py
-rw-r--r-- 1 root root 111574 2012-01-17 08:55 system-config-printer-kde.pyc
-rw-r--r-- 1 root root  71160 2011-05-20 14:19 system-config-printer.ui

```

I tried moving system-config-printer-kde.py (and also system-config-printer*) out of the way and nothing changed.

Does anyone have any clues? (A search in the bugs system for "control center printer" only found gnome-related reports).

---

### Post by kitterma on 2012-01-18
I also have 4.7.4 from oneiric-proposed installed and printer configuration, both through systemsettings and through printer-applet work fine.  

If you've moved files around, I would recommend putting them back to start with.  You have all the correct files in that directory.

Did you restart your session after you upgraded?

---

### Post by jtappin on 2012-01-18
> **kitterma said:**
> If you've moved files around, I would recommend putting them back to start with.  You have all the correct files in that directory.

Did you restart your session after you upgraded?

I did put them back once I found it didn't change anything. And yes I did restart the session after the upgrade (in fact since the problem is on a laptop, it's been rebooted several times since the upgrade).

---

### Post by kitterma on 2012-01-18
This appears to be a periodic problem that pops up now and then (it's not new to 4.7.4).  A bit of Googling suggests variously that reinstalling one of:

system-config-printer-kde
python-kde4
python-qt4-dbus

might help.  I'd try that next.  There's nothing in the code that changed with 4.7.4 that could be causing a problem like this.

---

### Post by jtappin on 2012-01-18
Still no joy, even after a reboot.

Maybe the messages to the terminal after running the workaround suggested in the Debian bug report may give a clue:
```
sudo /usr/bin/kcmshell4 system-config-printer-kde
```
```

AttributeError: 'bool' object has no attribute 'markDefaults'
kcmshell(4629)/python (plugin): Failed to import module 
kcmshell(4629)/kcontrol KCModuleLoader::loadModule: This module has no valid entry symbol at all. The reason could be that it's still using K_EXPORT_COMPONENT_FACTORY with a custom X-KDE-FactoryName which is not supported anymore 

```
(Unfortunately I am no expert in python or KDE internals).

---

### Post by kitterma on 2012-01-18
It's probably not related, but it appears that python-gtk2 gets used in the common parts of printer-config-common.  Do you have that installed?

---

### Post by jtappin on 2012-01-19
It is installed (v 2.24.0-2 according to dpkg -l).

I booted the same machine, in the same environment, using a Siduction (Aptosid fork) install on an external hard drive and the printer config tools worked there, with KDE 4.7.2. So I don't think it's a problem with may machine or the network environment confusing something.

So I'm confused.

---

### Post by kitterma on 2012-01-19
I think you have a variant of [https://bugs.launchpad.net/ubuntu/+source/kdeadmin/+bug/763369](https://bugs.launchpad.net/ubuntu/+source/kdeadmin/+bug/763369).

---

### Post by jtappin on 2012-01-19
Maybe, but those reports all look to refer to samba-shared printers whereas the printers here are all shared via lpd, and are raw postscript printers [*]. There isn't a local printer on this machine.

[*] Unless someone is inadvertently sharing a "private" printer.

---

### Post by kitterma on 2012-01-19
Yes, but I think the underlying error is python-cups/cups looking for a PPD file and not finding any file at all.  That would cause markDefaults to be 'False' - boolean - which is not the object type that the code is exepecting.

That would also explain why some people have this problem and others don't.  I'm not 100% sure on this though.

---

### Post by jtappin on 2012-01-19
Thanks for your investigations.

Do you have any idea how to get around the problem? There are PPD files in /usr/share/ppd, pretty much what I'd expect: postscript & text only in cups-included and numerous HP printers in hplip/HP.

---

### Post by kitterma on 2012-01-19
Not immediately.  I need to figure out a way to replicate this before I can go further with it.  I can't find anything that would be specific to 4.7.4 though.

---

### Post by jtappin on 2012-01-19
It had been a while since I had previously updated the printer configuration, (June 2010, I think) so the problem could have arisen any time since then. 

However as I mentioned, the same machine when booted with Siduction which has KDE 4.7.2 does get a configuration tool, which suggests either 4.7.4 or 4.7.3 as the start of the problem, or a Kubuntu-specific issue.

---

### Post by aebmad on 2012-04-26
I had the same problem with Kubuntu 11.10 - KDE 4.7.4. I had a printer in /etc/cups/printers.conf that was not present in /etc/cups/ppd. I edited this file, removing the printer that was not there and restarted the cups service 'sudo service cups restart'. It worked again. 
I hope it helps

---

### Post by busl on 2012-08-04
> **aebmad said:**
> I had the same problem with Kubuntu 11.10 - KDE 4.7.4. I had a printer in /etc/cups/printers.conf that was not present in /etc/cups/ppd. I edited this file, removing the printer that was not there and restarted the cups service 'sudo service cups restart'. It worked again. 
I hope it helps

you saved my day, aebmad - many thanks!

I had DefaultPrinter in /etc/cups/printers.conf pointed to DeviceURI file:///dev/null - removing it and restarting CUPS did the trick.

---

### Post by tuxd on 2013-04-04
Bug 763369 above helped to fix the issue for me. I had to rename files /etc/cups/printers.conf* and start config printers all over again.

---

### Post by terwilligerjones on 2013-04-10
Well, I was bitten with it today. Printer is an HP Photosmart C4700, connected wirelessly. The printer admin panel fails to work with the "The service Printer Configuration does not provide an interface KCModule with keyword system-config-printer-kde/system-config-printer-kde.py" error. Running from the command line, 
Traceback (most recent call last):
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 445, in on_tvMainList_cursor_changed
    self.fillPrinterTab(name)
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 1267, in fillPrinterTab
    self.fillPrinterOptions(name, editablePPD)
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 1311, in fillPrinterOptions
    ppd.markDefaults()
AttributeError: 'bool' object has no attribute 'markDefaults'
kcmshell(615)/python (plugin): Error while running factory function for Python plugin:  "system-config-printer-kde/system-config-printer-kde.py" 
Traceback (most recent call last):
  File "<string>", line 18, in kpythonpluginfactory_bridge
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 4398, in CreatePlugin
    kcm = u.makeui(component_data, widget_parent)
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 374, in makeui
    self.populateList(start_printer, change_ppd)
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 657, in populateList
    self.on_tvMainList_cursor_changed()
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 445, in on_tvMainList_cursor_changed
    self.fillPrinterTab(name)
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 1267, in fillPrinterTab
    self.fillPrinterOptions(name, editablePPD)
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 1311, in fillPrinterOptions
    ppd.markDefaults()
AttributeError: 'bool' object has no attribute 'markDefaults'
kcmshell(615)/python (plugin): Failed to import module 
kcmshell(615)/kcontrol KCModuleLoader::loadModule: This module has no valid entry symbol at all. The reason could be that it's still using K_EXPORT_COMPONENT_FACTORY with a custom X-KDE-FactoryName which is not supported anymore 

Reinstalling Python-pycurl. I've reinstalled kdeadmin. I moved printers.conf and restarted cups. I noticed that the same printer was in printers.conf under two different names, and corrected that while cupsd was not running. Nothing seems to help. I can administer the printers through localhost:631 cups interface, however.

---

