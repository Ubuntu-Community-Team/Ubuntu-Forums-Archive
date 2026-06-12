---
title: "[SOLVED] Firefox opens strangely"
date: 2008-11-04
forum: Desktop Environments
---

### Post by fballem on 2008-11-04
I am running ubuntu 8.10 64-bit. I've just noticed that Firefox is opening a little strangely.

Firefox-Expected shows how I would expect Firefox to open - please note that the ubuntu menu is at the top, and there are both top and bottom panels.

Firefox-Actual shows what actually happens. Firefox opens and there are no ubuntu panels. It looks like Firefox is taking over the entire desktop. The only way to put them back is to tap F11 twice (once to go full screen, the second time to return). On the return, I get my top and bottom panels back.

Any ideas on what is causing the problem, and how to fix it, would be most helpful.

Thanks,

---

### Post by newt110 on 2008-11-04
Disabling 'Ubuntu Firefox Modifications 0.6' in Tools/ Add-ons solved same problem for me. I was using f11 before that. I think there is a bug report for this but I have lost track of it. The problem is reported elsewhere as panel/ task-bar problems by various members.

---

### Post by fballem on 2008-11-04
> **newt110 said:**
> Disabling 'Ubuntu Firefox Modifications 0.6' in Tools/ Add-ons solved same problem for me. I was using f11 before that. I think there is a bug report for this but I have lost track of it. The problem is reported elsewhere as panel/ task-bar problems by various members.

Thanks for the suggestion, but the ubuntu Firefox modification extension is disabled and I still have the problem.

---

### Post by fballem on 2008-11-04
Solved myself:

1. Opened my home folder (Places > <home>) <home> is replaced by my username
2. Unhid folders (Ctrl-H)
3. There is a folder .Mozilla. I renamed the folder to backup.Mozilla
4. Started Firefox. This started with new settings, including clearing whatever it was that was causing my problem.

Before I did this, I made a backup of my bookmarks from Firefox (Bookmarks > Organize Bookmarks > Import and Export > Export HTML.

Once I cleaned out Firefox, I restored my bookmarks and deleted the backup folder that I mad in step 3.

---

