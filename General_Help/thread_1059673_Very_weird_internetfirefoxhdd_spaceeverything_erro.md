---
title: "Very weird internet/firefox/hdd space/everything error"
date: 2009-02-04
forum: General Help
---

### Post by Gizenshya on 2009-02-04
I delete stuff, and it goes away.  so far, so good.

I check disk space after that.. same as before.  0 bytes (yes, not a single byte free).  Delete a few hundred more MB, still 0 bytes.  And yes, I empty the trash as well.

For some reason, I'm constantly downloading around .5 Kib to 1.2 Kib.  even when firefox and everything else is done.

I can't do much of anything.  system monitor won't start (I guess it needs to write something to disk first?).  I can't click back on firefox.  On a side note, I now realize how much we take it for granted...

I've moved over gb's of files and still nothing.

If I try to put something back, I can't.  Luckily firefox doesn't die if it can't write to disk (which is why I can type this up).  go firefox! :D

I just updated from 8.04 to 8.10 btw.  I restarted and its still like this.

ohh, and all my persoanl settings are gone.  no bookmarks (even the ones I had), for example.  can't make any new ones.  I am keeping a text file atm (on another drive) as backup.  Apparently its only my ubuntu disk that is having the issue.

---

### Post by yther on 2009-02-04
If I had to guess, because something similar happened to me once, perhaps something is causing your system logs to become huge and they are eating all of your disk space.  Check the files in /var/log/ and note their sizes and time stamps.  

If it turns out to be log file bloat, then next it's time to find out what's causing them to be so big.  Either there is some problem, or (also happened to me) unnecessary settings could be causing thousands of messages that shouldn't be there.

Examples of mistakes I have made include firewall settings that logged *every packet*, and some kernel module that was spewing out dozens of messages every second.  These didn't eat up all of my disk space, but they came close.

You may also want to check your personal temp directory.  Sometimes stuff like X11 messages or KDE temporary files become very large.

If you happen to have something called "baobab" on your system, that could help you determine where the problem is by showing graphically where the biggest files (and directories) are.  You need to run it via sudo, however, or else it can only analyze the files you can normally read.

Good luck!

---

### Post by Gizenshya on 2009-02-04
hmmm...

nothing suspicious there.  but In narrowing it down in the var folder, I found this...

var/cache/apt/archives

3.5 GB worth of mainly .deb files.

are these the programs themselves (their installation directory), or just where they were cached BEFORE installation?  I'm thinking the latter, and if thats the case, then they should be ripe for deletion, right?

---

### Post by Gizenshya on 2009-02-04
decided they aren't needed...

but I can't delete them.  permission is denied on all files.

what do I do?

---

### Post by Gizenshya on 2009-02-04
ok, I googled a bit and found the following command...

```
sudo apt-get clean
```

that did the trick (for deleting the files).  "back" still doesn't work.. I'm going to do a little more testing and see how things go and I'll post if it fixed the other problems.

---

### Post by cariboo on 2009-02-04
If you run:

```
df -h
```

in a terminal you will get a better idea of where you don't have enough free space.

Jim

---

### Post by yther on 2009-02-04
I think perhaps Jim means "du -h", which will show you a summary of **d**isk **u**sage in "**h**uman readable" form (MB, GB, etc.), starting from your current location.  So you'd start in / (the very top) and see where the biggest stuff is, change into there and run "du" again, and so on.  ("df" shows you free space, broken down by the currently mounted volumes, so if you have almost everything on one disk/partition it may not be very useful.)

---

