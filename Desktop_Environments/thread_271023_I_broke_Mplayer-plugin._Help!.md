---
title: "I broke Mplayer-plugin. Help!"
date: 2006-10-04
forum: Desktop Environments
---

### Post by robtotheb on 2006-10-04
I was trying to get a BBC show to stream last night and I right clicked into mplayer firefox plugin's preferences and ticked ALL the options on.  BIG mistake.  Now everytime mplayerplugin loads its freezes firefox so i cant go back in and un-tick the boxes!  I tried reinstalling but no change.  Any suggestions?


- solved 

gedit /.mplayer/mplayerplug-in.conf 

Changed:
nomediacache=1   
to =0

---

### Post by penquin on 2007-05-20
I don't know if you are willing to do this, but it worked for me.  Just uninstall then reinstall Mplayer-plugin.  I ticked the same stuff before and after, and it only worked after reinstall.

---

