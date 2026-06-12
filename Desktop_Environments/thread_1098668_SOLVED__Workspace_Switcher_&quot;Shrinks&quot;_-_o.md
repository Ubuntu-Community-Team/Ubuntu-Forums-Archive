---
title: "SOLVED:  Workspace Switcher &quot;Shrinks&quot; - only occupies the top half of the space"
date: 2009-03-17
forum: Desktop Environments
---

### Post by N00bB00b on 2009-03-17
I had a problem earlier where my workspace switcher applet (virtual desktop for those of us who came from Wind0Ze) would seem to "shrink".

No matter how many workspaces I had set up, there was always an empty row beneath it.  So, for example, if I had a 3x2 setup (three columns, two rows), the display of those would occupy the top half of the workspace switcher (so each row would get about a quarter of the height of the space).  The bottom half was taken up by a single monolithic cell that was inaccessible.

Have No Fear!(TM).  Like everything else, there is a fix, and it's pretty easy.

1) We're going to enable the Configuration Editor (similar to Wind0Ze's Registry Editor):
   a) Navigate through the following menus:  System->Preferences->Main Menu.
   b) Click on "System Tools" (it may or may not be italicized).
   c) Put a check next to "Configuration Editor".

2) Open the Configuration Editor - navigate to the main menu->System Tools->Configuration Editor

3) Please be careful, you're messing around with powers that you cannot understand.

4) Type ctrl-f for "find".  Copy and paste the following into the box: /apps/panel/applets/workspace_switcher_screen0/prefs, and click on "Find"

5) In the bottom part of the split, click on the text (/apps/panel...)

6) Above, in the right panel, you will see a "num_rows" property.  Set it to 1.

7) Put a thanks in this thread.

---

### Post by AndrewMc on 2009-03-27
Thanks!

That's been bugging me for a while. I wasn't able to fix it exactly from your instructions, but I pointed me in the right direction where I found an odd entry called "applet_5" that didn't have any settings in it. A bit of (careful) prodding around and now it works.

---

### Post by Ein2015 on 2009-04-15
Thanks!

Worked perfectly!

---

### Post by Vermind on 2009-04-28
Thanks, I just had this issue with Jaunty, fixed with your help.

---

