---
title: "GDM post-login freezes for quite a while"
date: 2006-03-01
forum: Desktop Environments
---

### Post by meowsqueak on 2006-03-01
I use Gentoo, so I'm quite familiar with the potential speed of this software. However I like Ubuntu for certain reasons so I'm using it now at home.

I'm not sure if this is related, but it happened at the same time - I configured my xorg.conf for a second monitor (using dual-head nvidia card) and now when I log in with gdm and Gnome starts up, it sits there on 'Window Manager' (i.e. the first icon) for about 2 minutes. It's as if it's frozen. Only, if I leave it it eventually carries on and starts up Gnome proper. I can't get anything useful from top or ps (no massive CPU load, every process is just happily spending most of it's time asleep). I can't see any way to determine what is holding everything up.

I tried fluxbox too. Fluxbox also has an obviously too-long delay as well, only not quite so long (say, 30 seconds?). With Gentoo (and Ubuntu too before a few days ago) it would start in under 1 second, so something isn't right here.

My /etc/hosts file has my hostname against 127.0.0.1 in case anyone was about to suggest that... :)

---

### Post by joshuapurcell on 2006-03-01
You could try starting off at one of the terminal windows (Ctrl-Alt-F1 for example), turn off the gdm service (**sudo /etc/init.d/gdm stop**), then **startx**. This will automatically start your default window manager and move you to the terminal at F7, but you can then move back over to the F1 terminal and see what error messages pop up (if any).

---

### Post by meowsqueak on 2006-03-01
Thanks for your reply - I'll give that a try. However I think startx ends up using ~/.xinitrc (which I'll have to create) rather than whatever session script GDM uses, so it's not precisely the same. I'll give it a shot however.

---

