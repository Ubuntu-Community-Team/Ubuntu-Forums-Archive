---
title: "Unable to Click Outside Current 'Layer'"
date: 2010-08-11
forum: Desktop Environments
---

### Post by klco on 2010-08-11
Hi all thanks for the help,

I am having an extremely frustrating problem with my Ubuntu 10.04 AMD64 installation.  Quite often when I restart my desktop the mouse seems to be unable to click outside the current 'layer'.  

For example if I am in FireFox I can only click on the URL bar or the buttons there or inside the body of the page.  But one I click in one, I can't click outside it.

Often I can only click on the gnome menus, but not inside applications when I open them.  There doesn't seem to be a rhyme or reason to the problem and I have tried using different Visual Effects settings, different mouses, searching online for solutions, etc.  

Just a minute ago when I tried to copy my xorg.conf, I pressed Alt+F2 (since I can't click outside FireFox), dumped my xorg.conf to the terminal and when I tried to scroll the terminal to grab all of the output it scrolled FireFox and when I typed the text showed up in the terminal.

I see about attaching that to the ticket when I can, but in the meantime if anyone could help I would really appreciate it.

---

### Post by MatthewAdams on 2010-08-11
Do you mean you can't move the cursor outside of the "layer", or the cursor can move but clicking has no effect?

I'd advise you to CAREFULLY examine your settings in regards to Window Behavior, or Windows, or anything similar to that (Should be under System --> Preferences or System --> Administration). 


In Kubuntu, there's a setting called "click raises active window"...if unchecked, I would think this would recreate the same problem that you are having now, i.e, clicking something has no effect on if that window becomes active.

---

### Post by klco on 2010-08-11
I mean the latter.  I can move the mouse, but clicking seems to have no effect.  I tried as ahoy suggested and under System / Preferences / Windows there was an option 'Select windows when mouse moves over them' but nothing about clicking on the windows.  I did try changing that with no effect.

---

### Post by MatthewAdams on 2010-08-11
This is very unfortunate. It seems like the exact setting you need is available in Kubuntu. On Ubuntu, I can't seem to find anything at all. I apologize.

---

