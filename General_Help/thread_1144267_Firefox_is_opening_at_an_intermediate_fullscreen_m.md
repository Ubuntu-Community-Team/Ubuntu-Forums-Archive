---
title: "Firefox is opening at an intermediate fullscreen mode"
date: 2009-04-30
forum: General Help
---

### Post by geebob on 2009-04-30
I already asked this question over at Mozilla's support forum.  I have not gotten any solutions to my problem yet.

When I open firefox, it covers the complete desktop obscuring the lower and upper pannels.

This is not the full blown fullscreen. I know this because the toolbar and the bar with "file, edit, view, etc" is visible. The only way for me to get it out of this mode is for me to tap F11 twice. The first time I tap it, it goes into the full blown fullscreen mode, and the second puts the browser back to the normal size allowing me to see the upper and lower panels of my OS.

If you aren't sure what I'm talking about, I posted screenshots at the following link. 

[https://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=340192&forumId=1]("https://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=340192&forumId=1")

---

### Post by emarkay on 2009-04-30
You are still using 7.04 (confirm)? What type of PC, what graphic card, what version of FF?

---

### Post by geebob on 2009-04-30
Firefox is 3.09, Ubuntu is 8.10.  I have a Dell Inspiron 1501. I believe my card is an 1150 ATI Radeon Xpress

---

### Post by olskar on 2009-04-30
Are you using compiz? I think it might be a known compizbug if you do

---

### Post by geebob on 2009-04-30
I am using compiz and the compiz settings manager.

---

### Post by olskar on 2009-04-30
> **geebob said:**
> I am using compiz and the compiz settings manager.

Try disabling compiz by deactivating desktop effects and see if the problem remains

---

### Post by sumpm1 on 2009-04-30
I had this problem recently in 8.10 and solved it using the about:config address in Firefox, let me check, I'll be right back.

Okay, type about:config into the address bar in Firefox and hit enter. Search for browser.fullscreen.autohide and be sure to set it to false.

You may also try changing a "legacy support" setting in Compiz, search for that if my suggestion didn't work.

---

### Post by |Mitch| on 2009-04-30
Hit F11 twice and then hit the maximize button, close Firefox and when you restart firefox everything should be back to normal

---

### Post by |Mitch| on 2009-04-30
double-post

---

### Post by geebob on 2009-04-30
Thanks for all the suggestions.  I started with Mitch's suggestion first since it was the most simple and it worked.

---

