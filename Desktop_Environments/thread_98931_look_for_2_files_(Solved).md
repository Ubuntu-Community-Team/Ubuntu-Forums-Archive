---
title: "look for 2 files (Solved)"
date: 2005-12-04
forum: Desktop Environments
---

### Post by forbmj on 2005-12-04
Hey, I deleted two files accidently, which are /etc/init.d/rc and /etc/init.d/rcS.

Could you send these two files to me by email: [email]forbmj@gmail.com[/email]  or post them here?

Ugent help and many thanks.

forbmj

---

### Post by aysiu on 2005-12-04
I don't know if mine will work on your system, but...

```
#! /bin/sh
#
# rc            This file is responsible for starting/stopping
#               services when the runlevel changes.
#
#               Optimization feature:
#               A startup script is _not_ run when the service was
#               running in the previous runlevel and it wasn't stopped
#               in the runlevel transition (most Debian services don't
#               have K?? links in rc{1,2,3,4,5} )
#
# Author:       Miquel van Smoorenburg <miquels@cistron.nl>
#               Bruce Perens <Bruce@Pixar.com>
#
# Version:      @(#)rc  2.78  07-Nov-1999  miquels@cistron.nl
#

# Un-comment the following for debugging.
# debug=echo

#
# Start script or program.
#
startup() {
  case "$1" in
        *.sh)
                $debug sh "$@"
                ;;
        *)
                $debug "$@"
                ;;
  esac
}

  # Ignore CTRL-C only in this shell, so we can interrupt subprocesses.
  trap ":" INT QUIT TSTP

  # Set onlcr to avoid staircase effect.
  stty onlcr 0>&1

  # Now find out what the current and what the previous runlevel are.

  runlevel=$RUNLEVEL
  # Get first argument. Set new runlevel to this argument.
  [ "$1" != "" ] && runlevel=$1
  if [ "$runlevel" = "" ]
  then
        echo "Usage: $0 <runlevel>" >&2
        exit 1
  fi
  previous=$PREVLEVEL
  [ "$previous" = "" ] && previous=N

  export runlevel previous

  # Is there an rc directory for this new runlevel?
  if [ -d /etc/rc$runlevel.d ]
  then
        # First, run the KILL scripts.
        if [ $previous != N ]
        then
                for i in /etc/rc$runlevel.d/K[0-9][0-9]*
                do
                        # Check if the script is there.
                        [ ! -f $i ] && continue

                        # Stop the service.
                        startup $i stop
                done
        fi
        # Now run the START scripts for this runlevel.
        steps=$(echo /etc/rc$runlevel.d/S*)
        num_steps=0
        for step in $steps; do
            num_steps=$(($num_steps + 1))
            case "${step##/etc/rc$runlevel.d/S??}" in
                gdm|xdm|kdm)
                    break
                    ;;
            esac
        done
        current_step=0

        for i in $steps
        do
                [ ! -f $i ] && continue

                if [ $previous != N ] && [ $previous != S ]
                then
                        #
                        # Find start script in previous runlevel and
                        # stop script in this runlevel.
                        #
                        suffix=${i#/etc/rc$runlevel.d/S[0-9][0-9]}
                        stop=/etc/rc$runlevel.d/K[0-9][0-9]$suffix
                        previous_start=/etc/rc$previous.d/S[0-9][0-9]$suffix
                        #
                        # If there is a start script in the previous level
                        # and _no_ stop script in this level, we don't
                        # have to re-start the service.
                        #
                        [ -f $previous_start ] && [ ! -f $stop ] && continue
                fi
                case "$runlevel" in
                        0|6)
                                startup $i stop
                                ;;
                        *)
                                startup $i start
                                ;;
                esac
                last_step=$(($last_step + 1))
                # 50% of progress for rcS, 50% for our ultimate runlevel
                progress=$(($last_step * 50 / $num_steps + 50))
                if type usplash_write >/dev/null 2>&1; then
                    usplash_write "PROGRESS $progress" || true
                fi
        done
  fi
# eof /etc/init.d/rc
```

```

#! /bin/sh
#
# rcS           Call all S??* scripts in /etc/rcS.d in
#               numerical/alphabetical order.
#
# Version:      @(#)/etc/init.d/rcS  2.76  19-Apr-1999  miquels@cistron.nl
#

PATH=/sbin:/bin:/usr/sbin:/usr/bin
runlevel=S
prevlevel=N
umask 022
export PATH runlevel prevlevel

#
#       See if system needs to be setup. This is ONLY meant to
#       be used for the initial setup after a fresh installation!
#
if [ -x /sbin/unconfigured.sh ]
then
  /sbin/unconfigured.sh
fi

#
#       Source defaults.
#
. /etc/default/rcS
export VERBOSE

#
#       Trap CTRL-C &c only in this shell so we can interrupt subprocesses.
#
trap ":" INT QUIT TSTP

#
#       Call all parts in order.
#
steps=$(echo /etc/rcS.d/S??*)
num_steps=0
for step in $steps; do
    num_steps=$(($num_steps + 1))
done
current_step=0

for i in $steps
do
        # Ignore dangling symlinks for now.
        [ ! -f "$i" ] && continue

        case "$i" in
                *.sh)
                        # Source shell script for speed.
                        (
                                trap - INT QUIT TSTP
                                set start
                                . $i
                        )
                        ;;
                *)
                        # No sh extension, so fork subprocess.
                        $i start
                        ;;
        esac
        last_step=$(($last_step + 1))
        # 50% of progress for rcS, 50% for our ultimate runlevel
        progress=$(($last_step * 50 / $num_steps))
        if type usplash_write >/dev/null 2>&1; then
            usplash_write "PROGRESS $progress" || true
        fi
done

#
#       For compatibility, run the files in /etc/rc.boot too.
#
[ -d /etc/rc.boot ] && run-parts /etc/rc.boot

#
#       Finish setup if needed. The comment above about
#       /sbin/unconfigured.sh applies here as well!
#
if [ -x /sbin/setup.sh ]
then
  /sbin/setup.sh
fi

```

---

### Post by forbmj on 2005-12-04
Thanks a lot. But I find my disk becomes "read only". Does it mean I have to reinstall the system?

---

### Post by aysiu on 2005-12-04
[QUOTE=forbmj]Thanks a lot. But I find my disk becomes "read only". Does it mean I have to reinstall the system?[/QUOTE] I'm not sure I know what you mean by it becoming "read only." At what point did you come across this message?

---

### Post by forbmj on 2005-12-04
I used the single mode to enter the system, but I couldn't create the new file, and got the error: read only system.

Now I am trying to use the rescue mode....hope it to work

---

### Post by aysiu on 2005-12-04
Try typing ```
sudo nano /etc/init.d/rc
``` What happens?

---

### Post by forbmj on 2005-12-04
thanks, in single mode, it doesn't work. I used the rescue mode and finally get back my system with the replaced two files. Many thanks to everyone!

---

