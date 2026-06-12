---
title: "Remote Access / User Impersonation"
date: 2009-03-06
forum: Desktop Environments
---

### Post by darkpixel on 2009-03-06
I ran into several questions when my server's monitor died about a week ago.

When the monitor died, I initially started using VNC to view the server desktop.  My plan was to use this as a stop-gap until my new monitor arrives.

Earlier today, VNC stopped working.  I was disconnected in the middle of a session.  Attempts to reconnect fail, and I see nothing running on port 5900.

I ssh'd into the box and I see vino-server running.  I can even 'ssh -X' and run vino-preferences to disable/enable vino.  For some reason, vino-server is not grabbing port 5900.  I'm sure a reboot will fix whatever is wrong--but I have stuff open that needs to be saved.

This led me on a search for remote X/GDM sessions--but it's a bit out of my league.

Is it possible to connect into an already running X session?

Another solution I looked into was simply starting up a VNC server manually by SSHing into the server--but I messages saying "cannot open display".  Is it possible from the command-line to impersonate a user that is already signed in?  In other words, be able to launch vncserver from the command line and have it run under the already-logged-in user?

Lastly, I wondered if it were possible to take the display (say of gedit) and redirect it back over my SSH session so I could interact with it from my laptop.  (I know I can start gedit if I run 'ssh -X', but can you connect to an existing app?)

---

