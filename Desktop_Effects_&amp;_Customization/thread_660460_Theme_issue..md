---
title: "Theme issue."
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by Roasted on 2008-01-06
Two things.

A: Randomly, the titles of the applications I have open at the bottom of the screen will change their boldness. Sometimes they are bold, other times they are not. It varies, and I have no clue why. How can I change it? All of my fonts in appearance are the same - Sans 10 bold.

B: I have a theme, named Chrome, I really like. However, for some reason it wants to use the Mac window border. I don't want to use the Mac window border, however in the window border selection list, I don't see Chrome listed. WTF?
 

Emerald is not installed.

---

### Post by NilsE on 2008-01-06
There is some potential that the theme is over writing the fonts so check in the gtk file within the /usr/share/themes folder of the theme you are using.

Not all themes set all aspects of a theme. See if the chrome theme has a metacity folder.  Since you said no window frames show up it likely does not have one.

---

### Post by ryanVickers on 2008-01-06
fonts issue - no idea...

no window border issue - perhaps it didn't come with a window border theme? :rolleyes:

---

### Post by Roasted on 2008-01-06
I don't see why it wouldn't. I check the preview picture each time before I download. The chrome one in the preview had a specific window border that definitely wasn't mac. I can adjust my window border to anything... chrome just isn't listed. Mac just happened to come on first thing.

I'd check the themes folder but I'm on my XP laptop. I'll check my ubuntu rig later.

---

### Post by NilsE on 2008-01-07
> **Roasted said:**
> I don't see why it wouldn't. I check the preview picture each time before I download. The chrome one in the preview had a specific window border that definitely wasn't mac. I can adjust my window border to anything... chrome just isn't listed. Mac just happened to come on first thing.

I'd check the themes folder but I'm on my XP laptop. I'll check my ubuntu rig later.

A lot of times when people post the theme they do a complete screenshot even though they are not posting all pieces of the theme.  

You probably know this already (took me awhile to figure it out) but if it helps while you are looking, in the Appearance wizard here are the descriptions:

Controls - are the GTK themes  such as buttons, sliders, panels, menus etc..  
Window Borders - Metacity themes are the  borders (top, sides, bottom), close button etc., 
Icons -  are obviously icons. and 
Pointers - are the mouse pointers.

Controls and Window borders are in the themes folder - /usr/share/themes/THEME NAME 

Icons and pointers are in the icons folder - /usr/share/icons/ICON AND/OR CURSOR THEME NAME

They can also be installed in your home drive but it is more efficient to keep them all in the /usr/share/ folders. However, if you use pieces of different themes and do a save as it will save the name and links to it in your home folder under .themes

---

