---
title: "Difficulty launching app from KDE desktop icon"
date: 2005-09-06
forum: Desktop Environments
---

### Post by jdawdy on 2005-09-06
I installed Deer Park 2 on Ubuntu running KDE desktop via the binary installer to /usr/local/firefox.

However when I try to make a desktop shortcut link and put /usr/local/firefox/firefox into the command box, Deer Park will briefly flicker onto the screen then close.

I have fiddled with the permissions with no luck. I can launch it from root, or run as other user (root) or with sudo from a terminal. However I would prefer to just have an icon that launches it without resorting to sudoing via a terminal.

I removed the Firefox installation that was already installed.



tnx
Jim

---

### Post by cwaldbieser on 2005-09-06
[QUOTE=jdawdy]I installed Deer Park 2 on Ubuntu running KDE desktop via the binary installer to /usr/local/firefox.

However when I try to make a desktop shortcut link and put /usr/local/firefox/firefox into the command box, Deer Park will briefly flicker onto the screen then close.

I have fiddled with the permissions with no luck. I can launch it from root, or run as other user (root) or with sudo from a terminal. However I would prefer to just have an icon that launches it without resorting to sudoing via a terminal.

I removed the Firefox installation that was already installed.



tnx
Jim[/QUOTE]
You really should net need to run it as root or with sudo.  I would suggest you install it to ~/usr instead, and you can give it a test drive from there.  You will be able to fiddle with ownerships and permissions in your home directory without having to sudo all the time.

As far as making the launcher-- I find that some programs only work correctly when they are launched with thier full path.  I just create a shell script to run the full path of the program, then create a shortcut to the shell script.

---

### Post by jdawdy on 2005-09-10
Doing a search, I ran across mention of similar problems with Deer Park, so apparently it is specific to that build.

I installed the latest linuz firefox installer from mozilla.org, and it works fine, shortcuts and all.

Jim

---

