---
title: "Two strange problems in jaunty with the gnome panel"
date: 2009-05-18
forum: Desktop Environments
---

### Post by night-wing on 2009-05-18
Hello.

I have two strange problems with the main menu panel in gnome.

The first one, I have since I installed jaunty:
Every time, when I start a game (like nexiuz or openarena), the icons in the panel are moved around, when I switch back to gnome desktop. This also happens, when I activate the "fix position" option from the icon. And also, when the game is in the same native screen resolution as gnome itself is.

The second one first appeared yesterday:
The gnome-panel doesn't load at startup. I did not update something or worked in the system before. Yesterday morning, all was good and like it should be. I also shut the pc down reguarly. In the afternoon, I had a blank gnome desktop without menu.
I can start the menu via terminal and have no error message. I also can start it via adding the service "gnome-panel" to the autostart programs. But this is not like it should be (and used to be).

Can anyone give me a hint?

Thanks.

Regards
nightwing

---

### Post by hkphooey on 2009-05-18
I'm not sure I can give you a hint, but I can share your frustration. Here's a list of things I've tried. Seems to be not only gnome-panel, but also nautilus and metacity in my case. 
   [http://ubuntuforums.org/showthread.php?t=1157756](http://ubuntuforums.org/showthread.php?t=1157756)

I think this could be related to me deleting some items from the menu using rightclick > Edit Menu. Were you doing that prior to experiencing this problem?

---

### Post by Reilithion on 2009-05-18
I have a similar problem.

I have two screens -- each connected to its own graphics card.  When I log in now, only the gnome-panels on my *secondary* screen show up.  The ones on my primary screen never load.  Unlike you, night-wing, I'm unable to start up the gnome-panel for my primary screen using a terminal because if I try, it terminates and prints out the following error:
```
Cannot register the panel shell: there is already one running.
```
The one that's running, of course, is on my secondary screen.  This rather cripples my primary screen.

I also experience a bug where choosing a menu item on my secondary screen causes that program to be launched in my primary screen.  Together, these bugs are incredibly annoying.  They make it much harder to make use of *either* of my screens.

EDIT: Looks like we're not the only ones having this problem.  [http://ubuntuforums.org/showthread.php?t=1161560&highlight=gnome+panel](http://ubuntuforums.org/showthread.php?t=1161560&highlight=gnome+panel)

---

### Post by Reilithion on 2009-05-18
I was able to get my panels back.  I followed the instructions provided in that other thread.  In case it helps, I'll reproduce them here.

In a terminal, enter the following command:
```
rm -r ~/.gconf/apps/panel
```
Then log out and back in.  (I actually rebooted, but it should work to just log out and back in.)

**WARNING**: If you've customized your panels, this will uncustomize them!

---

### Post by hkphooey on 2009-05-18
I actually tried removing/renaming the entire .gconf directory, but this still didn't bring the panels back. Also tried the .gnome2 and .gconfd directories to no avail. 

I think the panels configuration file is actually OK, because when I run gnome-panel from the command line, it comes up fine, and also when I add gnome-panel to my System > Preferences > Startup items. But it won't start up on its own any more (and nautilus, and metacity) which is wrong and I want to get back to the cause of it all, rather than putting on a BandAid solution. 

Reilithion: I sometimes run Ubuntu with an LCD screen attached to the Monitor out port of my laptop. When I first boot into it, the panels are on the wrong screen, but I can just drag them over to the right screen with the mouse. Maybe this is all you need to do?

---

### Post by hkphooey on 2009-05-21
I gave up: Reinstalled a fresh copy of 9.04 and now everything is working fine. Took me 4 hours to get everything up and running, but ultimately less time than it was taking me to chase around after this maddening problem.

---

### Post by night-wing on 2009-05-22
To me the hints also didn't work.
But I am now back to intrepid. So this could be closed! 
Thank you for all hints and help!

---

### Post by pjomega on 2009-05-25
If you have an on again, off again multiple monitor setup like me (and hkphooey above), gnome-panel may be trying to launch the panel on a nonexistent screen. I'd call it a bug; it seems like it OUGHT to see there's only one screen, and launch it there. Even so, it's a quick fix (let's hope it stays put). 

1) Run gconf-editor and check /apps/panel/toplevels
2) On each {side}_panel_screen{#} look for the "monitor" and "screen" keys; change their values to correspond to the screen you want. If you have only one, they should probably both be 0.
3) Log out and back in again. If you're like me, you'll probably see some default panels pop up. Right click on them and select "Delete This Panel." Do be sure these are the default ones and not the nice customized one you spent twenty minutes tweaking to get just right...
4) Check gconf-editor to make sure whichever toplevels are still there still have the appropriate screen/monitor and log out and back in again.

Your customized panels should be back. Incidentally, you can also just kill gnome-panel and restart it again after tweaking gconf, but I found gnome-panel didn't want to stay dead, so your mileage may vary.

---

### Post by Reilithion on 2009-05-31
This is starting to seriously annoy.  Even after I used the fix I posted, the panels on my main screen disappear periodically.  I have to delete ~/.gconf/apps/panel/ and then reboot every time.  I'm trying to nail down the pattern.  But if I keep having Gnome problems I'm seriously considering switching to KDE or Xfce or something.

---

### Post by gnimsh on 2009-07-13
I checked this out on the bug list, and its actually in the 100 papercuts to be fixed.  Here's the solution I found, which works for me:

"So in gconf-editor go to apps->panel ->general and find the corresponding entry for you in my case toplevel_id_list and reorder the panels in the list in the order you want them to appear in this case the first is at the edge of the screen."

For me the 2 items were listed as top_panel_screen0 and bottom_panel_screen0.  If you double click that entry and change the order so the panel you want is on top (likely the one that is in 2nd position needs to be moved to the first position) they will remain like this once you reboot!

---

