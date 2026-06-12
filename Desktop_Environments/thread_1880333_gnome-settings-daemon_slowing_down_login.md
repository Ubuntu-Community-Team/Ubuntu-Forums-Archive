---
title: "gnome-settings-daemon slowing down login"
date: 2011-11-13
forum: Desktop Environments
---

### Post by Diskdoc on 2011-11-13
Hi!

Oneiric (upgraded from Natty) brought with it a small nuicance for me. Booting is ok but _logging in_ is slow. The system just seems to wait for a minute or so, not much harddrive activity to speak of.

I switched to console and saw gnome-settings-daemon at 100% CPU during this time of stalling.

What's wrong and how can I resolve it? Attaching .Xsession-errors in case it's of any help.

---

### Post by Freddi67 on 2011-11-15
Hi!
I've been searching so long and wondering why nobody else seems to know the issue. My login is also slowed down very much by [FONT=Courier New]gnome-settings-daemon[/FONT] (starts sometimes several seconds after being logged in). The system monitor says it is "undisruptable". It has very high disk read-write activity (very noisy) which causes the system to lag/freeze. My only work-around is to "stop" the process immediately after login (I'm not sure if that's the english term, don't kill the process but pause it).

I had tried many other things without success, like

[LIST]
[*]creating a new user account with fresh configuration
[*]purging and reinstalling gnome-settings-daemon
[*]My home is encrypted (so if the daemon tries to read thousands of small files it could be slow). So I linked [FONT=Courier New].gconf[/FONT] to a folder outside of the encrypted directory. No difference.
[/LIST]
I hope someone has more ideas...
Maybe those people have the same cause for slow login?
[ ubuntuforums.org/showthread.php?t=1855821&highlight=gnome+settings+daemon+slow&page=3]("http://ubuntuforums.org/showthread.php?t=1855821&highlight=gnome+settings+daemon+slow&page=3")

---

### Post by Diskdoc on 2011-11-29
Seems to boot fine now! I'm guessing one of the latest updates fixed the problem! Happyyyy! I was not looking forward to figuring out what configuration files to delete..

---

### Post by Diskdoc on 2011-12-06
Sadly, I was mistaken. Problem still remains.

---

### Post by Diskdoc on 2011-12-06
I switched to console when the CPU hogging of gnome-system-daemon was occurring, did a quick cat on .xsession-errors and saw this:

> gnome-session[2464]: WARNING: Application 'gsettings-data-convert.desktop' killed by signal
gnome-session[2464]: WARNING: App 'gsettings-data-convert.desktop' respawning too quickly
gnome-session[2464]: WARNING: Error on restarting session managed app: Component 'gsettings-data-convert.desktop' crashing too quickly


..which hopefully brings us closer to the problem! I saw some bugs regarding this here and there but they're all supposed to be closed and fixed. Does anyone here know more about this?

---

### Post by SvenBuntu on 2012-01-11
I have the a similar problem with the same symptoms. Quick boot but really slow to load desktop after login in. syslog are showing issues about gsettings-data-convert.desktop. 

Anyone found a good resolution for this?

---

