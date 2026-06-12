---
title: "xfce gnome applets use all cpu"
date: 2009-02-28
forum: Desktop Environments
---

### Post by muckblit on 2009-02-28
I upgraded two pc's to ubuntu intrepid.

I had a hard time switching to xfce without k or gnome breaking back in. I finally switched to xdm, and use ~/.xinitrc with an .xsession file which is a link to that:

/usr/bin/xfwm4 &
/usr/bin/startxfce4

Then I made the mistake of adding to the xfce panel the xfapplet for gnome applets, on one of my two upgraded pc's. That computer suddenly started having 100% cpu as shown by the nifty cpu-mem-swap icons. I ran top in a term and three xfce-applets were each taking 30% of cpu.

To be fair, the applets are probably taking 100% of cpu because they are running into trouble loading. I could not see them in the panel. When I k9'd each one, nothing visible changed. I cannot get rid of them except by kill -9 [pid] because I cannot see them on the panel, so cannot drag and drop them back into the Add list dialog box. What a pain to have to look in a term, ps, grep for "apple", kill -9 three pid's.

I looked for ~/.xfce or something obvious, but I don't see any persistence file or directory to edit out the gnome applets from the xfce panel.

How can I delete my xfce gnome xfapplets?

---

### Post by muckblit on 2009-02-28
Now the gnome desktop disease came back.

This time it did not put a gnome panel over xfce panels, but the desktop has those stinking file icons all over it and I did not ask for gnome desktop.

I think that when I installed the SSH manager screenlet, it ran a gnome app, and the whole gnome elephant raped me again like before.

Last time I had to ctl-alt-backspace until I killed the dm, and then in command line mode just delete a bunch of dot dirs in home dir that sounded like gnome and gtk stuff. I can't find any other way...here goes...

---

### Post by muckblit on 2009-02-28
To get rid of gnome this time, all I had to do was go into xfce menu, settings, settings manager, desktop, and set a check in the box for Allow XFCE to Manage the Desktop.

That was never enough before!

I still can't figure out how to get rid of xfce gnome xfapplets.

---

