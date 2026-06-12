---
title: "GOK doesn't work"
date: 2006-06-02
forum: Desktop Environments
---

### Post by ashrack on 2006-06-02
I attach the GOK error log:
[ATTACH]10445[/ATTACH]
And also XORG.CONF file:
[ATTACH]10446[/ATTACH]

This issue will hopefully be resolved soon, since a lot of our students with special needs are unable to use DAPPER because of this issue.

bug report here:
[https://launchpad.net/distros/ubuntu/+source/gok/+bug/48074](https://launchpad.net/distros/ubuntu/+source/gok/+bug/48074)

---

### Post by ashrack on 2006-06-04
anyone? any ideas on solving it our handicapped students would really need it

---

### Post by ashrack on 2006-06-04
then I did:
q@zavod:/dev/input$ sudo mkdir mknod /dev/js0 c 13 0

and now I receive the following error when lunching GOK:
```
GTK Accessibility Module initialized
Bonobo accessibility support initialized
The program 'gok' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDevice, invalid or uninitialized input device'.
  (Details: serial 150 error_code 168 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
application finalize called
```

---

### Post by ginn on 2006-06-06
Here comes the solution:
sudo vi /etc/X11/xorg.conf

Comment out these lines:
Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to 
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to 
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to 
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

*** and also ***
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
under Section "ServerLayout"

Now, save the file and reboot.
Enjoy yourself with gok!

---

### Post by ashrack on 2006-06-08
tanx that worked

---

