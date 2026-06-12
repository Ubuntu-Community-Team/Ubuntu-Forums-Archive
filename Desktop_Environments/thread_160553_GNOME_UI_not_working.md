---
title: "GNOME UI not working"
date: 2006-04-15
forum: Desktop Environments
---

### Post by SweetwaterBurns on 2006-04-15
All right, GNOME doesn't seem to be working anymore. I no longer have, not sure what to call it, but the title bar at the top of each application with close,minimize, etc. The menu bar and task bar still come up, but no applications show in the taskbar when opened. Anything I open is not in a movable window.

The only changes I made to the system before it all went to hell was installing amarok and setting it up. After closing it, all Title bars disappeared.

Not sure exactly whats going on, any help would be appreciated, as the system is practicaly unusable.

If you can think of any questions that might help diagnose it, please ask. I'm honestly not sure where to start after going through the various config files I could think of and everything seeming ok.

---

### Post by oscar on 2006-04-15
Have you tried restarting your computer? Also I have had something like this when the window manager failed to load in dapper. What happens when you try changing your theme's window border?

---

### Post by bscbrit on 2006-04-15
Did you install amarok using synaptic, or apt, or did you compile from source?  I'm trying to work out what has been corrupted so that we can try and fix it.

For the time being, you can still close / minimize or whatever by right clicking on the appropriate icon in the lower panel - across the bottom of the screen.

---

### Post by SweetwaterBurns on 2006-04-15
I did restart the computer, everything seemed to start up normally, but when I start anything, there is no border at all.

Changing theme or window border settings did absolutely nothing.

Only other change I noticed, Running System => Preferences => Windows
I get the following:

"Cannot start the preferences application for your window manager
Window manager "unknown" has not registered a configuration tool"

Everything else under preferences loads without error.


I installed amarok through synaptic
Version 2:1.3.7-0ubuntu4-~breezy1 along with the amarok gstreamer package.

Can't do anything with the bottom panel as you suggested, because it doesn't register any running application(stays blank).

---

### Post by bscbrit on 2006-04-15
I've not got much to suggest - I cannot imagine how using synaptic can have borked your GDM.  I can only suggest that you re-install GDM and all of its dependencies to try to recover the situation.  It sounds as if files or directories have had their permissions changed or have been deleted completely - and there are no known bugs in synaptic that would cause that!

---

### Post by SweetwaterBurns on 2006-04-15
Yeah, I thought it was really odd, as I've been using Ubuntu for a long time and never had anything like this happen unless I was odviously at fault.

Guess I have an excuse to try out dapper now.

See if I can figure out what happened and If I fix it (or at least find out what broke), I'll post it here.

---

### Post by bscbrit on 2006-04-15
Good luck!

---

### Post by r3m0t on 2006-04-15
Try typing

[FONT="Courier New"]gnome-window-decorator&[/FONT]

in the terminal

---

### Post by Ramses de Norre on 2006-04-15
Do you get any errors when executing metacity in terminal (or any other window manager you use).
I'd also try the command given in the previous post without the '&' so you can see error output.

---

### Post by SomeoneWhoIsntMe on 2006-04-15
Yeah, something's wrong with your window manager, not GNOME itsself.

---

### Post by SweetwaterBurns on 2006-04-16
Allright, I've been able to reproduce the error.

After running metacity in a terminal everything goes back to normal.

If I go to Amarok, right click on a song in the playlist, and select "Edit Track Information," Metacity exits with this error:

Bug in window manager: Unexpected X error: BadAlloc (insufficient resources for operation) serial 20388 error_code 11 request_code 53 minor_code 0)
Aborted

Fun stuff, but at least I seem to have everything working now.

---

