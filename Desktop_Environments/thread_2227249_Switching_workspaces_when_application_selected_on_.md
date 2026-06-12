---
title: "Switching workspaces when application selected on the launcher?"
date: 2014-05-31
forum: Desktop Environments
---

### Post by beyere on 2014-05-31
In most DEs with a dock I have used, if you select a running application by clicking its icon in the dock or by alt-tab'ing to it, the active workspace changes so the selected application is immediately in front of you.

In my current unity setup, that doesn't happen.  The icon you select is highlighted but nothing else happens.  You have to manually move to the workspace for the application you want to use.  Is this a feature
or a bug?  Is there a way I can reconfigure my unity desktop so this works the way I want it to?

Thanks in advance.
EB

---

### Post by mc4man on 2014-05-31
Works fine here, if an app is open on another ws clicking icon moves to that ws & focus's app window.
ex.
I'm on ws 1 & nautilus is open on ws 4. Clicking icon switches to ws 4 & focus's nautilus window.

---

### Post by beyere on 2014-05-31
Great!  All I need to do now is to figure out why my system is different from yours and then make it not different from yours.

How best to do that?

---

### Post by deadflowr on 2014-05-31
> **beyere said:**
> Great!  All I need to do now is to figure out why my system is different from yours and then make it not different from yours.

How best to do that?

Try resetting the desktop session to the defaults.
Since that is a default behavior.

Which version of Ubuntu?

---

### Post by beyere on 2014-05-31
14.04.

Resetting to default behavior gets rid of more than one workspace, mooshing all my windows onto one workspace.  

When I re-enable workspaces, I have the same problem again.
EB

---

### Post by buzzingrobot on 2014-06-01
> **beyere said:**
> 

Resetting to default behavior gets rid of more than one workspace, mooshing all my windows onto one workspace.  

When I re-enable workspaces, I have the same problem again.
EB

Sounds like you reverted to default in Systems Settings.  By default, workspaces are not enabled, so reverting to default would kill all workspaces but one and move open windows to it.

Try resetting Compiz and Unity.  You'll need to install one tool and use the terminal:
```

sudo apt-get install dconf-tools
dconf reset -f /org/compiz/
setsid unity
unity --reset-icons

```

---

### Post by beyere on 2014-06-01
I followed those steps.  My icons in the launcher reverted to their defaults but the behavior I described in the original post persists.  I will poke around compiz config settings and see
if that changes anything.
EB

---

### Post by buzzingrobot on 2014-06-01
I don't install or use CCSM because something invariably breaks.  Unity is implemented as a Compiz plugin.

---

### Post by mc4man on 2014-06-01
> **beyere said:**
> I followed those steps.  My icons in the launcher reverted to their defaults but the behavior I described in the original post persists.  I will poke around compiz config settings and see
if that changes anything.
EB

Why don't you log into a guest session, enable workspaces & see if it works properly there.

---

