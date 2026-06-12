---
title: "Focal shell.sh desktop shortcut w/sudo?"
date: 2020-09-01
forum: Desktop Environments
---

### Post by marksmarks on 2020-09-01
I created a Focal desktop shortcut for a shell script. 
However, unlike running it in a terminal window and entering my password only once,
running from the desktop shortcut requires entering my password several times, once for every step the script makes.

How could the desktop shortcut be crafted so I only need to enter my password once, upon starting.

References:

1) My Desktop snapupdate.desktop file; 

```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=/usr/local/sbin/snap-update.sh
Name=SnapUpdate
Comment=snapupdate
Icon=/usr/share/icons/hicolor/16x16/actions/package-upgrade.png

```

2) The shell script;

```

#!/bin/bash
# this script starts the snapd service, deletes old snap images, does a refresh and disables it again
# put it in /usr/local/sbin/snap-update and give it executable rights

set -x
systemctl unmask snapd.service
systemctl start snapd.service
systemctl status --no-pager snapd.service
snap refresh
LANG=C snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done
sudo rm /var/lib/snapd/cache/*
systemctl mask snapd.service
systemctl stop snapd.service
kill -9 $(pgrep snapd)

```


3) Original Source : [https://gist.github.com/rubo77/15366925051dd214b18c306f9389a573](https://gist.github.com/rubo77/15366925051dd214b18c306f9389a573)

Thanks,
-------
PS: I also have a date usage desktop shortcut that runs fine (if anyone is interested)

My Desktop graphusage.desktop file;

```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/usr/local/sbin/graphusage.sh
Name=GraphUsage
Comment=graphusage
Icon=/usr/share/icons/hicolor/16x16/actions/package-upgrade.png

```

The shell script;

```

#!/bin/bash
# this script runs vnstati
# put it in /usr/local/sbin/graphusage.sh and give it executable rights
vnstati -s -i enp0s25 -o ~/Desktop/UsageSummary.png

```


See attached desktopIcons.png & graphusagechart.png
-----

---

### Post by scorp123 on 2020-09-02
> **marksmarks said:**
>  How could the desktop shortcut be crafted so I only need to enter my password once, upon starting.

Why not add the commands you need to do to /etc/sudoers file and make it so that you don't need a password?

Examples from my own /etc/sudoers file:  I want to be able to list disk partitions (e.g. from USB sticks), check disk temperatures, and do a few other things, without having to type a password. The code thus looks like:

```

## <snip>
## ... default entries skipped here, the post would get too long otherwise
## </snip>

##
## Here's the stuff I added to the bottom:
##

# Members of "sudoers" can ask 'lsof' about open ports and the programs using them without password
%sudo ALL=(ALL) NOPASSWD: /usr/bin/lsof -n -i -P

# Members of "sudoers" can check last bad login attempts without password
%sudo ALL=(ALL) NOPASSWD: /usr/bin/lastb

# Members of "sudoers" can check 'dmesg' without password
%sudo ALL=(ALL) NOPASSWD: /usr/bin/dmesg

# Members of "sudoers" can check 'fdisk' partitions without password
%sudo ALL=(ALL) NOPASSWD: /usr/sbin/fdisk -l

# Members of "sudoers" can check 'smartctl' for e.g. disk temperature without password
%sudo ALL=(ALL) NOPASSWD: /usr/sbin/smartctl -x /dev/sd[a-z]

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```

You could use the same method and add the commands you need to execute with a "NOPASSWD" clause. But please only use this within reason and don't add potentially dangerous commands to that list, it's very very easy to hose your system that way. Please don't add any commands that have no business of being executed without a password check.

To edit the /etc/sudoers file you need to execute the "visudo" command, e.g.
```
sudo visudo
```

You can also use a different editor and then have "visudo" check if your syntax is correct (something that the "visudo" command would do if you used it directly), e.g.
```
sudo visudo -c -f /etc/sudoers
```

Here's what a syntax check should look like if everything is correct:
```
 sudo visudo -c -f /etc/sudoers

/etc/sudoers: parsed OK
/etc/sudoers.d/README: parsed OK
/etc/sudoers.d/zfs: parsed OK
```

---

### Post by ActionParsnip on 2020-09-02
Or use sticky bit and own as root so it'll run as root when anyone uses it

---

### Post by TheFu on 2020-09-02
> **ActionParsnip said:**
> Or use sticky bit and own as root so it'll run as root when anyone uses it

Not the sticky bit, but the setuid bit.  The sticky bit is used in /tmp/ to prevent non-owners from deleting files/directories.  The **chmod** manpage has a clear description for both.

If it were me, I'd run the entire script with sudo and write the script assuming it always ran under sudo elevated privileges. The OP is being prompted because some commands aren't being run with the needed elevated privileges, so, on his system, a password gets requested.  If the programs were already running with an effective userid of root, then those prompts wouldn't happen.

I'm not a fan of setting up setuid permissions for any script.  That is much to general (anyone), and can probably be abused in ways that non-experts would catch.  As for the sudoers, rather than list each command, just list the exact userid who should be allowed to run this exact script (use the full path) without a prompt for a password.  Inside the script, I'd not trust the PATH environment and would specify every command using the full, exact, correct, path to each command.  This is a best practice for all scripting anyways, so we all should do it in all our scripts.

Never trust the PATH, especially for running elevated privilege commands.

---

### Post by marksmarks on 2020-09-03
Thank You,

scorp123
ActionParsnip
TheFu

As I am only an intermediate Ubuntu user it will take me some time to implement your guidance.

Thanks again!

---

