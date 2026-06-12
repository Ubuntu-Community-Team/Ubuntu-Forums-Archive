---
title: "Devilspie problems"
date: 2007-03-14
forum: Desktop Environments
---

### Post by dld on 2007-03-14
Two problems with Devilspie:
1)  Using System/Preferences/Sessions/Startup I startup Devilspie along with
SeaMonkey, Flock, Gnome-terminal, and others.   Under Current Sessions I
see that Devilspie has order 50, and I can change it to a lower value, but I
can't make that change stick from one session to the next.

2)  SeaMonkey starts up two windows, browser and mail.  Same class, application.
Their titles are dfferent when they finally appear on screen, and change as I
use them.  But the mail window title includes "Inbox" if I was viewing an inbox
when I shut down the prior session.    I can't make  (contains (window_name)
do anything for me.  Perhaps these windows have other titles when being
formed??
  Don

---

### Post by dld on 2007-03-21
1)  It doesn't seem to matter that Devilspie has the same order as
programs opening windows.

2)  The following does the job:

(if (is (application_name) "Gecko")
   (begin
     (set_workspace 2)
     (if (contains (window_name) "Mail")
        (geometry "996x686+10+51")
        (geometry "1046x941+229+51")
     )
   )
)

---

