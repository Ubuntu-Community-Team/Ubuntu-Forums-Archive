---
title: "Synchronizing with Unison and udev"
date: 2009-04-29
forum: General Help
---

### Post by Snip on 2009-04-29
Finally got everything to work! The script is executed by udev whenever a USB drive is connected. The script then checks wether there is a config file for the specific disk in /home/<user>/Sync and acts accordingly. The config file should have the same name as the disk volume ID, which can be found with `sudo vol_id -u /dev/sdxx`

/usr/local/bin/sync_usb
```

#!/bin/bash

# Get volume ID for connected disk
VOLUME_ID=`vol_id -u /dev/$1`
if [[ "$VOLUME_ID" == "" ]]; then
    exit;
fi

# Get the username of the current user
X11User=`who | grep :0\) | cut -f 1 -d ' '`
if [[ -z "$X11User" ]]; then
    exit;
fi

export DISPLAY=":0.0"
export HOME="/home/$X11User"

CONFIG="$HOME/Sync/$VOLUME_ID"
DISK_DIR="/mnt/$VOLUME_ID"
ROOT=""

if [[ -f "$CONFIG" ]]; then
    echo "10" # For zenity at the end this block

    /bin/mkdir -p "$DISK_DIR"
    /bin/mount /dev/$1 "$DISK_DIR"

    while read LINE; do
        # Skip blank lines and comments
        [[ -z "$LINE" ]] && continue
        [[ ${LINE:0:1} == "#" ]] && continue

        if [[ ${LINE:0:4} == "ROOT" ]]; then
            ROOT="${LINE:5}"
            continue
        fi

        if [[ ${LINE:0:4} == "SYNC" ]]; then
            DIR="${LINE:5}"

            [[ -z "$ROOT" || ! -d "$ROOT/$DIR" ]] && continue
            [[ ! -d "$DISK_DIR/$DIR" ]] && mkdir -p "$DISK_DIR/$DIR"
            [[ ! -d "$ROOT/$DIR" ]] && mkdir -p "$ROOT/$DIR"

            /usr/bin/unison -root "$ROOT" -root "$DISK_DIR" -path "$DIR" -batch
            continue
        fi
    done < "$CONFIG"

    /bin/umount "$DISK_DIR"
    /bin/rmdir "$DISK_DIR"
fi | zenity --progress --pulsate --auto-close --title="USB Sync" --text="Synchronizing..."

```

/etc/udev/rules.d/99-sync-usb.rules
```
KERNEL=="sd*", SUBSYSTEMS=="usb", ACTION=="add", RUN+="/usr/local/bin/sync_usb %k"

```

Example config file
```

wouter@wouter-laptop:~$ sudo vol_id -u /dev/sdb1
1B13-F236

```

/home/wouter/Sync/1B13-F236
```

ROOT=/home/wouter

SYNC=Documents/College
SYNC=Music

```

Any suggestions or comments?

---

### Post by TetonsGulf on 2009-12-30
Only one... can you help me understand and use it?

I have Unison running and syncing without a problem. 

For some background, check this out: [http://ubuntuforums.org/showthread.php?t=1367665](http://ubuntuforums.org/showthread.php?t=1367665)

Hopefully it'll help with understanding what I'm trying to set up and learn how to do, but I don't know a ton (okay, anything really other than it can be done :)) about scripting.

Maybe you can help me with the last two parts of my problem (I would love to know how to do it), which are:

[LIST=1]
[*]How to string together profiles so only specific files are sync'd (for example not the entire Home folder, but a few folders like Documents, Pictures, Videos and Music)
[*]How to initiate Unison to start the sync when I plug in the USB drive
[/LIST]

Hope you're still around and are feeling up to teaching!

---

### Post by JeffreyRatcliffe on 2011-05-29
All this worked fine until I upgraded to Natty.

Previously, udev gave me unison-gtk, and when I quitted unison, udev then mounted the USB stick normally.

Under Natty, there seems to be a race condition - either udev gives me unison-gtk, and after quitting, nothing, or it mounts it normally.

Any ideas how to get this working again?

---

