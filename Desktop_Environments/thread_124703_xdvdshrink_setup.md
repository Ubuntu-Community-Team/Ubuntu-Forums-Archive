---
title: "xdvdshrink setup"
date: 2006-02-02
forum: Desktop Environments
---

### Post by psilo357 on 2006-02-02
im getting a certain error when trying to run the program, here is a log of it, if anyone could help me out it would be great.

INFORMATION

   Project:                                  DVD_VIDEO
   File cleanup?                             Yes
   Auto-burn?                                No, prompt
   Save ISO with burn?                       No
   DVD Title:                                1
   Audio channel:                            0
   Subtitle channel:                         None

   PROGRESS   Rip started at 00:55:56

   DVDSHrink Function                        Status    Elapsed

   Reading the chapter list                  Done!    [00:00:00]
   Ripping Title                             Working!Error!
tcextract: no process killed

   DVDShrink has failed!
   Error:
      -> tccat reported an error copying title!
   Command run:
      -> nice -n +19 tccat -i /dev/dvd1 -T 1,-1 -L 2> /tmp/DVD_VIDEO/tccatdebug.txt | tee /tmp/DVD_VIDEO/DVD_VIDEO.vfifo /tmp/DVD_VIDEO/DVD_VIDEO.afifo >/dev/null 2> /dev/null

   Check all your files etc. If it appears that the problem is
   ephemeral restart the script with 'dvdshrink --restart'

   End of command output
   ---------------------------------------

libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd1 with libdvdcss.
libdvdread: Can't open /dev/dvd1 for reading
[tccat] (pid=11310) failed to open DVD /dev/dvd1

   See the log file at /home/randy/DVD_VIDEO.log for more information.
   Exiting!


   Thank you for using OzWare!


Hit any key to close terminal and exit!


thanks guys

peace

---

### Post by psilo357 on 2006-02-02
bumping this thread;, any ideas

peace

---

### Post by psilo357 on 2006-02-02
bump again

---

### Post by psilo357 on 2006-02-03
another day, and i still need help

bump

thanks

---

### Post by syklitengutt on 2006-02-03
ask on the k3b mailing list.
I did and got aswers the next day.
Check out their website for more info...

---

