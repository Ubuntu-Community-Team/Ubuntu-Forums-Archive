---
title: "openbox session does not start, computer does not react"
date: 2014-01-18
forum: Desktop Environments
---

### Post by HenkHarmsen on 2014-01-18
I have installed openbox following [these]("http://dottech.org/129812/how-to-install-openbox-xubuntu-linux/") instructions. 

After logging out and logging into a Gnome/openbox session I just have a black screen with a big cross formed cursor on it [like what you see with xkill].
This is not the usual openbox screen [I have been using Crunchbang for years].

There is no way I can log out and log into a xcfe session again - I can move the cursor but mouse left or right does not produce any menu. 
Inserting a CD produces a Thunar window.


I would be very happy if somebody can tell me how I get log into my computer again...

---

### Post by HenkHarmsen on 2014-01-18
found a solution....:

put a CD rom into the computer; this opens a thunar window.
select "open terminal here".
in the terminal type: "gnome-session-quit", this logs out the session.
select "xubuntu session" and log in.
this brought everything back to normal.

---

