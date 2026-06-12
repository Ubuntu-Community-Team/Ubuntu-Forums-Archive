---
title: "Kde doesn't load the beryl window manager"
date: 2007-02-18
forum: Desktop Environments
---

### Post by yurukov on 2007-02-18
Hi, I got the kubuntu and installed beryl. I followed the guide in the beryl wiki, but then KDE starts it would not load the beryl window manager. What I did was to create a /usr/bin/startberyl.sh:
```
#!/bin/sh
 export KDEWM="/usr/bin/beryl-manager"
 exec startkde

```
and make a session that starts it. Did not work.

Then I changed directly the kde startup from:
```
test -n "$KDEWM" && KDEWM="--windowmanager $KDEWM"
kwrapper ksmserver $KDEWM
```
to:
```

//test -n "$KDEWM" && KDEWM="--windowmanager $KDEWM"
kwrapper ksmserver "/usr/bin/beryl-manager"
```
Did not work either.

Instead what worked was that I added beryl to the Autostart folder. The annoying thing is that it takes several seconds after KDE is loaded for beryl to take effect. How can I fix that?

---

### Post by tendays on 2007-07-13
I've been having a similar problem.

What do you mean by "does not work" ? You should always post the standard "what I did; what I expected; what I had instead" format otherwise people don't respond...

Anyway:

Check the permissions on your startberyl.sh script (chmod 0755) ?

I have the additional difficulty that I have to run beryl and emerald directly, rather than beryl-manager, because I need the --force-aiglx option, which is not provided by beryl-manager.

So what I did is to create a "/usr/bin/beryl-wm" script with the following:

```
#!/bin/sh
# start beryl and emerald - by tendays

emerald &

beryl --force-aiglx
```

(no "&" after invoking beryl because (I think) when the script exits, ksmserver exits as well, and takes everbody down with it). Maybe they should be swapped, actually, doing "beryl & ; emerald" ...

Then I copied startkde into startkde-beryl, changing, as you did, the ksmserver invocation into

```
kwrapper ksmserver --windowmanager /usr/bin/beryl-wm
```

I then created a .desktop file for that in /usr/share/xsessions .

It almost works, except that the alt-F1 and alt-F2 shortcuts no longer work :-( I can use the mouse for the former and never use the latter so it's no big deal for me.

EDIT: I solved the alt-f1 and alt-f2 by having them run dcop kicker kicker showKMenu and dcop kdesktop KDesktopIface popupExecuteCommand, respectively

HTH

---

