---
title: "lxde (not full lubuntu) set screen blankout on Dell D430"
date: 2013-06-23
forum: Desktop Environments
---

### Post by edcompsci on 2013-06-23
I haven't been able to do this successfully, but I just found that in /etc/acpi there are various sh scripts that control power options.  For screenblank it looks like this:

```
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"
    . /usr/share/acpi-support/screenblank
    fi
done
```

Looks like maybe I need to look in /usr/share/acpi-support/key-constants or . /usr/share/acpi-support/power-funcs


Any help?

---

### Post by edcompsci on 2013-06-29
OKay I see this script doesn't determine when to blank the screen (after running it), it just blanks the screen.  Now to figure out what programs call this script.

---

### Post by edcompsci on 2013-06-29
OKay I see this script doesn't determine when to blank the screen (after running it), it just blanks the screen.  Now to figure out what programs call this script.

---

### Post by edcompsci on 2013-06-29
I see that in /etc/UPower/UPower.conf it says "# Only the system vendor should modify this file, ordinary users
# should not have to change anything.", but I am tempted to change the timeout value here.

---

### Post by edcompsci on 2013-07-05
I thought I had this solved by changing the number in that file btut it seems not allways to work.  putting on backburner

---

