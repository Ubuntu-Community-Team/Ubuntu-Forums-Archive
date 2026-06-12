---
title: "Can't Configure GDM"
date: 2007-02-24
forum: Desktop Environments
---

### Post by 16777216 on 2007-02-24
I can't re/configure GDM in any way.
I reinstalled it and that worked until I rebooted.
This is very annoying.

---

### Post by Stemp on 2007-02-24
What do you mean by re/configure GDM ?

---

### Post by 16777216 on 2007-02-25
It will not let me set it up or change settings
A reinstall fixes it untill I reboot then it resets back to default debian settings. ( with a light blue-gray background and the theame with big flower. )

---

### Post by Stemp on 2007-02-25
It resets back to the Debian default ? This is not even the Ubuntu default theme ? 
So you're changing your theme in Menu System, Administration, Connection etc.... and it's only working during the current session ?

---

### Post by 16777216 on 2007-02-25
> So you're changing your theme in Menu System, Administration, Connection etc.... and it's only working during the current session ?

Can't even do that unless I reinstall GDM then if I reboot it resets.
And I just found out I can't save session changes either.
My wife's account can save session changes but not mine.
I am thinking my user privileges have been messed up some how.
This is very annoying.

---

### Post by Stemp on 2007-02-25
Try to launch the gdm setup from a terminal : 

```
gksu gdmsetup
```

---

### Post by 16777216 on 2007-02-25
```
gksu gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.
```

is what I get.

---

### Post by Stemp on 2007-02-25
Not nice
Well in fact you're not the only one : [http://ubuntuforums.org/showthread.php?t=190821](http://ubuntuforums.org/showthread.php?t=190821)
See post #5 and #10 :(

---

### Post by 16777216 on 2007-02-25
YAY! oh well, thank you for the help.

---

### Post by BMWolfgang on 2007-03-04
you might want to try this:

[http://www.ubuntuforums.org/showthread.php?p=2248101#post2248101](http://www.ubuntuforums.org/showthread.php?p=2248101#post2248101)

---

### Post by x1a4 on 2007-03-04
Hi,

You're running Kubuntu, so your default display manager is **K**DM.  Use the KDE Control Centre (*kcontrol*) to change KDM's theme.

---

### Post by 16777216 on 2007-03-05
Here is a post I made elsewhere that might shed some light.

> With GDM it starts fine but I have to log in then it hangs so I kill X ( Ctrl+Alt+Bksp ) then it works fine with the exception of I am unable to configure GDM unless I reinstall it then it still resets on reboot only to need reinstall all over again.

KDM, well that's *better *but I have to kill X ( Ctrl+Alt+Bksp ) as soon as I see my mouse cursor for it to start properly else it simply goes to a blank screen with a tty text cursor blinking in the top left corner.

As far as I can tell it is a X related server misconfiguration

I am going to try the solution above.
Thanks all for the help.

---

