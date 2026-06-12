---
title: "How to troubleshoot disappearing Gnome extensions?"
date: 2018-11-19
forum: Desktop Environments
---

### Post by frankvw on 2018-11-19
On Ubuntu 18.04LTS running Gnome 3 almost all of my Gnome extensions sometimes disappear after unlocking the screen or resuming from hibernation. I have grabbed a copy of the syslog (nothing else in /var/log appeared to contain relevant data). This started a few weeks ago and is therefore almost certainly related to the notorious "some sort of  update that broke something". :)

When all is well my desktop looks like this:
[IMG]http://www.silverwolfmedia.com/tmp/NowYouSeeThem.jpg[/IMG]

But when things go sideways after unlocking the screen or resuming from hibernation, this is what I'm left with:
[IMG]http://www.silverwolfmedia.com/tmp/NowYouDont.jpg[/IMG]
(Note how the extensions haven't just disappeared from the Tweaks extension list but actually have stopped working as well: no more menu, no more static workspaces switcher, etc. in the top and bottom bars.)

Problem is, I have plowed through the syslog which contains tons of data, but I don't really know what to look for. So my question is: how can I find out what's going wrong where so I can file a proper problem report with the right party instead of just whining about how "it doesn't work"? :P

All suggestions would be appreciated!

// FvW

---

