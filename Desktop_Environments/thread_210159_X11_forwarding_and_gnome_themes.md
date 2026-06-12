---
title: "X11 forwarding and gnome themes"
date: 2006-07-06
forum: Desktop Environments
---

### Post by shartl on 2006-07-06
hello,

I've some strange problem with ssh X11 forwarding:

when I connect to a remote machine running ubuntu 6.06 from a non-ubuntu-machine (centos, windows with xming) the surface of the started gnome-programs (gedit, ...) doesn't look as it should do.

the surface of the remote-started programs looks like plain gtk2 - small (wrong) fonts, no nice-looking buttons, wrong icons, ...

when connecting from the windows client the correct theme can be enforced by starting gnome-theme-manager and just switching the used theme 2 times (although xming dies short after). trying the same from centos doesn't work because when starting gnome-theme-manger a error is shown ("unable to start the settings manager 'gnome-settings-daemon')

has anybody a solution for this problem?

regards
simon

---

### Post by aguy on 2006-11-04
I too am having this problem.

I have just upgraded my fileserver from breezy to edgy.  In breezy I could login via SSH on my windows box and run gnome-session to get a GUI with Xming.  Looked just like I was running locally.  However in Edgy it logs in but says something about not being able to start gnome-settings dameon and uses a plain theme (NOT the same local theme which it is set to use).

Does anybody know how to remedy this?

Thanks

---

### Post by mkropat on 2007-02-25
I've had similar problems when running a gnome-session under Xephyr in Edgy. Running /etc/X11/Xsession instead of gnome-session seems to work for me. Who knows the intended way to spawn a new session--the GDM startup procedures are spaghetti.

Also in case any one else has the same problem, I was also getting this error on gnome-session startup:

"There was an error starting the GNOME Settings Daemon."

"Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

---

### Post by akadruid on 2007-10-25
> **shartl said:**
> 
when I connect to a remote machine running ubuntu 6.06 from a non-ubuntu-machine (centos, windows with xming) the surface of the started gnome-programs (gedit, ...) doesn't look as it should do.

the surface of the remote-started programs looks like plain gtk2 - small (wrong) fonts, no nice-looking buttons, wrong icons, ...

I've seen this. I think its the default failure mode when it can't read the theme info.  It's looking on the local machine for the theme.

I believe you need to have the exact same theme on the local machine with the same name in the same relative place for it to work i.e. your non-ubuntu machine would need 'human' with all the componants at the same location if your ubuntu machine is using the default theme.  I think you can save the theme on the ubuntu machine using the theme-manager and copy that to the centos machine and import it.

Failing that, if you can't run the ubuntu theme manager, maybe try running the centos theme manager, changing the them and changing back?  Or else try downloading a new theme from the web onto both machines and switching to that on both machines?

---

