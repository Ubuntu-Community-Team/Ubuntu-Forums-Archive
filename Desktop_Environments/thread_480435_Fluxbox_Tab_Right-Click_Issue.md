---
title: "Fluxbox Tab Right-Click Issue"
date: 2007-06-21
forum: Desktop Environments
---

### Post by DonnieP on 2007-06-21
Running repository fluxbox (RC2) on feisty.  The fluxbox documentation I've read says I ought to be able to right-click a fluxbox tab and get the root menu to select an app rather than the window menu you get when you right-click a title bar (shade, stick, etc.).  The point, according to the documentation, is that when you right-click a tab and select an app this way, the selected app automagically joins the group with the app you right-clicked from.  Well . . . when I right-click a tab I just get the window menu (shade, stick, etc.) rather then my root menu.  Why?

---

### Post by Happy_Man on 2007-06-21
Sorry if I seem rude... but did you add other programs using middle-click drag first?

---

### Post by DonnieP on 2007-06-21
Yes - middle-click drag works fine.  I can group apps with the mouse - I just can't automatically group them by running them from a right click of an existing tab.  Also I've found (possibly related?) that the windowMenu resource in init doesn't work for me either.  I set up a custom windowmenu and referenced it in it with the windowMenu resource, but all I get on right-clicking a window titlebar is the default menu (stick, shade, etc.)

---

### Post by kerry_s on 2007-06-21
I never seen that kind of tab feature your talking about, i have always created a group file and put what i wanted to group automaticaly. Can you provide a link to the doc your looking at?

Any changes in the fluxbox files, you need to click on restart.

for instance, here is my groups:

emelfm xterm mousepad
opera dillo


don't forget to click on restart after you add the apps and group of apps, you want to auto group.

---

### Post by DonnieP on 2007-06-21
Thanks - yes, I've been careful to restart after making changes.  (In fact I've exited fluxbox altogether several times and have also tried reinstalling fluxbox.)  Here's one of the references to the business about right-clicking the tab.  I haven't tried the groups and apps approach yet because this reference says that the right-clicking method might mess up the groups approach.  Also I was looking for something a bit more on-the-fly.

[http://fluxbox.org/docbook/en/html/x242.html]("http://fluxbox.org/docbook/en/html/x242.html")

It's toward the bottom of the page - Autogrouping from Tabs.

---

### Post by DonnieP on 2007-06-21
Also, this pdf of a magazine article also mentions the right-click of the tab method to open an app into a tabbed group:

[http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.linux-magazine.com%2Fissue%2F43%2FFluxbox_Window_Manager.pdf&ei=ogF7RpGII5jMgwScr4jdBQ&usg=AFQjCNGwA5PfS-FM8grszQV7-YCTGisIEw&sig2=q7pPefa4p0GKOFdmZZm8KQ]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.linux-magazine.com%2Fissue%2F43%2FFluxbox_Window_Manager.pdf&ei=ogF7RpGII5jMgwScr4jdBQ&usg=AFQjCNGwA5PfS-FM8grszQV7-YCTGisIEw&sig2=q7pPefa4p0GKOFdmZZm8KQ")

---

### Post by kerry_s on 2007-06-21
I've don't know what to tell you, i've never seen that option, maybe it's something that has to be specially compiled in.

wait for red squirrel to chime in, he compiles fluxbox regularly, maybe he will know.

---

### Post by yabbadabbadont on 2007-06-21
I think they dropped that feature a long time ago.  Most of the online docs haven't been updated in a long time.  I generally read through the Changelog file to find out about new/dropped features.  Sometimes it is the only way to learn how to configure a new feature.  I'll look through the changelog of my svn version and see if I can find anything about tab autogrouping.

Edit: By the way, I tried getting the root menu like you described in fluxbox 1.0rc3 SVN Revision: 4937 and it just gives the normal window border right-click menu.

Edit2: It looks to me like that feature was added, then replaced with the groups file functionality.  (a long time ago too)
```
*02/08/11:
   * New menu items (Thanks Cosmic Flo)
   * Added Autogrouping
     * Add this line: session.groupFile: ~/.fluxbox/group
       to the file ~/.fluxbox/init and edit ~/.fluxbox/group
       Groupfile format:
       There is one group for each line in the file
       and you just type the instance name of the program
       to be grouped. Ex:
       Navigator nedit
       xterm
       This will make two groups, one with netscape and nedit
       and one with xterm.
       The new window will only group itself to other windows
       on the same workspace and to the last window that was
       focused.
*02/08/10:
   * French translation in fluxbox-generate_menu (Thanks Cosmic Flo)
*02/08/04:
   * Fixed doxygen comments and minor clean up.
*02/08/02:
   * autogrouping-from-tab patch (Thanks Steve Cooper)
     This will allow you to popup the root menu, if you right click,
     and select an application and it'll start grouped to the tab.

```

---

### Post by DonnieP on 2007-06-21
Thanks for checking into it.  At least it doesn't sound like I've inadvertently screwed something up in my installation.  That was my fear.

---

