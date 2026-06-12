---
title: "HELP Accidently deleted both menu bars."
date: 2009-09-30
forum: Desktop Environments
---

### Post by SpeedRacer on 2009-09-30
I think I uninstalled the gnome-panel package or something. The only way I could get here is by clicking the external drive shortcut on the desktop and opening a file in opera. How do I fix this without having to reformat as I have been through 4 formats already since I started using ubuntu and It really gets annoying... Please help me!

---

### Post by greyfox1 on 2009-09-30
I think the only way you can end up with no panels is to kill the gnome-panel process.  Gnome doesn't let you delete your last panel to avoid exactly the situation you are in.  Try this:

[LIST]
[*]Press ctrl+alt+F2
[*]Type gnome-system-monitor to bring up System Monitor
[*]Look for the process called gnome-panel.  If you can't find it, it isn't running.  Press ctrl+alt+F2 again and type gnome-panel to start the process again.
[/LIST]

---

### Post by SpeedRacer on 2009-09-30
I pressed ctrl+alt+f2 and it brought me to a command prompt where I had to login. I checked and it said gnome-panel is not installed so I used the install command and now it looks like I got my panels back except one more thing I got an error when I rebooted.

Error
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

Do you want to delete the applet from your configuration?

When I was trying to delete the evolution email app from the apps menu I tried to remove completely and one of the things that was listed was gnome panel and fast user switching applet or something like that. Can I just install that and it will work, and what's the command for that?

---

### Post by Vaphell on 2009-09-30
goto synaptic and find fast-user-switch-applet
or from terminal: sudo apt-get install fast-user-switch-applet

---

### Post by SpeedRacer on 2009-09-30
Awesome! installed and rebooted and now the little shutdown menu is in the corner again (had to use sudo reboot earlier). The best thing is the panels look just as I had them before they went away so I don't have to reconfigure them.

---

### Post by greyfox1 on 2009-10-01
Err, I meant alt+F2, not ctrl+alt+F2.  My mistake, sorry-- but it looks like you have resolved it anyway.  Cheers.

---

### Post by locombian on 2009-10-02
hellooo

i deleted my lower panel to install the dock AWN. now i want to get rid of the dock and get the panel back?

any ideas??????????/

---

### Post by hariks0 on 2009-10-02
> **locombian said:**
> hellooo

i deleted my lower panel to install the dock AWN. now i want to get rid of the dock and get the panel back?

any ideas??????????/

Right click on the dock and select Quit.Just click on the top panel-->New Panel. A new panel will be added at the bottom. You can use Ubuntu Tweak to completely lock down the panels.

Using compiz ? And comes from windoze ?

Read this : [http://ubuntuforums.org/showthread.php?t=891922&page=2](http://ubuntuforums.org/showthread.php?t=891922&page=2)

---

### Post by FiReSTaRT on 2009-10-31
I also got the dreaded > The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

Do you want to delete the applet from your configuration?
I ended up deleting it and now I can't get it back. No help from apt/aptitude and can't find it in Synaptic (running on Karmic).. Any tips to get it back?

---

### Post by sensory on 2009-11-08
> **FiReSTaRT said:**
> I also got the dreaded 
I ended up deleting it and now I can't get it back. No help from apt/aptitude and can't find it in Synaptic (running on Karmic).. Any tips to get it back?
Same here. Fast-user-switch-applet is not available in Synaptic. Using apt I get:

```
Package fast-user-switch-applet is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gdm
```Any help? This is a very frustrating problem.

edit: After re-installing gnome-panel and gnome-panel-data the "Indicator Applet Session" showed up, which seems to be FUSA in 9.10. It could have also been something else I'd done before, but when looking through panels to add I was looking for FUSA, not "Indicator Applet Session". :P

---

