---
title: "Compiz dies after update"
date: 2010-08-17
forum: Desktop Environments
---

### Post by randywilharm on 2010-08-17
Can anyone tell me what to type in terminal to diagnose this?

I typed "compiz" into the terminal and attached the readout.

It looks scary!

---

### Post by earthpigg on 2010-08-17
hi,

try this:

> compiz --replace

---

### Post by randywilharm on 2010-08-19
Ijust tried that and here's what the terminal read:



johnwilharm6@c-98-229-72-151johnwilharm6:~$ compiz --replace
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager



It does nothing at this point......thanks for the suggestion anyway..

---

### Post by realzippy on 2010-08-19
..which graphics driver/card??

---

### Post by randywilharm on 2010-08-19
I use an NVIDIA GEforce GTS 250

I installed it about 2wks ago with no problem until a few days ago.

---

### Post by realzippy on 2010-08-19
..reinstall the nvidia driver.

---

### Post by randywilharm on 2010-08-19
It's looking like the only alternative up to now.
Thanks for the idea--- I'll try it...

---

### Post by randywilharm on 2010-08-19
I just finished uninstalling/installing the new nvidia driver 256.44

with no success......Thanks anyway for your help..

---

### Post by randywilharm on 2010-08-20
After reinstalling the NVIDIA driver I tried to enable desktop effects + the gui seemed to "freeze up" when in fact it was actually functioning.

Because of the perceived "freeze up" I prematurely tried to exit the program
instead of letting it do its job.


Lesson Learned: Just because a readout on a GUI app freezes, it does'nt mean its not working.

Everything works now because I know
the app is working even if the readout freezes.


Thanks to all!

---

