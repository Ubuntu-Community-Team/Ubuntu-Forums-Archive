---
title: "grep notification log file for gnome 3.12"
date: 2014-09-29
forum: Desktop Environments
---

### Post by cedardoc on 2014-09-29
I realize this is more of a gnome 3 question than am Ubuntu question, but maybe someone here has dealt with this problem and can help.

I love gnome 3.10+ (currently on 3.12) on ubuntu 14.04, except for one thing that drives me crazy.  When I get notifications to windows that are already open (like a Pidgin message or a bash script of mine opening a chrome tab), the window doesn't open but instead I get a notification that the window is "ready", and I have to click a bunch of times to see something that should just pop up.  Sometimes I'll get a message when I'm not at my desk and because the window doesn't pop up, I miss it.

Anyway, I thought that there must be a way to access some log of all notifications somewhere, but so far no luck finding it.  I just found out that as of gnome 3.12 it uses a different system called gnotifications in a bigger system called GIO.

Does anyone know how I can see changes in a text file somewhere to trigger a wmctrl script to make the window pop up any time that file changes and contains the word "pidgin" or "chrome" or whatever?


Thanks,
Dave

---

### Post by vasa1 on 2014-09-29
Would the answer to [Is there a way to view notification history?]("http://askubuntu.com/a/352125") help you at least partly? There's also an answer there involving a ppa if you're so inclined.

---

### Post by cedardoc on 2014-09-30
Thank you, that's close, but no cigar.  I get a response to anything I do with notify-send, but not with natively derived notifications...

I wonder if there's a different version of doing the same thing for the different notification platforms.  I noticed that pidgin uses libnotify (actually I haven't tested pidgin yet with this - everyone else is sleeping, ha ha)

---

### Post by cedardoc on 2014-09-30
update - this command at the terminal:

dbus-monitor "interface='org.freedesktop.Notifications'" | grep --line-buffered  "member=Notify\|string"

does catch pidgin notifications on my machine with gnome 3.12, so that's the main thing I needed.  Thank you!!

---

### Post by vasa1 on 2014-09-30
If you feel your issue is solved, please mark it solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

