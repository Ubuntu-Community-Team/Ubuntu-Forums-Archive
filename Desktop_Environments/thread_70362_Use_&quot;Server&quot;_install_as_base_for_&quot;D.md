---
title: "Use &quot;Server&quot; install as base for &quot;Desktop&quot;?"
date: 2005-09-29
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2005-09-29
Ive seen blips about people doing this. For people who have; has it been a pain?

Im the type of user who only whats installed whet he needs/wants. Bloat drives me nuts. I know windows enough to get a xp.iso down to 180 megs and just over 600megs installed. With linux though Im lost. 

So. Is it worth it to do a "Server" install then adding what I need? Or is it more trouble than its worth?

---

### Post by SilentCacophony on 2005-09-29
I'm the same type of user. I have a minimal install that I set up like that, which is what I usually use. I also have a regular install mainly so that I'm familiar enough with it to help out new users here, and as a backup OS in case I break my other. ;) 

I don't find it very difficult at all, but I used to be an Amiga user, and so am more familiar than some with working from commandline and GUI equally. I found the total install time to be about equal, since I wasn't installing and updating packages I didn't use.

Anyway, my recommendation is to use the aptitude package manager, which lets you easily browse packages from a console or terminal, and it also does a good job of uninstalling unneeded dependencies when you uninstall packages. I'm not sure if it's there by default, but if not, then **sudo apt-get install aptitude**, and you're off.

From there, you can do anything. I had one install with no X at all, using gpm for mouse support, screen for mutiplexing a single console, mc for filemanager, w3m, lynx and links for browser, etc... :) Or, for a light X environment, you could try something like: x-window-system-core, xscreensaver, menu, apmd, openbox, obconf, xterm, rox-filer, browser/email client of choice, and maybe fbpanel if you want a panel... If you don't want to have to *startx* to get into X, you'd want xdm, wdm, or gdm to log straight into X.

It's a good way to learn more about using linux in general, and also gives the satisfaction of having just what you want. You just have to be preapared to do some research...

EDIT: Thought I'd add a link to an uploaded [screenshot]("http://ubuntuforums.org/gallery/showimage.php?i=997&c=7") of my minimal install.

---

### Post by recce101 on 2005-09-30
[QUOTE=MetalMusicAddict]Is it worth it to do a "Server" install then adding what I need? Or is it more trouble than its worth?[/QUOTE]

No trouble at all, quite painless, even for this senior citizen Linux newbie. I prefer a light desktop and am very happy with XFCE. Here's my routine:

Do a server install, make sure everything is working, tweak the mount points to my liking, and edit /etc/fstab accordingly. Expand the /etc/apt/sources.list to include the universe and multiverse repositories as described at ubuntuguide.org, then apt-get update. Next, apt-get install x-window-system-core xfce4 gdm. Reboot into the XFCE desktop and tweak as desired. Then apt-get install synaptic and use that to add whatever other software you want.

---

### Post by az on 2005-09-30
sudo apt-get install x-window-system-core icewm menu mozilla-firefox synaptic xterm

Aptitude is part of the base install.  So is dselect.

---

