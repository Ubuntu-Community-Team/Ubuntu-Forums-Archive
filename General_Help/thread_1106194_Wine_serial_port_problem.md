---
title: "Wine serial port problem"
date: 2009-03-25
forum: General Help
---

### Post by sv1cdn on 2009-03-25
Hello!
Running Ubuntu 8.10 and Wine 1.0.1
Serial ports were running fine until recently something changed and serial ports are not detected in windows applications under wine.
In ~\.wine\dosdevices symbolic links are created yet the problem remains. dmesg shows my serial ports fine and serial ports are working with other linux software.
Any idea?

---

### Post by sv1cdn on 2009-03-26
Quote from winehq.org fellow Martin helped me a lot!

> The following has been tested for Fedora 8 but should also work with any
Linux distro that uses udev to manage devices or runs the contents of
the /etc/rc.d/rc.local script during the boot process.

The problem was that the standard serial ports /dev/ttyS* and the USB
serial ports /dev/ttyUSB* are owned by root and by default only give
read and write access to their owner and the 'uucp' group. This means
that a normal user can't run programs that access them.

I know two solutions:

1) The kludge. Add the command

chmod uga+rw /dev/tty[A-Z]*

into /etc/rd.d/rc.local

By default this script is run as part of the boot process
but contains nothing except comments saying when it is run
and what it is for.

2) A cleaner solution. Add an overriding rule to the UDEV rules set.
These are run at boot time to set up the device files in /dev.
Add the following file to /etc/udev/rules.d and make sure it is
owned by root.root and has "rw-r--r--" permissions. Here's the file:

=========== /etc/udev/rules.d/51-local.rules ==========================
#
# Locally defined rules.
#

#
# Give world read/write access to ttyS* and ttyUSB* serial devices
#
KERNEL=="tty[A-Z]*", GROUP="uucp", MODE="0666"

=======================================================================

You may need to change the file name, which must not overwrite or
modify an existing file and MUST follow the file containing a
rule that sets the serial ports mode to "0660". Run

grep 'KERNEL=="tty[A-Z]*"' /etc/udev/rules.d/*

to check which file that is. In my system its in
/etc/udev/rules.d/50-udev-default.rules but other distros may differ.
Your new file must start with a number that's higher than that of the
file containing the default rule.


Martin

---

