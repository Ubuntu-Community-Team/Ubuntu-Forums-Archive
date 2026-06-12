---
title: "unison, separate desktop settings from content"
date: 2009-06-27
forum: Desktop Environments
---

### Post by corny on 2009-06-27
users shall get their environment independently of what computers they log on on our net with different laptops, desktops and HTPC. therefore their home directory is sychronized using unison every time they log in and out with gdm. 

works perfectly since years. user can logout on a computer A go over to computer B log in and continues where she/he was.

my policy is to synchronize the whole users /home folder to the single central server, excluding files which are not nessesary (like .trash and files ending on ~, etc)

because of different screen sizes, different sound hw, different power management and other computer specific settings it becomes more and more tricky to exclude the right files from synchronization. also font and desktop settings should be different on a laptop compared to a HTPC.

from your experience: is it better to include /home first, and then to exclude what is not needed - OR - to build up a list of what is really  needed?

in both cases i have to fidle out application by application what settings are related to presentation/layout and what to the use itself, right?

my users unison synchronisation profile (part.):
```
# Roots of the synchronization
root = 
root = ssh://myserver/

# Some regexps specifying names and paths to ignore
ignore = Name *~
ignore = Name .*~
ignore = Name *.tmp
ignore = Path .dbus 
ignore = Name .xsession-errors
ignore = Name .Xauthority
ignore = Name .gnome-system-monitor.*
ignore = Path .gconfd
ignore = Path .metacity/sessions 
ignore = Path .unison 
ignore = Regex .*[Tt]rash.*

# Propagate timestamps of files and force newer one 
# and does not ask in non-conflict situations
times = true
auto = true

# Log actions to the terminal
log = true
logfile = .unison/unison-logfile
```

---

