---
title: "Gaim crashing emerald. A strange bug..."
date: 2007-03-22
forum: Desktop Environments
---

### Post by kadane|R| on 2007-03-22
Hello to everyone reading this thread...

My problem is as follows:

After some time when I installed beryl/emerald on gnome (ubuntu 6.10) everything was working fine, no bugs whatsoever... 

But one day I've recalled that there is an option in System>Preferences> Sessions
witch is "automatically save changes to session".
I thought it would be nice to leave some apps open in different desktops instead of opening them all over again every time i logged in to gnome.

...and then I've opened a pandora box!

I had my gaim on all desktops before and now every time i right click on gaim's title bar my window decoration crashes  (emerald??) all of beryl effects are working fine..

So I've disabled this option "on all desktops" when using metacity and lunched beryl again and it worked. all was fine.
But the big annoyance is that every time  I log in this option, "on all desktops", returns.

I thought that there is something wrong in some config file so I deleted
~/.gnome2/session and ~/.beryl/setting
by so making new ones. But it didn't help.

SO.... what the HELL is wrong??

_The problem:_

1. My window borders disappear when I right click on the title bar. This happens only when gaim is on all the desktops.
2. Switching this option off solves the problem but every time I log in and beryl is launched at session's start-up this option returns.
3.  To be very clear this happens only when beryl is launched automatically at start-up. If I log in without beryl then everything is saved as it should be.
Launching beryl manually and this option returns. Going back to metacity switching it off. Again going to beryl and everything is fine until the next log-in.

I'm using Intel P4 2.4 ghz, Geforce FX5500
ubuntu 6.10 Linux 2.6.17-10-generic
nvidia driver 1.0-9631
beryl and emerald are 0.2.0

---

### Post by kadane|R| on 2007-03-22
ok... I have the feeling  that either no one knows or didn't understand my problem...

maybe someone knows where does gnome saves it's session data?

one more thing i'm getting this error when i'm trying to open the workspace switcher preferences

```
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_9/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_9/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_9/prefs/num_rows' stores a non-schema value

```

---

### Post by deadowl on 2007-03-22
Personally, I gave up on Gaim.

For one, GTK's combo boxes are the most annoying thing. Try maximizing Gaim Vertically and clicking the status box on the bottom and you'll see what I mean. Whoever was working on GTK decided that having the default option under the mouse was more important than visibility in terms of usability. Just one of those things that pushed a newbie to use KDE instead.

On top of just using GTK, every time I try to use a plugin in Gaim it spits a segmentation fault out at me at some point or another.

I believe AOL has a Linux version of AIM, but I believe that Kopete might be a better option for matching in a level of functionality. I generally just use IM programs to connect to MSN and AIM, but someone needs to add MySpaceIM (eww) to that list soon.

I think Gaim holds its own as an IM program in terms of functionality (unlike many GTK-based apps), but you have to keep your alternatives in mind (namely Kopete).

If you decide to use Kopete, keep in mind that you have chat window styles that you can download, though I don't think you could quite match Gaim in terms of what the contact list will look like (they're two different programs after all).

---

