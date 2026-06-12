---
title: "sudo GUI apps"
date: 2017-03-01
forum: Desktop Environments
---

### Post by alabamatoy2 on 2017-03-01
16.04.2 desktop.  totally new fresh install.  I open a terminal and enter "sudo nautilus" in order to have the GUI file mgr with elevated privileges.  It works, but in terminal I get:

```
(nautilus:2786): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (nautilus:2786): CRITICAL **: Another desktop manager in use; desktop window won't be created
Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
```

Is this normal?  The file manager (nautilus) indeed runs with root privs, bu what's all the warning and critical alert?  How do I eliminate this?  Am I doing this (file mgr with elevated privs) the wrong way?

---

### Post by Perfect Storm on 2017-03-01
You should really use **gksudo** instead **sudo** when using with gui.

---

### Post by TheFu on 2017-03-01
Or **sudo -H {insert-gui-program}**

The issue is that sudo alone doesn't change the HOME environment variable, so the other userid, root, is trying to write config file stuff to your normal userid's HOME.  There are many ways this can be bad, but usually the "badness" doesn't show up until later.  root owning files in your HOME is bad.

You'll want to fix the root file ownership.  Run ```
sudo chown -R $LOGNAME ~/
``` to fix it.  Notice how sudo doesn't use the -H option? That is on purpose, this time. Feel free to read up about other options for sudo in the manpages. It is a very powerful command, well beyond what 95% of normal users AND administrators understand.

The better solution is don't use root for GUI programs. There a multiple security issues running X/Windows programs as root, though on a home network the risks for non-internet programs is minimal.

IMHO.

---

### Post by alabamatoy2 on 2017-03-01
Installed gksu, run gksudo nautilus and I get
====
```
** (gksudo:11435): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gksudo:11435): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed
```
====

The sudo -H nautilus resulted in:
====
```
(nautilus:11671): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:11671): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
```
====

Again, the GUI app works, but I get the errors, and have to ctrl-c in Terminal once I exit the GUI app.  Is this normal?

---

### Post by alabamatoy2 on 2017-03-01
It turns out that ANY app I run from command line (example gnome-system-monitor) or that I select from the GUI "Ubuntu software" icon and add to the launcher behaves this same way.  The default apps that are in the launcher bar seem to work, but any app I add to the launcher, even WITHOUT sudo, behaves this same way.  I launch the app and nothing happens.  the launcher shows the little arrowhead next to the icon as though its running, but there is no GUI window for the app.  I have reinstalled the OS, and this problem persists.  Can anyone help me troubleshoot what's going on?

---

### Post by TheFu on 2017-03-01
They are just messages.  If the message is about some other component that you aren't using, I wouldn't worry.  When you launch these apps from the menu, those same messages are sent ... nowhere.

For example, I don't run much of a GUI and don't care about dbus stuff at all.
I'm not using "accessibility features" either, so those not working just doesn't matter.

Did you run that **chown** stuff?

---

### Post by yetimon_64 on 2017-03-01
> **TheFu said:**
> Or **sudo -H {insert-gui-program}**...
With gksu being deprecated I use this one mostly now. Apparently pkexec can also be used if gksu is not installed.

> **alabamatoy2 said:**
> It turns out that ANY app I run from command line (example gnome-system-monitor) or that I select from the GUI "Ubuntu software" icon and add to the launcher behaves this same way. ...  Can anyone help me troubleshoot what's going on?No trouble as such there really, just terminal notifications; see next quote ...

> **TheFu said:**
> They are just messages.  If the message is about some other component that you aren't using, I wouldn't worry.  When you launch these apps from the menu, those same messages are sent ... nowhere. ...
+1.

---

### Post by alabamatoy2 on 2017-03-01
> **yetimon_64 said:**
> With gksu being deprecated I use this one mostly now. Apparently pkexec can also be used if gksu is not installed.  No trouble as such there really, just terminal notifications; see next quote ...   +1.  But (whining) the apps wont WORK!  They do nothing.  As I posted above, "I launch the app and nothing happens. the launcher shows the little arrowhead next to the icon as though its running, but there is no GUI window for the app."  They dont execute, as far as I can tell.

---

### Post by ajgreeny on 2017-03-02
What applications are these that do not run; are they perhaps command-line apps which will never run that way?

Some real examples might help us to help you more.

And as TheFu asked, "Did you run that chown stuff?" as it is still possible having used **sudo nautilus** to open the file-manager, that some of the files and folders in your home are no longer owned by you as they should be but by root.  That can cause numerous problems, the greatest probably being an inability to login as your user.

---

### Post by alabamatoy2 on 2017-03-02
> **ajgreeny said:**
> What applications are these that do not run; are they perhaps command-line apps which will never run that way?
Anything I add to the launcher.  I can pick any preinstalled app from the ubuntu software listing, and run it, and I get the errors and no gui window.

Respectfully, I understand the command line fairly well.

---

### Post by TheFu on 2017-03-02
Please post an example ".desktop" file that is being used to launch.

---

### Post by vasa1 on 2017-03-02
> **alabamatoy2 said:**
> It turns out that ANY app I run from command line (example gnome-system-monitor) or that I select from the GUI "Ubuntu software" icon and add to the launcher behaves this same way.  The default apps that are in the launcher bar seem to work, but any app I add to the launcher, even WITHOUT sudo, behaves this same way.  I launch the app and nothing happens.  the launcher shows the little arrowhead next to the icon as though its running, but there is no GUI window for the app.  I have reinstalled the OS, and this problem persists.  Can anyone help me troubleshoot what's going on?

This question appears distinct from the original issue. It's better for all concerned if you start a new thread with a descriptive title for each disctinct issue you face.

---

### Post by TheFu on 2017-03-02
Did you run the chown command I provided in #3 above?  That would explain why new GUI apps cannot run as the normal userid. 
The apps are trying to create settings and aren't allowed because root owns the file/directory where the settings belong.  Make sense?

For why sudo doesn't work, I dunno at this point.

---

### Post by alabamatoy2 on 2017-03-02
> **TheFu said:**
> Did you run the chown command I provided in #3 above? 

Yes, it seems to have had no effect.

---

### Post by TheFu on 2017-03-02
Ok  - rather than reinstalling, try creating a new userid - without sudo rights - and setting up the programs in the menu you'd like there.
Example .desktop file?

---

### Post by alabamatoy2 on 2017-03-02
I reinstalled the OS yet again, had same problem.  I started looking at  the display configuration.  For some reason, by default, the  installation of 16.04.2 is creating TWO desktops, one is displayed, the  other is not.  The apps that I tried to run were actually running, but  the GUI for the app was appearing in the non-displayed desktop!  I didnt know it was  there, so I couldn't see the GUI.  I deleted the non-displayable  desktop (system settings, displays), and the GUIs now appear where they should.

I apologize  for wasting yalls time, but you have educated me on several points in  this thread.  Thanks for your time and attention.

---

### Post by ajgreeny on 2017-03-02
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to users searching the forum.

---

