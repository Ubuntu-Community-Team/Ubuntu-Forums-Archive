---
title: "KDE crashes after upgrade to 10.10"
date: 2010-10-19
forum: Desktop Environments
---

### Post by jpmallory on 2010-10-19
I've just upgraded to 10.10 and X crashes after every login to KDE.  I am able to use the gnome desktop with no problems.

Tried removing the .kde and .kderc directories, and it still crashes.

---

### Post by jpmallory on 2010-10-19
I've just tried removing my home directory,(moved it and created a new one) and that doesn't seem to fix the issue either. 

Here's the tail of .xsession.errors:

[/usr/bin/akonadi_contacts_resource] akonadi_contacts_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_contacts_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_maildispatcher_agent] No protocol specified
[/usr/bin/akonadi_maildispatcher_agent] akonadi_maildispatcher_agent: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_maildispatcher_agent' returned with exit code 1 (Unknown error)
"/usr/bin/akonadi_maildispatcher_agent" crashed too often and will not be restarted! 
[/usr/bin/akonadi_maildir_resource] No protocol specified
[/usr/bin/akonadi_maildir_resource] akonadi_maildir_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_maildir_resource' returned with exit code 1 (Unknown error)
"/usr/bin/akonadi_maildir_resource" crashed too often and will not be restarted! 
[/usr/bin/akonadi_contacts_resource] No protocol specified
[/usr/bin/akonadi_contacts_resource] akonadi_contacts_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_contacts_resource' returned with exit code 1 (Unknown error)
"/usr/bin/akonadi_contacts_resource" crashed too often and will not be restarted! 
[/usr/bin/akonadi_ical_resource] No protocol specified
[/usr/bin/akonadi_ical_resource] akonadi_ical_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_ical_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_ical_resource] No protocol specified
[/usr/bin/akonadi_ical_resource] akonadi_ical_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_ical_resource' returned with exit code 1 (Unknown error)
"/usr/bin/akonadi_ical_resource" crashed too often and will not be restarted! 
D-Bus session bus went down - quitting
[akonadiserver] D-Bus session bus went down - quitting
[akonadiserver] terminating service threads
[akonadiserver] terminating connection threads
[akonadiserver] stopping db process
Application 'akonadiserver' exited normally...

---

