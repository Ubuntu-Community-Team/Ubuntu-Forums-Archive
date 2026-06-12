---
title: "GEdit: Change current line background color"
date: 2007-03-29
forum: Desktop Effects &amp; Customization
---

### Post by fnando on 2007-03-29
Hi,

How can I change the current line background color in GEdit editor? I read that you have to do this in your current theme but I don't know which file I need to modify and what I need to put in it.

Can someone guide me on this?

Thanks.

---

### Post by smbm on 2007-03-29
Hi

Try opening gedit then go to edit, preferences and check the highlight current line box. 

Hope this helps

EDIT:

Sorry I just re-read your post and I seem to have answered an entirely different question. Sorry.

If I think of anything I'll let you know.

---

### Post by merlyn on 2007-03-30
Open Gedit.

Goto Edit / Preferences, select the fonts and colours tab.

Unselect 'use default theme colours'.

Click on 'Background colour'.

Go crazy with the Gnome colour selector.

---

### Post by fnando on 2007-03-30
> **merlyn said:**
> Open Gedit.
Click on 'Background colour'.


This option changes the page background color. I want to set the current line background color. This option isn't available on Preferences.

---

### Post by fnando on 2007-03-30
I attached a image to illustrate what I'm saying.

---

### Post by merlyn on 2007-03-30
Try the selection option and see how that works out.

Cheers.

---

### Post by fnando on 2007-04-02
> **merlyn said:**
> Try the selection option and see how that works out.

This affects only the selected text. Not the current line. :(

I still think that the only to change this is tweaking the gtkrc theme file.

---

### Post by KClaisse on 2007-06-09
Did you ever solve this? I have my background black and when I use that highlight line feature it washes out my font completely. 

[img]http://img352.imageshack.us/img352/8935/washouthq2.jpg[/img]

---

### Post by tc101 on 2007-10-30
After I upgraded to ubuntu 7.10, the "fonts and colors" tab under edit/preferences changed.  It now only lets me use pre assigened color schemes.  Is there some way to change this back?  If not, how do I create my own color scheme?

---

### Post by napzilla on 2008-01-09
The schemes are written in XML. Place your custom theme in ~/.gnome2/apps/gedit/styles/. 

If you don't feel like starting from scratch, you can copy and modify one of the existing themes in /usr/share/gtksourceview-2.0/styles/ or download  [ATTACH]55777[/ATTACH], which is the one I use.

Brian

---

### Post by sur on 2008-02-03
I used the current_line plugin for the same... its works great!!

Issue these commands from the consol

1) cd  ~/.gnome2/gedit/plugins
2) svn co [http://svn.simplesideias.com.br/general/gedit/plugins/current_line/](http://svn.simplesideias.com.br/general/gedit/plugins/current_line/)


Now restart your gedit. In Edit -> Preferences 
1) In View tab, check the checkbox to hilghlight current line
2) In Pligins tab, activate the current_line plugin, select the plugin from list and click configure plugin to add foreground and background colors for current line.

Thanks!!

--
sur
[http://expressica.com](http://expressica.com)

---

