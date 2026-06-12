---
title: "Thunderbird not working after 'backup'"
date: 2008-12-10
forum: General Help
---

### Post by geezerone on 2008-12-10
Hi

Whilst copying .mozilla-thunderbird folder to a backup location and discovering it was moved (!) and lost all setup (like a new install when starting Thunderbird) I copied back but now get a message saying "Thunderbird is already running but not responding, to open a new window close the existing one or restart system"

I have rebooted to no avail and want to get Thunderbird working again.

Any ideas?

---

### Post by sanus|art on 2008-12-10
Check what user account is set to default at:
```
nano ~/.mozilla-thunderbird/profiles.ini
```
try to change to another one (if exist), should be existed after proper backup.

---

### Post by Oceanic on 2008-12-10
CTRL + ALT gives all processes
is thunderbird process still active?

you can easily create a new profile and place all your emails and settings in that new folder.

in the profiles.ini file change to the new folder
[http://kb.mozillazine.org/Profiles.ini_file](http://kb.mozillazine.org/Profiles.ini_file)

handy: [http://kb.mozillazine.org/Files_and_folders_in_the_profile_-_Thunderbird](http://kb.mozillazine.org/Files_and_folders_in_the_profile_-_Thunderbird)

---

### Post by geezerone on 2008-12-10
Thanks guys.

I edited my profile.ini and changed id to my backup version and all is well.

As this was a baptism of fire :lolflag: what ways do you backup profiles for Thunderbird and Firefox?

Cheers.

---

### Post by sanus|art on 2008-12-10
I'd suggest to backup '~/home' to some different drive with 'rSync' (included by default) - something like:
```

rsync --force --log-file=/var/log/rsync-home.log --progress --ignore-errors --delete -avzlpE /home/$USER /backup/BACKUP_HOME
```This will preserve permissions, work in archive mode, synchronize the files, delete the old ones, preserve executeability ... bla-bla.
And to restore - just 'cp -r ANITHING YOU NEED' from '/backup/BACKUP_HOME' and that is it.

Just create '~/Desktop/SYNC-HOME.desktop' file with:
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=SYNC-HOME
Type=Application
Terminal=true
Icon[en_US]=gnome-panel-launcher
Exec=rsync --force --log-file=/var/log/rsync-home.log --progress --ignore-errors --delete -avzlpE /home/$USER /backup/BACKUP_HOME
Name[en_US]=SYNC-HOME
Comment[en_US]=home-Backup
Comment=home-Backup
Icon=/home/sasha/.icons/Clearlooks OSX/scalable/apps/applications-development.png
GenericName[en_US]=home-Backup

```and make it executable.

---

