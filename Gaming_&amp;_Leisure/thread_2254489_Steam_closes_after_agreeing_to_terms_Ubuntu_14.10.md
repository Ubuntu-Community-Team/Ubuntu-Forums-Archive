---
title: "Steam closes after agreeing to terms Ubuntu 14.10"
date: 2014-11-27
forum: Gaming &amp; Leisure
---

### Post by xfearxnxloathing on 2014-11-27
Installed Steam through Terminal 
> sudo apt-get install steam
Everything installed fine.

I open it and immediately get an error
> OpenGL GLX context is not using direct rendering, which may cause performance problems.

For more information visit [https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457](https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457).
Steam continues to run and come up so I click "Okay" button on the error window and it closes  it with Steam still up and running on the "Steam Subscriber Agreement" window. I click "I Agree" and everything disappears.

When run from Terminal I get: 
> bravewolf@Legacy:~$ steamRunning Steam on ubuntu 14.10 32-bit
STEAM_RUNTIME is enabled automatically
[2014-11-27 09:51:46] Startup - updater built Nov 21 2014 16:23:41
Looks like steam didn't shutdown cleanly, scheduling immediate update check
[2014-11-27 09:51:46] Checking for update on startup
[2014-11-27 09:51:46] Checking for available updates...
[2014-11-27 09:51:46] Download skipped by HTTP 304 Not Modified
[2014-11-27 09:51:46] Nothing to do
[2014-11-27 09:51:46] Verifying installation...
[2014-11-27 09:51:46] Performing checksum verification of executable files
[2014-11-27 09:51:47] Verification complete
Requested Force create but SharedObjectMutex already created
Forced create but already created for SharedObjectEvent
Forced create but already created for SharedObjectEvent
Error: OpenGL GLX context is not using direct rendering, which may cause performance problems.


For more information visit [https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457](https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457).
Running Steam on ubuntu 14.10 32-bit
STEAM_RUNTIME has been set by the user to: /home/bravewolf/.steam/ubuntu12_32/steam-runtime


I would really like to get this whole thing figured out and am worried I have some other major errors with my upgrade. If it helps, I could not install steam through Software Center. It would show up start to install then hang and free, turn dark and I would have to Force close it. Hopefully you guys can Help me figure out what is going on.

---

### Post by R33D3M33R on 2014-11-28
Try deleting these files: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

---

### Post by xfearxnxloathing on 2014-11-28
I wonder why I couldn't find this answer when I searched the forums.. Anyway, this worked for me, I just followed the commands for 14.10. Cheers, mate!!

---

