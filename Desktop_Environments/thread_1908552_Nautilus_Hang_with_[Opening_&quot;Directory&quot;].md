---
title: "Nautilus Hang with [Opening &quot;Directory&quot;] Window in GNOME-fallback and GNOME 3"
date: 2012-01-13
forum: Desktop Environments
---

### Post by StewartM on 2012-01-13
Hello,

I don't know if this is a problem or normal, but I don't remember it.

My laptop running 11.10 currently exhibits the following actions:

a) Opening any directory using Nautilus via Places in GNOME-fallback also opens an "Opening 'Directory'" message window on the bottom panel as well as the directory itself (i.e., opening Documents will open Documents but also cause an additional "opening Documents" window to appear on the bottom panel). The directory itself opens almost instantly, but the "Opening 'Directory'" window hangs around for about 15 seconds. I can easily open and close various directories before their "Opening..." counterparts disappear.

b) Opening any directory in GNOME 3 does not show the window, but given that a spinning symbol hangs around for about 15 seconds as well it looks like the same 'hang' is occuring, just without a seperate window appearing.

c) I then open nautilus directly in the terminal, (user$: nautilus) thinking that I'd see a message what might be causing the hang. Lo and behold, there was no additional window, and nautilus opened instantly! So this only happens when starting nautilus via the GUI.

d) In Unity, I see no such indication of any 'hang' (however, it could be just hidden). 

e) I have tried to see if I can catch what's going on by observing GNOME-system-monitor but without luck.

f) It affects all three users on this computer, including one which is just a guest account which I don't use (so it's probably the result of a messed-up user directory)

g) Three things that might be relevant:

1) I am using encrypted /home user directories

2) Because of a bug in ecryptfs crashes, I am running the proposed 3.0.0-15-generic-pae kernel which contains a fix.

3) I have KDE 4.7 Plasma Desktop and Lubuntu installed, and have been experimenting with these. 

The last may be especially relevant because Lubuntu/LXDE uses the gtk 2 libraries and for a while when I first opened its file browser (pcmanfm) after logins I would get a "transport error" message, an error which didn't seem to effect operation and would not re-appear on subsequent pcmanfm openings. But now I get no error message at all when opening pcmanfm, not even the first time after logging in.

When I played around with Xubuntu with Ubuntu on the same laptop, I had a similar problem with Thunar (Xfce's file manager) bucking Nautilus. So is there a conflict between having and using nautilus and pcmanfm on the same computer? If so it's got to be at a fundamental level, not at the /home/user level as I have a user which hasn't used LXDE/Lubuntu and it is affected. 

Right now I just want to know if this is a problem, or is it normal after the update and I've just missed it. Anyone else have it? Anyone else have Lubuntu and Unity/Gnome/Gnome-fallback and seeing this?

StewartM

---

### Post by StewartM on 2012-01-14
I'm using 10.04 this morning, on my faster home box (3 GHz vs 2 GHz on the laptop), and I'm seeing that in GNOME 2.3 that there is for a fraction of a second an "opening [directory]" window appears too. My 10.04 box has only GNOME 2.3 on it, so there can't be any possibility of Nautilus bucking another file manager.  

Firefox 9 gives the same "opening Firefox" window as well, but only briefly, and has for years, so I expect that.

But still--12-15 seconds for a file manager to fully finish opening? I don't think I remember this. Is anyone else experiencing similar delays in GNOME 3/Classic GNOME on 11.10? (The window opens and is available immediately, but the "Opening ..." window hangs around that long).

StewartM

---

### Post by StewartM on 2012-01-18
Well, well. Seems that on the Arch Linux forums someone has exactly the same problem:

[http://forums.opensuse.org/english/get-technical-help-here/applications/469213-nautilus-slow-startup.html](http://forums.opensuse.org/english/get-technical-help-here/applications/469213-nautilus-slow-startup.html)

The only thing that for-sure eliminates it is to download GNOME tweak tool, and go to "Desktop" and then turn off "Have the file manager manage the desktop".

Why this applies to all my home directories, even accounts that are barely used, is beyond me. I don't know whether or not to mark this as "SOLVED" because this really isn't a solution, just a workaround.

-StewartM

---

### Post by elboulangero on 2012-08-15
Same situation for me, except that the  "Have the file manager manage the desktop" doesn't solve the problem...

---

### Post by spazio73 on 2012-08-17
I've the same problem so i've opened a bug report

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/999719](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/999719)

The bug has been confimed but nobody is working on it.

:(

---

