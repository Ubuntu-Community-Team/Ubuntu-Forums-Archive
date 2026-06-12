---
title: "KDE Fails to Load past Harddrive Icon after upgrade to 14.10"
date: 2015-02-03
forum: Desktop Environments
---

### Post by Illydth on 2015-02-03
Hopefully this isn't a duplicate post.  Thanks for any assistance in advance.

My work desktop was on the previous LTS version of Ubuntu (12.04 I believe).  Recently I just upgraded to 14.10 (Utopic Unicorn).

The upgrade went fine (no issues observed during the upgrade process).  I've been out sick the last couple days and I came back to find my machine powered down.

When I went to boot this morning, the system came up to the normal login menu (Using GDM since the default lightdm wasn't handling Kerberos logins well).  When I go into my normal user KDE begins to boot up, displays the "hard drive" (First Icon in the boot process) and then freezes up.  Mouse continues to move and I can console out (ctrl-alt-F1) and log in properly without an issue.  I've fully updated the system to no avail.  Upon logging in I get a message that says I have 1 running zombie process, which turns out to be a sub process of kdeinit4 (start_kdeinit_w)...it looks like KDE login is going zombie on me...this happens EVERY time I attempt to log in.

init(1)----gdm(<pid>)----gdm-session-wor(<pid>)----upstart(<pid>)----startkde(<pid>----kdeinit4(<pid>)----start_kdeinit_w(<pid>) <--- Zombie Process

ALL users on the system experience the same thing.  Gnome is not affected (I can log in to the gnome desktop without an issue).  I've tried removing my user's .kde home directory (/home/<user>/.kde) to remove any bad settings (didn't work).  I found some advice on other searches suggesting that it could be an Effects/Renderer issue causing the problem but setting .kde/share/config/kwinrc's "Compositing" section to either "Backend=Xrander" (Something like that) or simply to "Enabled=false" doesn't fix it.

I tried pushing non-graphical runlevel and then trying "startx" to get into XWindows (I guess Ubuntu doesn't have a non-graphical runlevel), but I did manage to get GDM killed and run startx...it, however, took me into a partial gnome setup, not KDE.  

No .xsession-errors file is created in my home directory.

In case it matters, hardware is a Dell 7010 Optiplex with an integrated Intel Graphics card.  This thing has worked for months now with no problems.

HELP?  I suspect I could probably reinstall the system and get it back on it's feet, but there's almost a year of customized settings and additional installed packages that will take me FOREVER to figure out what's missing/broken/should have been installed but wasn't by default.

It's obviously a KDE issue / something wrong with the state of the system after upgrade, but I couldn't begin to determine where to go to figure out what's wrong.

--Illydth

---

### Post by Illydth on 2015-02-03
At this point I'd be happy to hear the words "Can't fix your KDE Installation, but here's how you can blow it away completely and reinstall the entire KDE packageset from the ground up!"

--Illydth

---

### Post by mörgæs on 2015-02-04
See my 'upgrade' thread, link in my signature. First post, search for *dpkg*.

---

