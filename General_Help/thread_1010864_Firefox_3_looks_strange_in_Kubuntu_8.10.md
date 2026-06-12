---
title: "Firefox 3 looks strange in Kubuntu 8.10"
date: 2008-12-14
forum: General Help
---

### Post by QBB on 2008-12-14
Hi there,

After I screwed up Ubuntu, I recently installed Kubuntu 8.10 (default installation) with some additional applications like Firefox 3. And somehow FF3 looks strange to me. (see attachment)

Some of the things I noticed:
- The backgroundcolor of checkboxes and radiobuttons are grey while the website's bgcolor is different (i.e. white; see attachment)
- Checkboxes do not always appear completely but appear when I hover my mouse over the checkbox
- When I hover my mouse over some tabs they loose their borders (see attachment)

I played around with KDE-themes and with FF-themes in order to have it fixed. I even restored my old userprofile to see if that fixes it. None of it worked out well.

In some forum I had to set the following settings in about:config:
browser.display.use_document_colors: TRUE
browser.display.use_system_colors: FALSE

They were allready set correctly.

I attached a screenshot where you can see the backgroundcolor of the radiobuttons and the screwed borders of taps (I opened 3 tabs).

Since I'm no [k]ubuntu-guru I have no idea where to look. Any suggestions???

---

### Post by shadowplay on 2008-12-19
I can confirm this. Looks this  way for me immediately after re-install and update.

---

### Post by jay li on 2008-12-19
Did you install different theme?

---

### Post by knowledgeispwr on 2008-12-20
This [thread]("http://forum.kde.org/how-to-integrate-firefox-into-kde-t-17786.html") on KDE's forums has good tips on how to integrate FF3 into KDE 4.x  You can get it looking pretty decent.

---

### Post by QBB on 2008-12-22
@Jay li: Yes, I tried several themes for FF3 as well as KDE itself.

---

### Post by QBB on 2008-12-22
> **knowledgeispwr said:**
> This [thread]("http://forum.kde.org/how-to-integrate-firefox-into-kde-t-17786.html") on KDE's forums has good tips on how to integrate FF3 into KDE 4.x  You can get it looking pretty decent.
Thank you! I followed the instructions and within several minutes I got it working! :D

Thanks!

---

