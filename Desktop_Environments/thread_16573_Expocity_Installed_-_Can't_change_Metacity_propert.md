---
title: "Expocity Installed - Can't change Metacity properties ?"
date: 2005-02-22
forum: Desktop Environments
---

### Post by nico1278 on 2005-02-22
I've installed Expocity on Warty, downloaded the sources from the official site and than compiled it. Works just fine. But during installation the metacity package for the windows borders has been changed. I can't figure out how to restore my favorite Myst wondows borders. Can't do it from themes menager. Any sagestions? Thks.

---

### Post by kassetra on 2005-02-22
[QUOTE=nico1278]I've installed Expocity on Warty, downloaded the sources from the official site and than compiled it. Works just fine. But during installation the metacity package for the windows borders has been changed. I can't figure out how to restore my favorite Myst wondows borders. Can't do it from themes menager. Any sagestions? Thks.[/QUOTE]

Yes, you can try doing it this way:
1. launch gconf-editor:
Applications->System Tools->Configuration Editor
2. In the tree on the left, go to apps->metacity->general
3. Edit the value of the line that starts with "theme" by clicking on the name of the theme currently in use.
4. Type in the theme name you want to use (this is an exact name, so you might want to look in /usr/share/themes for the theme you want, and then make sure it has a metacity directory)
5. Click in the Key Documentation to "set" your changes.
6. Close the editor.  :)

---

### Post by nico1278 on 2005-02-22
Doesn't work.... May be there is a metecity config file..... Realy strange....

---

### Post by kassetra on 2005-02-22
[QUOTE=nico1278]Doesn't work.... May be there is a metecity config file..... Realy strange....[/QUOTE]

1. You have to be really precise in the name you type in the gconf-editor, it has to match the name that the theme calls itself, usually the directory name in /usr/share/themes.

2. What version of metacity are you running?

---

### Post by nico1278 on 2005-02-22
1) That's what I did, tried with /usr/share/themes/Myst, then /usr/share/themes/Mist/metacity-1 but no effect.

2) The version of metacity is the default one for Warty, I thinks it is 2, but not so sure.

---

### Post by nico1278 on 2005-02-22
1 Doesn't help. Tried /usr/share/themes/Mist, then /usr/share/themes/Mist/metacity-1 but no effect :-(

2 Metacity version is the default one for Warty, i think it is 2, but may be I'm wrong.

---

### Post by kassetra on 2005-02-22
[QUOTE=nico1278]1 Doesn't help. Tried /usr/share/themes/Mist, then /usr/share/themes/Mist/metacity-1 but no effect :-(

2 Metacity version is the default one for Warty, i think it is 2, but may be I'm wrong.[/QUOTE]

Oh!  No, just type "Mist" in for the theme name.  :)

---

### Post by nico1278 on 2005-02-22
OK , didn't get you the 1 time, sorry. But anyway it wont work, this was allready the value of the string, that's why I thought I should enter the path, as stupid as it seems. Actually changining the themes in theme menager changes olso the value of the sting , but all I got is the same window boardering...

---

### Post by kassetra on 2005-02-22
[QUOTE=nico1278]OK , didn't get you the 1 time, sorry. But anyway it wont work, this was allready the value of the string, that's why I thought I should enter the path, as stupid as it seems. Actually changining the themes in theme menager changes olso the value of the sting , but all I got is the same window boardering...[/QUOTE]

Most likely then, expocity is controlling metacity's theming... you might want to see if there is an expocity theme value to change in the gconf-editor...

let me see if I can find out some more here...

---

