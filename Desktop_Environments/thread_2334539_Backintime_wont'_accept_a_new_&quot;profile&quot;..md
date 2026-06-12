---
title: "Backintime wont' accept a new &quot;profile&quot;."
date: 2016-08-20
forum: Desktop Environments
---

### Post by lukon on 2016-08-20
After installing 16.04, I can't run Backintime.

When I start Backintime, it asks me to either restore a previous configuration, or create a new one.

1. There is no previous configuration.

2. After filling out the form to create my "Main Profile" configuration, I click "OK" and nothing happens. No configuration file is created.

---

### Post by Germar on 2016-08-20
Please run `backintime-qt4 --debug` from Terminal, configure it again and post the output from Terminal in here if it doesn't proceed again.

---

### Post by lukon on 2016-08-20
> **Germar said:**
> Please run `backintime-qt4 --debug` from Terminal, configure it again and post the output from Terminal in here if it doesn't proceed again.

```
DEBUG: [common/backintime.py:509 arg_parse] Arguments: {'debug': True} | unknownArgs: []

Back In Time
Version: 1.1.12

Back In Time comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; type `backintime --license' for details.

DEBUG: [common/backintime.py:576 getConfig] config file: /home/luke/.config/backintime/config
DEBUG: [common/backintime.py:577 getConfig] profiles: ['1']
DEBUG: [common/pluginmanager.py:88 PluginManager.load_plugins] Register plugin path /usr/share/backintime/plugins
DEBUG: [common/pluginmanager.py:104 PluginManager.load_plugins] Add plugin qt4plugin.py
DEBUG: [common/pluginmanager.py:104 PluginManager.load_plugins] Add plugin notifyplugin.py
DEBUG: [common/pluginmanager.py:104 PluginManager.load_plugins] Add plugin userscriptsplugin.py
DEBUG: [common/tools.py:611 keyring_supported] Found appropriate keyring 'keyring.backends.SecretService'
DEBUG: [common/tools.py:611 keyring_supported] Found appropriate keyring 'keyring.backends.SecretService'
DEBUG: [common/tools.py:611 keyring_supported] Found appropriate keyring 'keyring.backends.SecretService'
DEBUG: [common/config.py:375 Config.set_snapshots_path] Check snapshot folder: /media/WHEEZE
DEBUG: [common/config.py:385 Config.set_snapshots_path] Create folder: /media/WHEEZE/backintime/ExistenceUBUNTU/luke/1
Traceback (most recent call last):
  File "/usr/share/backintime/common/tools.py", line 189, in make_dirs
    os.makedirs( path )
  File "/usr/lib/python3.5/os.py", line 231, in makedirs
    makedirs(head, mode, exist_ok)
  File "/usr/lib/python3.5/os.py", line 231, in makedirs
    makedirs(head, mode, exist_ok)
  File "/usr/lib/python3.5/os.py", line 231, in makedirs
    makedirs(head, mode, exist_ok)
  File "/usr/lib/python3.5/os.py", line 241, in makedirs
    mkdir(name, mode)
PermissionError: [Errno 13] Permission denied: '/media/WHEEZE/backintime'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/share/backintime/qt4/settingsdialog.py", line 1698, in accept
    if self.validate():
  File "/usr/share/backintime/qt4/settingsdialog.py", line 1452, in validate
    if not self.save_profile():
  File "/usr/share/backintime/qt4/settingsdialog.py", line 1351, in save_profile
    ret = self.config.set_snapshots_path( snapshots_path, mode = mode )
  File "/usr/share/backintime/common/config.py", line 386, in set_snapshots_path
    tools.make_dirs( full_path )
  File "/usr/share/backintime/common/tools.py", line 192, in make_dirs
    %(path, str(e)), self, 1)
NameError: name 'self' is not defined
DEBUG: [common/configfile.py:476 Config.set_current_profile] change current profile: 1
luke@ExistenceUBUNTU:~$
```

In 14.04 Backintime use to simply work just fine.

I'm trying to set it up to backup certain folders on a mounted NTSF drive called "SLURP" (all my user files) to another mounted NTFS drive called "WHEEZE" which exists exclusively to be a backup of SLURP.

In 14.04 Backintime never presented me with this "Advanced" stuff to fill out in making a profile.
--------------------------------------------

Apparently, I can't upload a screen-shot of what I'm talking about.

---

### Post by lukon on 2016-08-22
Bump. Still no resolution to this problem.

---

### Post by Germar on 2016-08-23
Sorry, missed your reply. Like I said on GitHub, this is a bug in 1.1.12 which happens only if your user has no write-permissions on the destination.

---

### Post by lukon on 2016-08-28
Cool. Thanks, Germar. But my motherboard BIOS just broke. So I won't have time to try your solution until I replace the motherboard and rebuild the computer.

---

