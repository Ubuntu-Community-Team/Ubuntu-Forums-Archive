---
title: "Firefox font only"
date: 2005-04-08
forum: Desktop Environments
---

### Post by vvu on 2005-04-08
Can anyone tell me or point me to where I can change the menu font size for Firefox on the new Hoary 5.04 Kubuntu release?  I was using the Preview 5.04 and the font was small - I did a format and reinstalled the FINAL cleanly and the font is large - ONLY the menu.  I took care of the system wide fonts by installing by Windows fonts - the only that did not take the system wide fonts were Firefox and Kynaptics - anyone know why and where I can change this behavior?


Thanks.

---

### Post by vvu on 2005-04-08
Okay, quickly found out the solution to my MENU size issue (not the actual text on the web sites).

Go to [B]/home/YOURNAME/.mozilla/firefox/svkuol11.default/chrome
[/B]
and create a file called **[COLOR=DarkRed]userChrome.css[/COLOR]**

Just add this into that file and save - close Firefox and restart - this _ASSUMES_ you have ARIAL as a font in your system (otherwise choose your own font).


/* Make menus big, pretty and readable (like the old SGI look):
 * menubar isn't used after 12/19 builds, but is needed for NS6;
 * the rest are for post-12/19
 */
menubar, menubutton, menulist, menu, menuitem {
  font-family: arial !important;
  font-style: normal !important;
  font-weight: normal !important;
  font-size: 3mm !important;
}

/* Single line text fields */
input {
  /* Set font size and family of text fields */
  font-family: clean !important;
  font-size: 12px !important;
}

/* Shrink tab titles by 20% */
.tabbrowser-tabs .tab-text {
  font-size: 80%;
  font-style: normal !important;
}


Good Luck!

---

### Post by c_dog on 2005-04-09
The easiest way to change Firefox's menu font size in to go into the Edit>Preferences>General>Fonts&Colors and set the Display resolution to more closely match the dpi of your monitor. IFCR the pull-down give you 72 dpi,  96 dpi, or other. If you choose 'other' Firefox will display a line the screen that you can measure with a ruler it'll convert it for you to dpi.

---

### Post by Cool_dude_Prav on 2005-04-09
Wow.. Great info..

Tnx man!!!

---

### Post by vvu on 2005-04-09
Going into the Preferences Section to fix the FONT setting does NOT always work - trust me, I spent ten minutes trying to make the changes the easiest way possible using the GUI.  I found out the solution to Firefox issue because it IS documented in the Mozilla.ORG pages.  They talked about the two .CSS files as the way to control these behaviors.  Also your method does not take into account EVERY possible features you can changes about Firefox.  My example shows fonts and tab sizes whereas the MOZILLA.ORG pages describes tab colors, Bookmarks, etc...much more.  And you can not do that just by going to the Preferences Section of the GUI.

More here - [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html) - many more pages.

---

