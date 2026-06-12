---
title: "File Types and Programs preference tool?"
date: 2005-02-05
forum: Desktop Environments
---

### Post by jnoreiko on 2005-02-05
GNOME Nautilus help mentions a preference tool that I can't find: the File Types and Programs preference tool.

Where is it? How do I open it?

---

### Post by Davepet on 2005-02-05
I'm still stumbling through my system, but check out: "computer"> "desktop preferences">"preferred applications"

Lets you set default browser, emial,text editor,& terminal

Also, from Nautilus help:
----------------------------------------------------------------------
To modify the actions associated with a file or file type, perform the following steps:
1-In the view pane, select the file for which you want to modify an action. If you want to modify an action associated with a file type, select a file of that type.

2-Choose File &#8594; Open With. Perform either of the following steps:

       Choose Other Application. An Open with Other Application dialog is displayed.
       Choose Other Viewer. An Open with Other Viewer dialog is displayed. 

3-From the table in the dialog, select the application or viewer for which you want to modify the behavior.
4Click on the Modify button. A Modify dialog is displayed. The following table describes the options on the Modify dialog:
--------------------------------------------------------------------------------

So sounds like the tool is actually part of Nautilus. I'm having trouble c&p from yelp so read the rest at:  A tour of the GNOME Desktop>Nautilus File Manager>Assigning actions to files.

Hopw that helps

Dave

---

### Post by Davepet on 2005-02-21
Update:
I was digging around last night looking for a way to change a file association & discovered that the file preferences tool *is* a feature on standard Gnome/Nautilus systems, normally located in the desktop preferences submenu.

No idea if it's just a menu entry that was removed by the Ubuntu folks, or if the app itself has been entirely removed.

It would sure be nice to find, since there are som .dat files in a mozilla folder that my system thinks are mpegs.

Dave

---

### Post by piedamaro on 2005-02-21
[QUOTE=Davepet]Update:
I was digging around last night looking for a way to change a file association & discovered that the file preferences tool *is* a feature on standard Gnome/Nautilus systems, normally located in the desktop preferences submenu.

No idea if it's just a menu entry that was removed by the Ubuntu folks, or if the app itself has been entirely removed.

It would sure be nice to find, since there are som .dat files in a mozilla folder that my system thinks are mpegs.

Dave[/QUOTE]
 There is no "file association" in gnome. It has been removed since gnome-2.7.
Just use: right click on the file/open with

---

### Post by Davepet on 2005-02-21
I tried that, but my system is firmly convinced that .dat files are mpeg's. Even puts the movie reel icon on them. The open with dialog won't let me change the default action, & it won't let me change what the system thinks .dat files are.

gedit can open the files, but all the open with dialog says is:

"Open pluginreg.dat & other files of type "MPEG Video" with:'/usr/bin/gedit'  "

clearly not what I wanted, & even if it were, it still doesn't become the default action.

any suggestions?

Dave

Edit: OK, I can change the default action with the "properties" dialog, but I still want to  make the system realize that .dat files are not mpeg's

---

