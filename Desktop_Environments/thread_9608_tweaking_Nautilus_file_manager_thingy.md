---
title: "tweaking Nautilus file manager thingy"
date: 2004-12-29
forum: Desktop Environments
---

### Post by Datchew on 2004-12-29
Been using linux for almost 4 whole days now.
What a BIG difference from Microsoft stuff. 

Anyway, so far so good, got it installed, updated, fixed backgrounds and splash and login screen setup due to outstanding help on this board. 

Now, however, i can't seem to figure out how to change things in the file manager (Nautilus?)  I want to make it (GASP) kinda like windows explorer where i can see a menu of folders on the left and subfolders on teh right so i can browse around without opening up a new window everytime i try to open a new folder. 
Any ideas?  Trying to browse and ending up with 50 stacked windows is getting REALLY old.  

Please give me the simple stuff.  I'm a HUGE newB.  
Thanks,. :mrgreen:

---

### Post by Smeggy on 2004-12-29
[QUOTE=Datchew]Been using linux for almost 4 whole days now.
What a BIG difference from Microsoft stuff. 

Anyway, so far so good, got it installed, updated, fixed backgrounds and splash and login screen setup due to outstanding help on this board. 

Now, however, i can't seem to figure out how to change things in the file manager (Nautilus?)  I want to make it (GASP) kinda like windows explorer where i can see a menu of folders on the left and subfolders on teh right so i can browse around without opening up a new window everytime i try to open a new folder. 
Any ideas?  Trying to browse and ending up with 50 stacked windows is getting REALLY old.  

Please give me the simple stuff.  I'm a HUGE newB.  
Thanks,. :mrgreen:[/QUOTE]
 Computer Menu > Desktop Preferences > File Management > Behaviour Tab > Tick "Always open in browser windows"

This will make Nautilus show a sidebar and use one window.  Then use the drop down list in the sidebar on the left to select "Tree".

Hope that helps.

---

### Post by mal on 2004-12-29
[QUOTE=Datchew]Been using linux for almost 4 whole days now.
What a BIG difference from Microsoft stuff. 

Anyway, so far so good, got it installed, updated, fixed backgrounds and splash and login screen setup due to outstanding help on this board. 

Now, however, i can't seem to figure out how to change things in the file manager (Nautilus?)  I want to make it (GASP) kinda like windows explorer where i can see a menu of folders on the left and subfolders on teh right so i can browse around without opening up a new window everytime i try to open a new folder. 
Any ideas?  Trying to browse and ending up with 50 stacked windows is getting REALLY old.  

Please give me the simple stuff.  I'm a HUGE newB.  
Thanks,. :mrgreen:[/QUOTE]
 There's an option in Nautilus Preferences to "always open browser" (or words to that effect).

However, before you do this you should read:

[http://www.bytebot.net/geekdocs/spatial-nautilus.html](http://www.bytebot.net/geekdocs/spatial-nautilus.html)

to get an uderstanding of how "spatial" mode is meant to work.  It's not as bad as it seems, once you get to know it.

Mal

---

### Post by Datchew on 2004-12-29
Smeggy, thanks much.
that was exactly what I was talking about.

Mal,  i'll take a look at that link. 
I appreciate it.

---

### Post by AndersAA on 2004-12-30
spatial is actually extreamly efficient once you get used to it.  Granted I had to force myself to use that only for about a week before I started liking it ;), can't live without it now though.

(I also use imwheel so I can use my forth mouse button to close active nautilus window)

---

### Post by CowPie on 2005-01-01
[QUOTE=Datchew]Been using linux for almost 4 whole days now.
What a BIG difference from Microsoft stuff. 

Anyway, so far so good, got it installed, updated, fixed backgrounds and splash and login screen setup due to outstanding help on this board. 

Now, however, i can't seem to figure out how to change things in the file manager (Nautilus?)  I want to make it (GASP) kinda like windows explorer where i can see a menu of folders on the left and subfolders on teh right so i can browse around without opening up a new window everytime i try to open a new folder. 
Any ideas?  Trying to browse and ending up with 50 stacked windows is getting REALLY old.  

Please give me the simple stuff.  I'm a HUGE newB.  
Thanks,. :mrgreen:[/QUOTE]
 Spatial is absolutely disgusting, don't worry you're not alone.  Read this if you want info on how it can be improved though (I would use it then!): 

