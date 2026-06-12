---
title: "Only one software management tool"
date: 2006-05-22
forum: Desktop Environments
---

### Post by N8MAN1068 on 2006-05-22
..is allowed to run at the same time.
Please close the other application eg 'aptitude' or 'synaptic' first.

---
Above is the error message I get when opening Update Manager. Still happens after a reboot.
Any ideas?

---

### Post by N8MAN1068 on 2006-05-22
doh.
edited my search string and found the answer...disregard.

---

### Post by N8MAN1068 on 2006-05-22
Ok. I take that back.
Issue came back again, and now I can't clear it.

Any other thoughts besides the lock files?

---

### Post by gingermark on 2006-05-22
Just a suggestion, but open up KSysGuard and have a look at what processes are running.

I once had a problem where Adept had crashed, and even after a reboot some of it's processes were hanging around. So have a look for apt, aptitude, adept or synaptic, and if they are there kill them and try adept-updater again.

As I say, just a suggestion,

---

### Post by N8MAN1068 on 2006-05-23
none of those are running.
Even a sudo ps x comes up clean for synaptic/adt etc al.

---

### Post by N8MAN1068 on 2006-05-25
/var/lib/apt/lists

file called 'lock'. Deleted it. Working now.

---

