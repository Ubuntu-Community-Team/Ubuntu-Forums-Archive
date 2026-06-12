---
title: "trying to make my computer pretty broke gnome..."
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by Nicole on 2007-05-28
Hi,

I'm not sure if this is the right place to ask for help - if not, do let me know where would be better, and I'll be happy to move over there!

Yesterday I was playing with all kinds of things to make my computer prettier - I had had beryl installed and working fine for a few weeks, and then yesterday installed avant window navigator and screenlets to make it even prettier, and it all worked fine. Then I shut down my computer, and the next time I turned it on (this morning), I changed so that Beryl was the default session (previously, it had been gnome), and tried to log in. It froze at the starting window manager part of logging in. So I pressed ctrl-alt-backspace to get back to the login screen and tried logging in to gnome. Same problem. Logging in as failsafe gnome got me into gnome - hence the reason I can post this! - but produced the following error message:
[INDENT]
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.[/INDENT]

I've had a look at man dbus-launch and man dbus-daemon, but they are really too technical for me to be able to really understand and therefore use them. 

I've now uninstalled all the things I installed yesterday, and even removed beryl, and restarted and it's still having the same problems.

Does anyone have any ideas about how I can fix it? If there's more information you need from me, I'm more than happy to provide it - just let me know!

Many, many thanks for your help,

Nicole


ETA: problem solved - if you happen to have a similar problem, renaming your .gnome, .gnome2 and .gnome2_private files as .gnome.bak etc, and restarting fixed it for me - gnome then recreates those folders when it restarts, and the problem goes away. Technical it's not, but my computer now works, so I'm happy...

---

### Post by airtonix on 2007-05-31
wow what a bummer....do you know how you got "beryl" as an option in your sessions menu via the login screen?

for me, i use run xclient setup and or just run gnome as per usual then run the beryl-manager which i presume is replacing xorg & metacity somehow on the fly....but i also assume this could be wrong.

---

