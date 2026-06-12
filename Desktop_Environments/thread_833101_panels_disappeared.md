---
title: "panels disappeared"
date: 2008-06-18
forum: Desktop Environments
---

### Post by joec3 on 2008-06-18
Yesterday I installed Xubuntu 8.04. Installed all the updates. Everything worked fine. Today everything booted up and launched ok.  All of a sudden the  xfce panels disappeared. Can't access the panel manager in the settings manager. Xfce still manages the desktop, programs still launch, still get a menu if I right click, can switch workspaces with mousewheel only. rebooting doesn't help. reinstalled xfce panel applet with synaptic but that didn't help.

How do I get this working again?

---

### Post by sisco311 on 2008-06-18
Try to run the panel from a terminal:
```
xfce4-panel
```and post the error message.

To open a terminal
press Alt+F2:
```
xfce4-terminal
```

---

### Post by joec3 on 2008-06-18
> **sisco311 said:**
> Try to run the panel from a terminal:
```
xfce4-panel
```and post the error message.

To open a terminal
press Alt+F2:
```
xfce4-terminal
```

That brought the panels back. No error message. But if I close the terminal the panels go away again.

---

### Post by sisco311 on 2008-06-18
Close all applications, press Alt+F2 and start the panel:
```
xfce4-panel
```

Log out with the *Save session for future logins* option (select it from the shutdown menu).

---

### Post by lordrick112 on 2008-06-24
Hi.

I'm having the same problem here. The panels just keep on dissapearing. 
When I try to shutdown and reboot, it asks me if I want to "Exit xfce panel?", not shutdown or restart.

Any Ideas on this one?

---

### Post by Speed8 on 2009-11-08
ty very much sisco, this worked for me in 9.10. had the same problem

---

### Post by munkeh on 2009-12-18
Hi I had the same problem with the two panels all of a sudden being panelnapped. Followed sisco311's instructions of 

Closing any windows.
Alt and F2
Typing- xfce4-panel

Which as said, rescued the panel from the naughty panelnapper.
Then went to
Applications > Settings > Sessions and Startup.
Made sure the "Automatically Save Sessions on Logout" was ticked.


All well and good so then ran into the same problem as Lordrick112 that clicking to logout would only ask do I want to, "Exit xfce panel"

So what worked was Shutting Down via Applications> Logout. Which strangely was not asking about the xfce4 and just gave the normal options.

So thanks sisco311 and I hope this helps anyone else.

---

