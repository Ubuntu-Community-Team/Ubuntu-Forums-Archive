---
title: "Disable Nautilus on Startup in KDE"
date: 2011-11-19
forum: Desktop Environments
---

### Post by czarmurphy on 2011-11-19
Hi, I have been using Kubuntu (Ubuntu installed first) for a little while now, and recently when starting up a Nautilus window has been opening. I would like to use only Dolphin, not Nautilus. I haven't been able to disable it yet, and I'd like to know how to.

I can't remember what I did to cause this, but it may have had something to with my messing with the Dolphin -> Dolphin Preferences -> Startup -> Home Folder -> Location. Currently, it is "file:///" sans quotes (I think at one point it was blank), and I am unable to clear and set the value.

That may be what is causing it. Or it may be startup programs, although I haven't found anything for this.

While I'm at it, I may as well ask how to disable Nautilus completely while I'm using KDE, as I only want to use Dolphin.

Thank you very much for your help!

---

### Post by dniMretsaM on 2011-11-19
What do you see here:
System Settings -> Startup and Shutdown -> Autostart

If you see Nautilus, disable it (untick the check box). As for disabling Nautilus completely, just make sure Dolphin is sat as the default file manager:
System Settings -> Default Applications -> File Manager

---

### Post by czarmurphy on 2011-11-19
I checked both of those, and both were already set in the way you instructed.

Can you think of anything else?

EDIT: The only thing in Autostart is gtk2-default-theme.rc.sh

EDIT2: I have discovered that the Nautilus window opens (on login) when using the KDE Plasma Workspace, and not when logging on to Ubuntu.

---

### Post by czarmurphy on 2011-11-20
Anybody find anything?

---

### Post by DMKryl on 2011-11-20
Did you check on the start up services?, System settings > startup and shutdown > Service manager

---

### Post by inobe on 2011-11-20
that is just a few of the annoyances.

in my opinion, if it matters, i would decide what desktop you like best then run only that from a fresh install.

personally, i been running kubuntu for years, i haven't did the session thing for a few years, and will never do it again.

kubuntu is better experienced solo, even if you remove the ubuntu desktop or kde, it'll never be like it was.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by czarmurphy on 2011-11-20
Thanks for the advice. I'll get started on this soon.

---

### Post by steve* on 2012-01-17
Your symptoms exactly describe what I was experiencing. My solution was to replace the 'Restore previous session' with 'Start with an empty session' check box found in System Settings - Startup and Shutdown - Session Management. I then reverted back to the default setting after re-logging into KDE and the offending window remained gone thereafter.

---

### Post by zahtar on 2012-02-03
thnx steve!

It worked for me too :)

---

### Post by Adrian W on 2012-03-05
I had exactly the same problem with a Nautilus window opening on every restart. To get rid of it I went to System Settings -> Startup and Shutdown -> Session Management. In the "On Login" section there is a field "Applications to be excluded from sessions" and I added "nautilus" to this. After a restart the Nautilus window didn't return.

---

### Post by dmackenzie on 2012-05-28
You can actually just kill nautilus from the command line and restart. Notice even after killing it from the gui it is still running in the background.

#> ps -ef | grep nautilus
<nautilus pid>
#> kill -9 <nautilus pid>

---

### Post by zeron00 on 2012-08-23
I've had the same problem in Kubuntu! Solution: edit or remove the file  /etc/xdg/autostart/nautilus-autostart.desktop If you choose to leave it, then you can edit it with KWrite or Kate or some other editor. The line you want to change is the one saying  OnlyShowIn=GNOME Make sure there is nothing else but 'GNOME' after the '=' sign. After saving the file delete the backup copy.

---

### Post by Jakin on 2012-08-23
this is rather simple to fix without messing with any other settings.

system->startup and shutdown->session management "on login" exclude "nautilus".

---

