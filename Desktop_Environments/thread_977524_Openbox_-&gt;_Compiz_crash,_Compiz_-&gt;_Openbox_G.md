---
title: "Openbox -&gt; Compiz crash, Compiz -&gt; Openbox Good"
date: 2008-11-10
forum: Desktop Environments
---

### Post by Paradigm_Complex on 2008-11-10
I feel like I'm missing something really simple.

I spend most of my time in openbox, but occasionally I'll throw up compiz fusion (mostly to show off).  When my .xinitrc is 

```
feh --bg-center /home/paradigm/themes/goban_bg3.jpg & 
xmodmap .xmodmap &
openbox

```

and I try to switch to compiz with

$ compiz --replace

X will crash with the following stderr:

```


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux euclid 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 10 09:42:18 2008
(==) Using config file: "/etc/X11/xorg.conf"
Warning: Only changing the first 10 of 32 buttons.

(openbox:8929): GLib-CRITICAL **: g_hash_table_destroy: assertion `hash_table != NULL' failed

(openbox:8929): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed

(openbox:8929): GLib-CRITICAL **: g_hash_table_destroy: assertion `hash_table != NULL' failed


waiting for X server to shut down XIO:  fatal IO error 17 (File exists) on X server ":0.0"

      after 367 requests (363 known processed) with 28 events remaining.

...



```

(The "Warning: Only changing the first 10 of 32 buttons." is due to xmodmap rearranging my mouse buttons)

If I start X with just "compiz" in my .xinitrc and switch to openbox with

$ openbox --replace

X will also crash.  I was at a loss as to why I would need to restart X to switch window managers.  I was about to give up trying to get it to work when I found that if I start x with "compiz --replace && emerald --replace" in my .xinitrc, I can switch to openbox with no problems at all!  Not only that, but I can switch back and forth between compiz and openbox, so long as I've started with "compiz --replace && emerald --replace" in my .xinitrc.

I was curious as to why the "--replace" would change anything when initially starting a window manager, but was willing to overlook the small technicality now that I got it working.  I typically prefer to use openbox, so just put "openbox --replace" in my .xinitrc... and I found that when I try to switch to compiz it still crashes.


EDIT:

I got it to work... sort of.  If I start X with "openbox --replace && emerald --replace" switching works, and emerald doesn't seem to do anything.

I'd prefer not to needlessly run emerald.  Any ideas why I would need to run emerald at all to get this to work?

---

