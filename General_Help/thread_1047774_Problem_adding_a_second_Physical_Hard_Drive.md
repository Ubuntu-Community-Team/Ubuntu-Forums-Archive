---
title: "Problem adding a second Physical Hard Drive"
date: 2009-01-22
forum: General Help
---

### Post by imcensored1 on 2009-01-22
My box works perfectly without the second drive installed.  I've tested this several times... 

With it installed, the box runs perfectly when the gui isn't logged in, and i SSH in...

or after a few minutes after the gui is logged in, the box will return to run normally until i try to do anything in the gui to which i get a major lag.  it takes about 2 minutes to open up a terminal window, and another 2 minutes to see my commands onscreen.  During this time, my SSH connection to the box is lagged

example:

19:31:30 up 6 days, 20:30,  3 users,  load average: 0.00, 0.13, 1.31
19:37:18 up 6 days, 20:36,  3 users,  load average: 20.37, 10.78, 6.43

All i did was call up a terminal window in the GUI and change directory.

(the 3 users: my SSH Connection, my VNC connection, and the computer logged in to the gui (my VNC spawns off of that)

Any suggestions?

---

### Post by dcstar on 2009-01-22
> **imcensored1 said:**
> My box works perfectly without the second drive installed.  I've tested this several times... 

With it installed, the box runs perfectly when the gui isn't logged in, and i SSH in...

or after a few minutes after the gui is logged in, the box will return to run normally until i try to do anything in the gui to which i get a major lag.  it takes about 2 minutes to open up a terminal window, and another 2 minutes to see my commands onscreen.  During this time, my SSH connection to the box is lagged

example:

19:31:30 up 6 days, 20:30,  3 users,  load average: 0.00, 0.13, 1.31
19:37:18 up 6 days, 20:36,  3 users,  load average: 20.37, 10.78, 6.43

All i did was call up a terminal window in the GUI and change directory.

(the 3 users: my SSH Connection, my VNC connection, and the computer logged in to the gui (my VNC spawns off of that)

Any suggestions?

You need to see what process is using so much CPU (use the **top** command).

You may also want to double-check your /etc/fstab file for any entries for the second HD.

---

### Post by imcensored1 on 2009-02-02
> **dcstar said:**
> You need to see what process is using so much CPU (use the **top** command).

You may also want to double-check your /etc/fstab file for any entries for the second HD.

The only process that has a lot of CPU time logged is
  155 root      15  -5     0    0    0 S  0.0  0.0  27:32.75 kswapd0

this is with the gui inactive for a few days and my SSH logged in 

here is my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0862b5d4-110e-41d2-bba7-afbe02d14fb6 /               ext3    defaults,erro$
# /dev/sda5
UUID=bbd7fd8d-1674-4a3b-8edb-ced265a26b94 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

