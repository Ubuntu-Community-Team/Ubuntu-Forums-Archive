---
title: "&quot;Cannot open display&quot; error with su"
date: 2009-12-14
forum: Desktop Environments
---

### Post by cybertoast on 2009-12-14
Something I found after searching for a while, and figured it would be useful to someone in future.

If you are trying to switch your current user from the terminal using su -, you may encounter errors like:
[LIST]
[*]"E233: cannot open display"
[*] "No protocol specified"
[*] "Cannot open display: (Gtk::InitError)"
[*] "Error: no display specified"
[/LIST]
and others, when you try to use any X application from the new user's session (like gvim, vimmate, firefox, etc.). The solution is simple. Instead of using su, use sux.

Explanation for why can be found [here]("http://www.softpanorama.org/Xwindows/Troubleshooting/can%27t_open_display.shtml"). The relevant section:
> With the default X authentication mechanism, an X client needs to have access to a valid X session cookie (which is, essentially, a shared secret between the X server and its clients).

When a user switches to a different user using the su command, X session cookies are not transferred and thus the user cannot start X applications under the user id to which he or she switched.

Solution to the authentication credentials problem: sux

Instead of su, use sux to switch user id. Like su, sux switches to a different user id. Unlike su, it ensures that the id being assumed is given access to the X session cookie so that X applications can be started. 

---

