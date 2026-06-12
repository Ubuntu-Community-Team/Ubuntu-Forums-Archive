---
title: "How can I move TF2 or Killing Floor from Windows to ubuntu?"
date: 2013-09-08
forum: Gaming &amp; Leisure
---

### Post by LaizureBoy on 2013-09-08
[FONT=arial black][SIZE=5]Hey guys![/SIZE][/FONT]
[U]
So, today I have a disturbing question, at least for those of us who have slow internet speeds...[/U]

[I]Is it possible to transfer my current **TF2 or Killing Floor** (both games supported by Linux) over to my Ubuntu partition, from my **Windows** one?


[/I]I have seen **repeated** posts about how to do it, but they are all from the *beginning* of the year; months before they replaced the **old file system** and exchanged it with a [B]new one.
[/B]I have tried multiple random ideas I had about how it might work, but I'm desperate, and I mean, **ANYONE** that has a 200 kb/s connection knows it sucks downloading ***14 GB's*** of data.

Anyways, if anyone could possibly help me out with this, it would be [I]**GREATLY** appreciated!

Oh, I'm running Ubuntu 12.04 btw; 13.04 gave me some crappy internet speed.[/I]

---

### Post by oldrocker99 on 2013-09-08
Both TF2 and Killing Floor have Linux versions, it's true, but the versions on your Windows partition are the Windows versions; wine might run them, but it's unlikely. I hate to be the bearer of bad news, but the best (in fact, the **only**) way to get both those programs on your Linux partition is to redownload the Linux versions using Steam for Linux. Maybe an allnighter download?

---

### Post by KryoMouse on 2013-09-08
There used to be a trick where you could copy the SteamApps folder from one OS to another, then run validation in an attempt to get the right files for the OS you've moved to. However I'm not sure that this method works anymore, common library files (with the exception of the binaries) or not.

---

### Post by colinlandman on 2013-09-09
Steam has the capability to make a backup of games in your library. You'll find this option in the menu "Steam -> Backup and Restore Games...". I was successfully able to restore a Team Fortress 2 that was backed up on a Windows machine. A small download was required afterwards, but at least the bulk of the application was restored. This is because assets are shared between both Operating Systems, only some platform specific executable code is ignored and this is what causes the download. The game is running flawlessly. I should also add that I did this with the new file system that was introduced by Valve.

I would recommend doing a backup of those games and restoring them on your Ubuntu Steam client using the same menu mentioned above.

---

