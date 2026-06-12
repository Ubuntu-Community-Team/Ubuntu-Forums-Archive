---
title: "kpilot = broken"
date: 2005-12-15
forum: General Help
---

### Post by Zaventh on 2005-12-15
The latest packages for kpilot seem completely broken. When I try to run "kpilot", I get:

 ```

kpilot: ERROR: [void KPilotInstaller::startDaemonIfNeeded()] : Can't start daemon : Could not find service 'kpilotdaemon'.

```

Uh.. Maybe that's because it's named kpilot**D**aemon???

So, I run /usr/bin/kpilotDaemon. It runs, but firstly all this comes up:
```

kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for abbrowser_conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for knotes-conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for vcal-conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for todo-conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for mal_conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for sysinfo_conduit
kpilotDaemon: WARNING: [bool SyncAction::SyncMode::setMode(int)] : Bad sync mode 0 requested.
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for abbrowser_conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for knotes-conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for vcal-conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for todo-conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for mal_conduit
kpilotDaemon: WARNING: [void fillConduitNameMap()] : No service for sysinfo_conduit

```

Kpilot is basically pointless without the conduits. So I try to "Configure Kpilot" and all I get is a blank window with OK buttons. I've tried downgraded to an older breezy package but get the same errors....

---

### Post by MartinG on 2005-12-15
Umm .. this isn't much help, but I find kpilot is working fine, using the version with KDE3.5.  What's irritating me is that I had a similar problem and I can't remember how I solved it :-(

I THINK what I did was to uninstall kpilot and remove all its configuration files in ~/.kde/share/config (and all the conduit config files also?), and then re-install onto a "virgin" system.

Anyway, keep trying, it's not terminally broken!  Best of luck!

---

### Post by degasus on 2006-12-14
Martin, you are right, its not broken completly

zaventh, i guess you have compiled it from cvs? i have done this some minutes ago and i got the same errors.

my solution was to change the prefix (default /usr/local) to /usr. i think kpilot wants its library  in /usr/lib/kde3, but now it was copied into /usr/local/lib/kde3.

now it works fine :)

---

