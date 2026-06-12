---
title: "when system tray icons become floating windows"
date: 2007-01-26
forum: Desktop Environments
---

### Post by freeatlast? on 2007-01-26
hi

i have a problem that a gnome or perhaps ubuntu expert may be able to help with - matlab (a mathematical package) can usually be interrupted from running a script by hitting CTRL-C. installed on my ubuntu edgy, CTRL-C does not interrupt matlab's processing, but instead does some strange and too-quick-to-follow window manipulations which end up with nothing particularly different except that my system tray icons (battery monitor and typing break) jump out of the system tray and become floating windows, see image below.

[IMG]http://i10.tinypic.com/2w2g37q.png[/IMG]

now i'm not expecting anyone here to be a matlab expert (necessarily!), so i'm not expecting to get an answer on the strange behaviour of matlab (though please shout if you know!), but i thought someone might know what has happened to these system tray icons which may help me to fix/mitigate the problem. in particular i thought...

* how does this CTRL-C reach the desktop instead of matlab (matlab is busy processing so if it doesn't "accept" the CTRL-C in short order might it be redirected to the desktop?)

* does CTRL-C mean "undock system tray icons" to the desktop? if so, can i change this? then i might not be able to interrupt matlab but at least i wouldn't have to reboot

* can i redock these windows somehow? i've tried every combo of left and right clicking and dragging to no avail so far :D

any thoughts on what is going on here, basically, it's quite an interesting result and must be explicable... :)

thanks
ben

---

### Post by freeatlast? on 2007-01-26
update - i managed to capture a screenshot during the wierd behaviour (only happens first time i ctrl-c in matlab).

[IMG]http://i13.tinypic.com/2r6is6g.png[/IMG]

note that the top and bottom toolbars that usually adorn my screen have disappeared temporarily, there is a 2x toolbar height empty space present at the bottom which is part of the matlab window, and the matlab window is frameless. on some occasions the matlab window gets to repaint before it all goes back, and there's no doubt about it - the matlab window has gone to full screen.

so perhaps CTRL-C means 'go fullscreen' to gnome, or something... errr... in any case, the system tray is emptied by this (those floating windows appear at this point), and then a moment later (less than a second), the matlab window goes back to where it was, the toolbars reappear (and are repopulated, you can watch it happening), but the floating windows remain and do not redock to the system tray.

fascinating. also, annoying.

---

### Post by tweedledee on 2007-01-27
> **freeatlast? said:**
> fascinating. also, annoying.

Agreed.  I had no idea you could do that!  I'm also quite sure that Ctrl+C should not do that, as I use that key all the time to kill program runs (not Matlab, though).  Do you see the same effect when Matlab is not running?  I'd guess it has something to do with Matlab if it ony occurs when Matlab is running; if it always occurs, you have a more basic problem.

---

### Post by freeatlast? on 2007-01-27
just matlab, and what's more, only the very first time i press CTRL-C in that matlab session. subsequent presses of CTRL-C do not cause the wierd behaviour again, but neither do they reach matlab, so nothing at all happens when i CTRL-C after the first time (matlab should interrupt). if i close and restart matlab, i am granted one new weird CTRL-C to spend as and when i choose.

now i'm getting used to it, i'm thinking the behaviour looks like what would happen if i turned off both my top and bottom panels (bars, whatever). i don't want to test that, because i'm not sure i'd be able to get my panels back! so... is it possible that the CTRL-C is being sent to the panels, as if they were focused rather than matlab, and that the panels application is thus being killed/closed/something similar?

hang on a sec... so i just tried "killall gnome-panel" (without matlab's involvement) and the effect is much the same. so it looks like that first CTRL-C i send to matlab is somehow getting routed elsewhere and interpreted as "kill the gnome-panel process". i was aware that CTRL-C meant "interrupt" in a shell prompt, but i didn't know that worked at a GUI level. and how it's getting passed on to gnome-panel i've no idea. any further ideas? may it be relevant that the matlab front-end runs on the JVM?

---

### Post by tweedledee on 2007-01-27
> **freeatlast? said:**
> so it looks like that first CTRL-C i send to matlab is somehow getting routed elsewhere and interpreted as "kill the gnome-panel process". i was aware that CTRL-C meant "interrupt" in a shell prompt, but i didn't know that worked at a GUI level. and how it's getting passed on to gnome-panel i've no idea. any further ideas? may it be relevant that the matlab front-end runs on the JVM?

Truly fascinating.  I can reproduce your "floating system tray" behavior if I kill the panel, and from then on everything sent to the tray ends up floating.  That seems to be a bug in the system tray, so I've filed one with gnome (you can confirm it and make sure it matches what you observe): [http://bugzilla.gnome.org/show_bug.cgi?id=401481](http://bugzilla.gnome.org/show_bug.cgi?id=401481) .

I don't think it's the JVM, or at least mine don't act that way.  But I don't have matlab to test, either.  All I can say for sure is that it's not normal - have you tried a google search on this?

---

### Post by freeatlast? on 2007-01-27
i have googled fairly widely, but only since my previous post have i understood roughly what was happening so most of my googling was probably in vain - still, i had a brief further attempt following that and haven't turned anything else up.

your bug report looks fine to me - i wasn't going to class this as a bug, really, since it involves killing the gnome-panel process, but it is at least a behaviour that could be improved upon. how that CTRL-C ends up killing it might be a bug, i suppose, but i don't think it's a bug that the system tray behaviour goes a bit funny after killing the panel process without warning (the gnome-panel hosts the system tray, right? but i'm guessing the system tray is not a separate process but a plug-in or some such for gnome-panel?). in any case, i remember windows had a similar profile under these circumstances - if you killed explorer, existing system tray icons were lost for good, though new ones could be added and behaved correctly.

now - i did find this (on a completely unrelated page, but it's a clue nonetheless)...

"So, if a process has the same group id with the tty, it can be kill by “ctrl-c” from that tty, no matter it is in background or foreground. In some old shells without job control feature (such as msh in busybox 1.00), if you start a process in background (with an “&”) then list processes with “ps -j”, you’ll find that the “bg” process has the same PGID with tty. In this situation, ctrl-c can kill both you fg and bg processes."

now, i was starting matlab from a launcher in gnome-panel. trying this again, and running ps -ej in a separate term i get:

> ps -ej
  PID  PGID   SID TTY          TIME CMD
...
10940 10940 10940 ?        00:00:03 gnome-panel
...
11898 10940 10940 ?        00:00:05 MATLAB
...
> 

in other words, the matlab process _does_ share a PGID with gnome-panel. now, the behaviour that CTRL-C in the matlab window kills gnome-panel makes a bit more sense. furthermore... when gnome-panel is killed the first time i press CTRL-C in matlab it automatically restarts, but, of course, with a different PGID. hence, further CTRL-C presses do not kill it again, explaining the "first time only" bit of the problem.

well, it seems there is a mechanism whereby we can kill gnome-panel from matlab using CTRL-C. furthermore, i can work around this temporarily by starting matlab from a separate terminal, though that's a bit rubbish.

now - the matlab that is still alive after death/resurrection of gnome-panel is still unresponsive to CTRL-C, which is weird (well, it's probably expected given that the first one fell off and hit gnome-panel instead, but it's still weird that CTRL-C bounces off it in the first place). whereas, a matlab started from a separate prompt does receive and interpret CTRL-C correctly.

leaving 2 questions, i think: first, why does CTRL-C bounce off that matlab at all regardless of its having the same PGID as the panel, and second, why does some app (for example, matlab or gaim) started from a gnome-panel launcher get the same PGID as gnome-panel, whereas some other (e.g. gnome-terminal) gets a different PGID (all settings other than the command to be run being the same in both launchers). oh, and third, what's a PGID?

and, practically speaking, to solve my problem - how do i force matlab to run from a launcher in the gnome-panel without starting a terminal (and thus cluttering my task bar) but yet with a distinct PGID from gnome-panel. and even if i manage that, will the resulting matlab process be responsive to CTRL-C? all i know is that if i start an independent gnome-terminal (different PGID from panel) and start "matlab" from there, it gets a different PGID (again, so 3 now) and it responds correctly to CTRL-C anyway. perhaps CTRL-C gets routed to the "base" process of those sharing a PGID? no - if i CTRL-C in gaim (for example), which shares the panel's PGID, i get sensible behvaiour. but then gaim captures this CTRL-C and responds to it (pops up a dialog of some sort).

interesting, interesting.

---

### Post by tweedledee on 2007-01-28
> **freeatlast? said:**
> leaving 2 questions, i think: first, why does CTRL-C bounce off that matlab at all regardless of its having the same PGID as the panel, and second, why does some app (for example, matlab or gaim) started from a gnome-panel launcher get the same PGID as gnome-panel, whereas some other (e.g. gnome-terminal) gets a different PGID (all settings other than the command to be run being the same in both launchers). oh, and third, what's a PGID?

1. I'm not sure.  I'd guess either a bug, or possibly matlab (presumably because it is working hard on something) delays the response to Ctrl+C long enough for it to get passed to another process?  Probably matlab just isn't playing nice with respect to IDs, but I don't really know.

2 & 3.  PGID is the "process group ID."  Basically, all programs started as a "branch" or pipe or varius other means from a single program end up sharing the same PGID.  The idea behind it is that you can kill a related group of programs all at once, although that is not what it is happening in your case (I'm assuming that other programs started from your panel remain open during this liittle game).  I hadn't noticed that everything started from the gnome-panel shares that PGID - that's actually a little annoying.  I may file a feature request at Gnome to modify that behavior.

> **freeatlast? said:**
> and, practically speaking, to solve my problem - how do i force matlab to run from a launcher in the gnome-panel without starting a terminal (and thus cluttering my task bar) but yet with a distinct PGID from gnome-panel. and even if i manage that, will the resulting matlab process be responsive to CTRL-C? all i know is that if i start an independent gnome-terminal (different PGID from panel) and start "matlab" from there, it gets a different PGID (again, so 3 now) and it responds correctly to CTRL-C anyway. perhaps CTRL-C gets routed to the "base" process of those sharing a PGID? no - if i CTRL-C in gaim (for example), which shares the panel's PGID, i get sensible behvaiour. but then gaim captures this CTRL-C and responds to it (pops up a dialog of some sort).

I don't believe you'll be able to override the panel's launching behavior.  However, it appears that if I launch an application from the panel but select the "in a terminal" option, the terminal gets the same PGID but the program gets a unique PGID.  While that still leaves you with an extra terminal wndow, at least you can still have a launcher.

---

### Post by freeatlast? on 2007-01-29
> **tweedledee said:**
> I don't believe you'll be able to override the panel's launching behavior.  However, it appears that if I launch an application from the panel but select the "in a terminal" option, the terminal gets the same PGID but the program gets a unique PGID.  While that still leaves you with an extra terminal wndow, at least you can still have a launcher.

yeah, that's where i've ended up. it's not elegant but it works well enough which suits me for now. thanks for all your help and info. i think i agree with you that's it's not smart for launched apps to share the PGID of the launcher (given your explanation of PGID), so i agree that might be worth a feature request. but i guess it hardly classes as urgent.

unless anyone's got anything more to add, i think i'll leave that there for now and perhaps revisit when i've time to do a bit of background reading and investigate more fully. thanks again, dude.

---

### Post by Flare183 on 2007-01-29
I am having the same problem, but not with GNOME applets, KDE applets running under GNOME.

---

### Post by tweedledee on 2007-01-30
One of the panel developers is looking into it, but thinks this isn't normal (i.e., all apps shouldn't end up with the same PGID).  In which case this may be an Ubuntu customization problem, and I'll shift the problem over to them.

Flare183, do your KDE applets share the gnome-panel PGID as well (from ps -ej output)?  I'm not certain if the PGID issue and the floating window issue are actually separate.  Also, what steps are leading to your floating windows (I assume that's what you mean by "same problem")?

---

### Post by Lil_Eagle on 2007-01-30
Interesting thread.  I find that I run into the same and I run KDE.  What floats?  The system updater.  Why?  No clue.  Does it always do that?  No.

I was thinking it might have something to do with Beryl.  Beryl is still quite buggy and does strange things, but I doubt if that would be a result of buggy Beryl.  It's only slightly annoying, just like the opacity of the panels are sometimes slightly different in places.

---

### Post by Flare183 on 2007-01-30
No, they just sit there, and the only way i can make them go back to the system tray is to restart GDM or even sometimes I have to restart the entire system.

---

### Post by Lil_Eagle on 2007-01-31
Hmm.  Since I don't use Gnome, it's hard for me to say.  I do know that since I upgraded to KDE 3.5.6 I haven't seen any floating windows.  On the other hand, the adept-notifier that normally should sit in the system tray is missing.

---

### Post by tweedledee on 2007-02-09
For the interested, there was a bug opened on Launchpad about this issue around the time this thread started: [https://bugs.launchpad.net/ubuntu/+source/gossip-telepathy/+bug/80370](https://bugs.launchpad.net/ubuntu/+source/gossip-telepathy/+bug/80370).  I have posted and highlighted this thread, so perhaps the cause will be tracked down.

---

### Post by tweedledee on 2007-02-17
Gnome developer claims it is a (now fixed) GTK bug - hopefully this issue will therefore be gone in Fiesty.  See [http://bugzilla.gnome.org/show_bug.cgi?id=401481](http://bugzilla.gnome.org/show_bug.cgi?id=401481).

---

### Post by inane on 2007-07-04
I have this problem on two machines (one edgy and one feisty)

the problem occurred after one of the recent updates, but now my tray icons refuse to go back, no matter how many restarts I do.

---

### Post by Nythain on 2007-07-05
this was a regular problem when kde would crash on me, half my system tray icons would do the same thing, i couldnt close the "floating windows" or anything, only thing that would fix it was a restart... never did figure out what or why, but i havent had a problem since i switched to fluxbox :)

---

