---
title: "Startup Applications with a delay."
date: 2009-06-01
forum: General Help
---

### Post by ontwowheels on 2009-06-01
9.04 here:

Is there a way in Startup Applicaions to start an application with a dealy?  Maybe by modifying a script?  I don't see the option in the Startup Applicaions applet.

Reason I ask is, when I try to set Cario Clock to auto start it does start on login but the clock is messed up.  When I start the clock manually it starts fine.  I assume it's a timing issue, possibily with it starting before or after conky.

THANKS IN ADVANCE.

---

### Post by Brandon Williams on 2009-06-01
If you wrap the command execution in a script in your ~/bin/ directory (create the directory if it doesn't exist), then you can make it do whatever you want prior to starting the app.

```
#!/bin/sh
sleep 10
exec realcommand
```

Make sure you remember to make it executable. To test, run it from the Alt+F2 dialog, not from the command line, to make sure that the environment available to a startup app will be adequate for the script to work correctly.

Alternatively, if it's just an ordering issue and not a timing issue, you can try renaming the .desktop files in your .config/autostart/ directory so that the one that must run second comes after the one that must run first when sorted (01_runsfirst.desktop, 02_runssecond.desktop, etc.). I think that the .desktop files will be handled in alphabetical (really ascii) order.

---

### Post by ontwowheels on 2009-06-01
> **Brandon Williams said:**
> If you wrap the command execution in a script in your ~/bin/ directory (create the directory if it doesn't exist), then you can make it do whatever you want prior to starting the app.

```
#!/bin/sh
sleep 10
exec realcommand
```

Make sure you remember to make it executable. To test, run it from the Alt+F2 dialog, not from the command line, to make sure that the environment available to a startup app will be adequate for the script to work correctly.

Alternatively, if it's just an ordering issue and not a timing issue, you can try renaming the .desktop files in your .config/autostart/ directory so that the one that must run second comes after the one that must run first when sorted (01_runsfirst.desktop, 02_runssecond.desktop, etc.). I think that the .desktop files will be handled in alphabetical (really ascii) order.

Thanks, I will give these a try this evening.  What you say makes sense about the alphabetical ascii.  My thought is conky window starting at the same time cario clock is messing up the clock.

I'll report back for all those sitting on the edge of their seat.  :D

---

### Post by binary10 on 2009-06-01
alternatively avoid the script and just mod your startup line, this was for the hp-systray.

```

sh -c "sleep 60; exec hp-systray" &

```

---

### Post by ontwowheels on 2009-06-01
> **binary10 said:**
> alternatively avoid the script and just mod your startup line, this was for the hp-systray.

```

sh -c "sleep 60; exec hp-systray" &

```


Interesting....that is probably the easiest, I'll try that first.

THANKS

---

### Post by ontwowheels on 2009-06-01
> **binary10 said:**
> alternatively avoid the script and just mod your startup line, this was for the hp-systray.

```

sh -c "sleep 60; exec hp-systray" &

```

This worked perfectly....THANKS ALL

---

