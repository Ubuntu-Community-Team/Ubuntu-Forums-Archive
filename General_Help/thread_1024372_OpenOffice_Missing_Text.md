---
title: "OpenOffice Missing Text"
date: 2008-12-28
forum: General Help
---

### Post by mperedithe on 2008-12-28
Hey Everyone,

I just upgraded to Intrepid from Ubuntu 8.06 LTS.  So far it's been great.  I have two issues that I need help with. 

First, the openoffice products do not show text in the menu bars or on the spread sheet.  I have upgraded to openoffice 3.0 but that didn't fix the problem.  I can type and text shows up on the page/spreadsheet/presentation but no text in the menu bars.

Second, I have installed the "Ubuntu-It" app for firefox but the pages it takes me too are all in french or italian.  How can I get it to send me to english pages?  

Anyhow, thanks for the help--you all have been wonderful with past issues.
Marc

---

### Post by abn91c on 2008-12-28
you may need to remove this file sudo apt-get openoffice.org-gnome to fix OOo 3.0
for firefox go to the toolbar, then click on the edit>preferences>content tab>languages

---

### Post by HereInOz on 2008-12-28
If the menu bar just displays small lines, rather than text, this will fix it:

Start Open Office writer
Click on the seventh line across (the Tools menu)
Click on the last line in the drop down box (Options)
Arrow down 3 times - which gets you to the View section - it will say View up in the title bar.
Click on all the ticks in this section to remove them.

This should restore your menu text.

---

### Post by HereInOz on 2008-12-28
Sorry, forgot to mention - press Enter after you have removed all the ticks.

---

### Post by mperedithe on 2008-12-29
Thanks HerelnOz your advice worked great.  However, as I have been playing around tonight I have discovered to my horror that the symptoms are worse than I realized.  While I do now have the text in the menu bars for OpenOffice.  I do not have the text in the menu bars for several other applications, such as Kaffeine and Eqonomize.  This doesn't seem to be affecting all KDE apps but it does seem to target office and sound and video apps.

I also found and removed the openoffice.org-gnome but it hasn't changed anything.

---

### Post by mperedithe on 2008-12-31
Quick update on the missing text.  Still no luck in correcting the problem.  Wine is also missing text throughout all parts of the configuration utility.

---

### Post by ktechman on 2009-02-02
Thank you HereInOz.

         Ktechman

---

