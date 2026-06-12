---
title: "&quot;file open&quot; slow hangs for 30 seconds"
date: 2006-02-23
forum: Desktop Environments
---

### Post by eitan on 2006-02-23
hello,

  a few days ago, this problem started:

    if i use gedit or gnumeric and invoke "file -> open",
  the operation will hang for maybe 30-60 seconds.  otherwise it 
  still works.

    this does not happen for a kde app (say if i use kpdf) or with acroread
  for example.  it does not happen with epiphany or firefox either.

    also, just as strangely, taking a screenshot also hangs
   for even longer, maybe 2-3 minutes before coming up.
   and after it comes up it will be unresponsive (in the meantime
   i've switched to using ksnapshot).

  i have no clue why my desktop (ubuntu gnome 5.10) has started 
  doing this and have no clue how to fix this.
  i have all the updates installed.  any help would be _most_ appreciated.

thanks, eitan

---

### Post by lamego on 2006-02-23
I would check the system log
  /var/log/messages

---

### Post by eitan on 2006-02-23
thanks for the tip.  i tailed /var/log/messages while attempting a file->open from gedit.  nothing.  i also scanned the log file.  i see a lot of atkbd.c messages, here's one:

Feb 23 14:06:58 localhost kernel: [4327254.727000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Feb 23 14:06:58 localhost kernel: [4327254.727000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

though i don't know what could be causing this.

---

