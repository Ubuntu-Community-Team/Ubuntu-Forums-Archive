---
title: "video play with compiz not working"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by salvadorveiga on 2007-11-01
Hello everyone the thing is... I see video clips all the time of people on their computers dragging their video windows and the video goes along with it... to me that doesn't happen... when  I start to drag a window the movie stays in place and the window borders will move so around the movie will be a kind of a blue background... on Mplayer the video driver enabled is X11/xv ... I also tried all other drivers especially the X11 (XImage/Shm) which lets me do the dragging but the video will stay small if I double its size or try to watch it full screen the size will remain the same and around there will be once again the blue background... any help ? oh yeah I am using a ATI 9200 Radeon Series

hope someone can help thanks

---

### Post by ajgreeny on 2007-11-01
Have a look in /etc/.mplayer/mplayer.conf and see if there is an uncommented (without #) line **zoom=yes**.  If it is **zoom=no**, change it and I think the sizing problem may go away, but I'm not sure.  Worth trying.

Your other problem of the contents of the window staying where they are, and only moving after the mouse button is released is the same as my system.  I haven't played around for a solution to it because it's not a problem to me, but it would be worth trying the same thing without compiz running, if you normally have it.

---

### Post by salvadorveiga on 2007-11-01
it worked slightly... it was commented though ##zoom=yes but I still get blue top bars and on the bottom as if a 16:9 movie... i'll try to manage that on my own thanks !

---

