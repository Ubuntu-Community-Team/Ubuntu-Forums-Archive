---
title: "Running BOINC in Compiz"
date: 2010-01-17
forum: Desktop Environments
---

### Post by jpalko on 2010-01-17
Anyone else running boinc on your desktop that has compiz running?

I was checking out the boinc manager after logging into my boinc account manager and noticed that it kept saying as status "Suspended - User is active" even when I wasn't. Is this something that Compiz causes? I adjusted the inactivity time and waited until that passed and nothing. When I put it the setting to "Run always" the calculations start okay.

Can it be that Compiz causes some continuous activity in the system that BOINC keeps seeing?

---

### Post by oldos2er on 2010-01-17
> **jpalko said:**
> Anyone else running boinc on your desktop that has compiz running?


Yes.

If you click 'Resume' for the suspended task, does it work?

---

### Post by jpalko on 2010-01-17
> **oldos2er said:**
> Yes.

If you click 'Resume' for the suspended task, does it work?

No. It's showing "Suspend" button on all projects. Oh yeah, x86_64 system in question. Guess I didn't say that earlier. :)

---

### Post by oldos2er on 2010-01-17
If the 'Suspend' button is not grayed out, that's normal. You can run ```
ps aux | grep boinc
``` to double-check that it's running.

---

### Post by jpalko on 2010-01-17
> **oldos2er said:**
> If the 'Suspend' button is not grayed out, that's normal. You can run ```
ps aux | grep boinc
``` to double-check that it's running.

The boinc process is running if those projects get listed at all. If it wasn't then boinc manager would complain that it cannot connect to boinc process.

---

### Post by oldos2er on 2010-01-17
Forgive my confusion. When you said "boinc account manager" I assumed you were referring to just the boinc manager.

---

