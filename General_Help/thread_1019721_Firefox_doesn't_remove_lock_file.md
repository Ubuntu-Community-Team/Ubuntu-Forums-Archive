---
title: "Firefox doesn't remove lock file"
date: 2008-12-23
forum: General Help
---

### Post by whollycow on 2008-12-23
I have a few boxes set up to authenticate with LDAP and PAM-mount.  Due to a bug in cifs that is unresolved ([https://bugs.launchpad.net/ubuntu/+source/samba/+bug/117727](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/117727)), users can only use firefox once within the system.  This is because user's the cifs-mounted home directory is unable to delete symbolic links, including the 'lock' file within each user's firefox profile.

1 - Has anyone run into this issue? Are there any good workarounds?  Thus far, the only option is to connect to the server via my Mac and delete the link file each time firefox has been used (Unacceptable)

2 - Is there a way to make each user use a single profile that is stored on each machine?  Firefox isn't an integral part of the lab work and will only rarely be used.

---

### Post by dagnabit dang doohickey on 2008-12-23
A script can be run, just before Firefox launches, that checks for and deletes the lockfile if Firefox isn't already running.
```

#!/usr/bin/env bash

lockfile="${HOME}/.mozilla/firefox/*.default/lock"

[ -L "$lockfile" -a -z "`pgrep -u \"$USER\" 'firefox'`" ] && \
    rm "$lockfile"

firefox &

```

Change Firefox's launcher command to point to the script, instead of Firefox.

---

### Post by whollycow on 2009-02-11
The script will not work for the same reason that Firefox doesn't work; I can't delete the lock file at all because it's a symbolic link.  Any other ideas?

---