[http://gnomesupport.org/forums/viewtopic.php?t=8570](http://gnomesupport.org/forums/viewtopic.php?t=8570)

---

### Post by poptones on 2005-01-01
The only problem I have with Nautilus is it is SOOOOO disgustingly slow when updating a view of a folder. Moving files is done ONE AT A TIME! If you have a folder with 2000 files and you just move twenty, it still takes an incredibly long time (I have measured more than five minutes). 

Remove file from display, redraw entire window; remove one more file, redraw display; remove one more file from pane, redraw...

This takes away a huge amount if usability from the entire concept. Why would you even want all your folders in view if it takes anything from five seconds to a minute for every single file moved because of the overhead? This I wish they would fix. When moving a lot of files just TURN OFF RENDER and refresh the pane only after redrawing the panel in a buffer. 

Other than that I love spatial mode. It can get cluttered until you get things repositioned, but you can prevent that just by clicking ANY folder and chooing "browse folder." Bingo, you're not in kansas anymore.

Spatial browsing + configurable scripts = any cool application you want. I have a template for all my image folders so they open up in the same place, same size every time. The "top" folder for them opens in another place. GQView opens in the little panel that's left. Movie files are similar, but different. Archives are completely different still. Total configurability. If I need to move around a lot of files I open a browser, other than that I have a few windows that "live" open on my desktop just about all the time. 

I do wish they would add the option in "browse" mode to "open spatial view." I'll probably get flamed for this yet a third time for bringing it up, but I don't know how one might do it with a shell script and I think this feature would help a lot of people see the great utility in it. That, and allow the right click "scripts" menu to become folder-aware (ie "add this script to the right click menu only in an MP3 folder...")

It's really hilarious how MS has been touting one new "invention" after another for the better part of a decade and still hasn't matched even the desktop power of  bash+gtk+zenity (much less the more "interactive" languages like python).

---

### Post by CowPie on 2005-01-04
[QUOTE=poptones]The only problem I have with Nautilus is it is SOOOOO disgustingly slow when updating a view of a folder. Moving files is done ONE AT A TIME! If you have a folder with 2000 files and you just move twenty, it still takes an incredibly long time (I have measured more than five minutes). 

Remove file from display, redraw entire window; remove one more file, redraw display; remove one more file from pane, redraw...

This takes away a huge amount if usability from the entire concept. Why would you even want all your folders in view if it takes anything from five seconds to a minute for every single file moved because of the overhead? This I wish they would fix. When moving a lot of files just TURN OFF RENDER and refresh the pane only after redrawing the panel in a buffer. 

Other than that I love spatial mode. It can get cluttered until you get things repositioned, but you can prevent that just by clicking ANY folder and chooing "browse folder." Bingo, you're not in kansas anymore.

Spatial browsing + configurable scripts = any cool application you want. I have a template for all my image folders so they open up in the same place, same size every time. The "top" folder for them opens in another place. GQView opens in the little panel that's left. Movie files are similar, but different. Archives are completely different still. Total configurability. If I need to move around a lot of files I open a browser, other than that I have a few windows that "live" open on my desktop just about all the time. 

I do wish they would add the option in "browse" mode to "open spatial view." I'll probably get flamed for this yet a third time for bringing it up, but I don't know how one might do it with a shell script and I think this feature would help a lot of people see the great utility in it. That, and allow the right click "scripts" menu to become folder-aware (ie "add this script to the right click menu only in an MP3 folder...")

It's really hilarious how MS has been touting one new "invention" after another for the better part of a decade and still hasn't matched even the desktop power of  bash+gtk+zenity (much less the more "interactive" languages like python).[/QUOTE]
 Hi, this tip may help from gnomesupport.org forums:

got to Edit->Preferences->Preview->Count number of folder items, pick "never", thus should sped up,

btw is nautlius slow to start up for anyone else?

---

### Post by andii on 2005-01-12
Just wanted to say 'Thanks': I was trying to work out how to get the thing to show file addresses so that I could use it for FTP and the whole thing about how to make it spatial seems to do the whole kit bag and caboodle ... though I've not actually tried ftp'ing yet... but it's great to have the forum where I can just have a look and discover by trying out stuff that looks interesting.
Ta! :D

---

