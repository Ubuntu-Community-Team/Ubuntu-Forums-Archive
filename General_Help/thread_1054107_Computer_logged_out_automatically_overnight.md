---
title: "Computer logged out automatically overnight"
date: 2009-01-29
forum: General Help
---

### Post by Luther11 on 2009-01-29
I'm using a brand new desktop with a fresh install of 8.10, amd64. Last night, I turned off my monitor and left the computer on so it would check email and download a bittorrent overnight. I used to do this all the time with my laptop. When I turned on the monitor this morning, I was back at the login screen, so I had to restart Evolution and Transmission. I remember after I went to bed, I heard a beep indicating a new email, and when I started Evolution, the new mail was there before I entered my password, so I know I didn't accidentally logout when I went to bed.

In "Power Management Preferences", in the "On AC Power" tab, the computer is set to never go to sleep, and the display will sleep when inactive for 1 hour. I can't find any configuration options anywhere that relate to logging out automatically.

Any help, fixes, etc. are welcome.

---

### Post by taurus on 2009-01-29
Are you sure it just logged you out instead of rebooting?  

Look at the **uptime** to see how long it has been up.

Applications -> Accessories -> Terminal
```
uptime
```

---

### Post by Luther11 on 2009-01-29
uptime output:
```
 10:51:03 up 18:08,  2 users,  load average: 0.14, 0.08, 0.02
```
So, 18 hours would mean it's been on since yesterday at 16:43, so it's definitely been running continuously.

EDIT: Is there some way I can record the time I logout? Or get that time if it's already recorded? I think that might be valuable information.

---

### Post by Luther11 on 2009-01-30
I left my computer on overnight again, and this time, it did not logout. This may sound like good news, but the fact that I can't replicate the problem makes me think that it will definitely happen again at some random time in the future. :? So, I just don't know what to think about it right now.

---

### Post by sedawk on 2009-01-30
Check
/var/log/messages
(Any new system messages after you left the keyboard)

and
/var/log/Xorg.0.log
(When did X (the desktop environement) start up).

---

### Post by Luther11 on 2009-01-30
I couldn't find anything in those two files. (Xorg.0.log.old didn't go back that far.) But I did find an interesting tidbit in /var/log/syslog.1. Note the line at 00:04:04:
```
Jan 28 23:02:48 hrimfaxi kernel: [22803.756740] hp_event
Jan 28 23:14:20 hrimfaxi kernel: [23495.646226] hp_event
Jan 28 23:17:02 hrimfaxi /USR/SBIN/CRON[8703]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 28 23:19:23 hrimfaxi kernel: [23798.550545] hp_event
Jan 28 23:19:23 hrimfaxi kernel: [23798.603875] hp_event
Jan 28 23:19:23 hrimfaxi kernel: [23798.689213] hp_event
Jan 28 23:42:58 hrimfaxi -- MARK --
Jan 29 00:02:58 hrimfaxi -- MARK --
Jan 29 00:04:04 hrimfaxi gdm[4957]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jan 29 00:04:06 hrimfaxi acpid: client connected from 8906[0:0] 
Jan 29 00:04:07 hrimfaxi kernel: [26482.556360] set status page addr 0x00033000
Jan 29 00:04:08 hrimfaxi gdmgreeter[8921]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks",
```
Does this mean X crashed and restarted?

---

### Post by Hatchetfish on 2009-03-05
A couple seemingly strange questions: 

Do you A) use a bluetooth keyboard or a keyboard with extra 'media' keys, and/or 

B) have a cat or other autonomous key pressing agent in your domicile? ;)

I ask A because a number of people have experienced a similar issue, even when sitting at the machine, of a key press, any key press, on a bluetooth keyboard causing an immediate X crash.  Some multimedia keys cause one as well, bluetooth or not.  That appears to possibly have been fixed, the bluetooth issue is more elusive. B is simply narrowing in on how they might get pressed. ;)

---

