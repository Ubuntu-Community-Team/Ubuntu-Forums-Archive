---
title: "Simulating a mouse click to raise skype from gnome-panel tray"
date: 2010-11-04
forum: Desktop Environments
---

### Post by sp3ctum on 2010-11-04
Here's a summary of my problem: When using Skype, it's possible to
close the gui of the application only. When doing this, the Skype
process itself doesn't close; it hides in gnome-panel's
notification-area.

Now, when opening the Skype application again (e.g. by clicking on a
Skype launcher), Skype starts a whole new process. This is shown to
the user as a new Skype tray icon being generated, as well as a new
gui window being created.


What I'd like to do is as follows:

I'd like to replace the Skype launcher with a script that would
* recognize if there is a Skype process running if yes, bring up that
* instance of Skype if not, start Skype normally

Now, I've read some of the source code of gnome-panel to try and see
how it's done. From what I've gathered, a button_press_event is bound
to some function that probably (am unsure of this) sends a signal of
some kind to Skype.

Very similar to this thread, except for Skype and without wmctrl (does
not work with Skype):  
**HOWTO: Make a launcher restore an open window (dock-like)**
[http://ubuntuforums.org/showthread.php?t=375529](http://ubuntuforums.org/showthread.php?t=375529)

I'm hoping someone has some ideas about this since mine are running
out.

---

### Post by SteveDee on 2010-11-04
Take a look at the Linux command "pgrep".

I've used this in Gambas programs to see if the application I'm about to launch is already running, example:-
```

PUBLIC FUNCTION AlreadyRunning() AS Boolean
'Is program already running?
'----------------------------------------------------------------------  
DIM strReply AS String

  EXEC ["pgrep", "-f", "-l", "my-tv.gambas"] WAIT TO strReply
  
  IF Split(Trim$(strReply), gb.newLine).Count > 1 THEN
    RETURN TRUE
  ENDIF  
  
END

```

Also take a look at command "wmctrl" (which is not installed by default, so go to Synaptic).

Using wmctrl like this:-
```

wmctrl -a skype

```
...will restore the Skype window (even if on another desktop), assuming Skype is already running.

---

### Post by kerry_s on 2010-11-04
never mind.

---

### Post by sp3ctum on 2010-11-05
Thanks for replying :)

pgrep is definitely the way to go when finding out if the program is running, which is great.

However, wmctrl has a limitation. It can only restore a window that already exists.
When Skype's window is destroyed (clicking the close button on the window),
wmctrl cannot find Skype's window and thus is unable to bring it back.

I'm looking for a 'back-end' way to send a GTK signal to Skype's process
or something like this approach. I'm unsure if that's possible, and
could use a pointer on what to read to learn how to do it. :)

---

### Post by SteveDee on 2010-11-05
OK, I'm not exactly a script kiddie, but using the two commands "pgrep" and "wmctrl" I've put together this simple script:-

```


#!/bin/bash
# Sript: SilverSurfer.sh by SteveDee
# Displays Firefox if already running,
# otherwise is loads it.
# ------------------------------------

if [ -z $(pgrep -fl "firefox") ]
then
	firefox
else
	wmctrl -a firefox
fi
exit 0

```

Running this from a panel launcher helps the user to avoid creating more than one instance of Firefox (...and losing open tabs).

Hopefully you can adapt this for Skype.

---

### Post by SteveDee on 2010-11-05
> **sp3ctum said:**
> Thanks for replying :)

pgrep is definitely the way to go when finding out if the program is running, which is great....


Sorry, we were posting at the same time, so I've only just seen this...

---

