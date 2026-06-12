---
title: "how to cancel printing processes through terminal?"
date: 2008-12-02
forum: General Help
---

### Post by coolethan on 2008-12-02
i was trying to set up my printer over a network and i didn't really know what i was doing at first so now i have two printing processes that just sit there and alternate between processing and pending every second or so.they won't go away the regular way by clicking cancel. is there a command i can use?

---

### Post by crwmike on 2008-12-02
From the terminal, type,```
cancel *print_job_name*
```
To find the the name of the print job.```
lpstat -t
```
Also I always cancel the queued print jobs before canceling the current print job.

---

### Post by coolethan on 2008-12-02
```
ethan@Nertwab:~$ lpstat -t
scheduler is running
system default destination: E210
device for E210: smb://WORKGROUP/NERTWAB/E210
device for PDF: cups-pdf:/
E210 accepting requests since Tue 02 Dec 2008 06:10:43 PM MST
PDF accepting requests since Mon 01 Dec 2008 03:46:24 PM MST
printer E210 now printing E210-14084.  enabled since Tue 02 Dec 2008 06:10:43 PM MST
printer PDF is idle.  enabled since Mon 01 Dec 2008 03:46:24 PM MST
E210-14083              ethan            22528   Tue 02 Dec 2008 06:10:41 PM MST
E210-14084              ethan           477184   Tue 02 Dec 2008 06:10:43 PM MST
ethan@Nertwab:~$ cancel E210-14083
cancel: cancel-job failed: Job #14083 is already completed - can't cancel.
ethan@Nertwab:~$ cancel E210-14084
cancel: cancel-job failed: Job #14084 is already completed - can't cancel.
ethan@Nertwab:~$ 
```

WTF the processes are still siting in there being retarded but if the job was completed then they should remove themselves from the list.

---

### Post by coolethan on 2008-12-02
mwwaahahahahahahaha mwahahahahaeee those commands didn't work so i did the next best thing which was delete my printer from the computer, that worked. The printer didn't work anyways which i think is because i don't really have a network setup on my xp computer anyways, i just have a router siting between it and the modem that gives me internet.

---

### Post by crwmike on 2008-12-02
Well, that one of doing it.

---

