---
title: "Missing suspend kde menu option"
date: 2014-01-15
forum: Desktop Environments
---

### Post by petko-ivanov on 2014-01-15
Just had it, updated and it disappeared.
I am using latest kde , fully updated.
$ uname -a
Linux desktop 3.13.0-3-generic #18-Ubuntu SMP Tue Jan 14 10:36:18 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


My Bios settings is S3.
I added my user to sudoers so I can invoke "sudo pm-suspend" without a password prompt. I i can invoke it from command line and it suspends without a password prompt and resumes fine.
Any idea why the menu items are not there?

P.S. I also have this BUT still does not work :
cat /etc/polkit-1/localauthority/90-mandatory.d/enable-suspend.pkla
[Enable suspend]
Identity=unix-user:*
Action=org.freedesktop.upower.suspend
ResultActive=yes

P.P.S. I get this :
dbus-send --session --print-reply --dest="org.freedesktop.PowerManagement" --type=method_call --reply-timeout=6000 /org/freedesktop/PowerManagement org.freedesktop.PowerManagement.CanSuspend
method return sender=:1.4 -> dest=:1.85 reply_serial=2
   boolean false
Not sure what that means and why..

---

### Post by QIII on 2014-01-15
Looking at your kernel version ...

Is this Trusty Tahr?

---

### Post by petko-ivanov on 2014-01-16
Kubuntu 13.10
KdeLibs 4.11.3
Qt Version 4.8.4
Kernel 3.13.0-3-generic
OS Type:64 bit

---

### Post by petko-ivanov on 2014-01-16
Any one ? :(

---

### Post by QIII on 2014-01-16
I never noticed before, but I don't have it in either Saucy or Trusty.  Then again I don't bother with suspend on those two desktop machines.

---

### Post by petko-ivanov on 2014-01-17
Is there any one with some Desktop expertise around here who can explain why KDE thinks I am not allowed to suspend?
That's how i interprete this :
dbus-send --session --print-reply --dest="org.freedesktop.PowerManagement" --type=method_call --reply-timeout=6000 /org/freedesktop/PowerManagement org.freedesktop.PowerManagement.CanSuspend
....
boolean false

---

### Post by QIII on 2014-01-17
Have you tried changing your power management settings?

---

### Post by petko-ivanov on 2014-01-17
i dont see anything relevant i can change..

---

### Post by FuturePilot on 2014-02-02
I just installed some updates and now my hibernate and suspend options are missing from the menu. Kubuntu 13.10 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014

---

### Post by FuturePilot on 2014-02-02
And I rebooted and they're back.... :-s:confused:

---

