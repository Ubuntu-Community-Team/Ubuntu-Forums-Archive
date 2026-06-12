---
title: "Getting a Greek font?"
date: 2005-08-28
forum: Desktop Environments
---

### Post by naked on 2005-08-28
How can I do this?  I search in synaptic for 'greek' and 'font' and found some language packs for gnome (el).  But I just need to be able to use a greek font in openoffice.

?

Thanks!

---

### Post by ekravche on 2005-08-28
I haven't actually tried this, but if you go to System->Preferences->Keyboard. Then when the Keyboard preferences windows appears click on the Layouts tab and then click the add button, you should be able to add greek. You'll also need to add the Keyboard indicator applet. You can do this by right clicking on the top panel. Then selecting add to panel, and from the list of applications select Keyboard indicator. After you've done these steps you should be able to see the currently enforced language on the panel above. Afterwards whenever you need to switch just click on the keyboard indicator and select the preferred language.

---

### Post by naked on 2005-08-29
[QUOTE=ekravche]I haven't actually tried this, but if you go to System->Preferences->Keyboard. Then when the Keyboard preferences windows appears click on the Layouts tab and then click the add button, you should be able to add greek. You'll also need to add the Keyboard indicator applet. You can do this by right clicking on the top panel. Then selecting add to panel, and from the list of applications select Keyboard indicator. After you've done these steps you should be able to see the currently enforced language on the panel above. Afterwards whenever you need to switch just click on the keyboard indicator and select the preferred language.[/QUOTE]
 &#964;&#951;&#945;&#964; &#962;&#959;&#961;&#954;&#963; &#966;&#953;&#957;&#949;

That works fine.  I would however rather just be able to install a greek font to use in openoffice.

I appreciate your help, but anyone else?

&#955;

---

### Post by mcrosmar on 2005-08-29
[QUOTE=naked]&#964;&#951;&#945;&#964; &#962;&#959;&#961;&#954;&#963; &#966;&#953;&#957;&#949;

That works fine.  I would however rather just be able to install a greek font to use in openoffice.

I appreciate your help, but anyone else?

&#955;[/QUOTE]

You can install the MS core fonts: sudo apt-get install msttcorefonts
[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafonts) 

You must select "Greek Polytonic" layout to keybord preferences.

---

### Post by nightfrost on 2006-10-22
I've been trying to get polytonic Greek to work for a year now under linux (more or less), but have failed miserably. I really don't understand why it's not possible. A font that should work fine for polytonic is MgOpenCanonica (which is included in Ubuntu by default). I've been selecting polytonic greek  through the keyboard preferences and, in OpenOffice for example,the Greek letters show up as they should. But it is impossible to get all the diacritics working. The problem is there even when using X input method (GTK_IM_MODULE=xim)... 

Any idea what might be going on?

---

### Post by madmetal on 2006-10-22
i hope this site helps with polytonic problems..
[http://tlgu.carmen.gr/](http://tlgu.carmen.gr/)

greek :-({|=
:-D

---

### Post by nightfrost on 2006-10-23
Thanks alot! That howto was great. Everything seems to work now. I can finally get rid of my Windows installation at last! I've been only keeping it around in order to write Greek diacritics. What a relief...

(however, it just works when I start open office from the command line for some reason. When I start from the menu, through the quickstarter, or through the deskbar applet &#8594; no diacritics).

---

