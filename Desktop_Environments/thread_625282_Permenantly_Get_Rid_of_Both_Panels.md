---
title: "Permenantly Get Rid of *Both* Panels?"
date: 2007-11-27
forum: Desktop Environments
---

### Post by bakaeigo on 2007-11-27
Is there anyway to permanently remove the "required" panel without workarounds such as autohide? I tried going into Preferences-->Sessions and removing the process (And changing its status to "normal") But it reappears after each reboot.

Thanks!

---

### Post by kyphi on 2007-11-27
When you say that you want to permanently remove the "required" panel, how will you then access your programmes?  To delete the panel will also take away all your icons on the panel.

You could just give it transparency.  That way your application icons will still be visible.

If that is what you want to do, just say so and I will gladly tell you how to do this.

---

### Post by Aathos on 2007-12-01
I am interested in this too.  I use the Avant Window Navigator dock for pretty much anything that a panel would be used for.  The only reason I would want a panel is that the notification area doesn't look good with the 3D style.   I have just hid the panel in the bottom right corner for now.  Perhaps a script could be written to kill the process on boot up?

---

### Post by XVII on 2007-12-01
Openbox is really minimalistic, and no panels (unless you want them).

---

### Post by urukrama on 2007-12-02
> **bakaeigo said:**
> I tried going into Preferences-->Sessions and removing the process (And changing its status to "normal") But it reappears after each reboot.

That is because gnome-panel is set to automatically restart when it for some reason stops, just like Nautilus. This is to prevent users from not being able to access anything when the panel crashes.

It is fairly easy to undo this, though. I don't have gnome installed on this computer, so what follows is based on my gnome-memories. Please forgive me if I make any mistakes.

Go to Preferences > Sessions as you did before. Before you try to remove the panel, look for something called 'Style'. I forget where exactly this is -- prehaps there is a button for it, otherwise try right clicking on the entry and see what comes up.

There are different 'Styles' available. From [here]("http://www.gnome.org/learn/users-guide/latest/prefs-sessions.html"):

> [LIST]**Normal** 
Starts automatically when you start a GNOME session.[/LIST]
[LIST]
**Restart** 

Restarts automatically whenever you close or terminate the application. Choose this style for an application if the application must run continuously during your session.[/LIST]

[LIST]**Trash**
Does not start when you start a GNOME session.
[/LIST]

[LIST]
**Settings**
Starts automatically when you start a session. Applications with this style usually have a low startup order, and store your configuration settings for GNOME and session-managed applications.
[/LIST] 

The panel should be on 'restart'. Change that to 'Normal' and you should be able to remove the entry without it coming back.

If you ever want to restart the panel, the command "gnome-panel" should bring the panel(s) up again.

I hope this helps.

---

### Post by Aathos on 2007-12-02
That worked for me.  However, alt+F2 doesn't bring up the Run Application dialog when there are no panels running.  That could be a problem when compiz crashes, because that is what I use to restart it.  I have been considering mapping a hotkey to to that command, but I am willing to live with that little hidden panel.

---

### Post by urukrama on 2007-12-02
Yes, I feared that, as it depends on gnome-panel. 

You can use a gmrun to do the same, though. Install it (it is in the repositories), and then bind the key Alt+F2 to it.

---

