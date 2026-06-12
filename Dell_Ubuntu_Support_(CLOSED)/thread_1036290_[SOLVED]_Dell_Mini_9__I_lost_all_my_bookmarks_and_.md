---
title: "[SOLVED] Dell Mini 9:  I lost all my bookmarks and can't fullscreen"
date: 2009-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by greenleaves123 on 2009-01-10
There was an icon on my Dell mini 9 to update stuff. I clicked it and it updated some things. But now I've lost all my bookmarks and my key with the windows symbol doesn't do a full screen anymore. 

My netbook doesn't have an F11 key. Previously I was using that windows key to make firefox full screen but now I can't. I tried searching for this problem, but I don't understand still. 

Does anyone know how I can get my bookmarks back or have the windows key be full screen again?

---

### Post by Claus7 on 2009-01-10
Hello,

about the windows key I think that you should readjust it from the key shortcuts menu:
System -> Preferences -> Keyboard shortcuts

Now about your bookmarks. Check if you have anything in /home/*your_user_name*/.mozilla/firefox/w6pgom85.default
or a similar folder. 

Regards!

---

### Post by ugm6hr on 2009-01-10
[http://mydellmini.com/forum/warning-about-the-most-recent-dell-ubuntu-update-t2422.html](http://mydellmini.com/forum/warning-about-the-most-recent-dell-ubuntu-update-t2422.html)

To fix the Firefox bookmarks / profile issue:

Either use Terminal (Applications -> Accessories -> Terminal):
Make sure you copy and paste exactly as here
```
rm ~/.mozilla/"web browser"
ln -s ~/.mozilla/firefox/ ~/.mozilla/"web browser"
```

Or use the File Manager (aka nautilus):
> 
Browse "Home Folder" (Places -> Home Folder)
Menu: View -> Show hidden Files
Double-click to Open ".mozilla"
Single left-click "web browser" (if it exists) and press Delete key on keyboard
Right-click "firefox" -> Make link
Right-click "Link to firefox" -> Rename; type "web browser" and press Return on keyboard



To remap the Windows key to F11 (which allows fullscreen in Firefox):
```
echo "keycode 115 = F11" > .Xmodmap
```
Reboot and "load" the xmodmap when offered.

---

### Post by greenleaves123 on 2009-01-10
Thanks ugm6hr! That fixed my bookmarks and the fullscreen problem!

---

### Post by Claus7 on 2009-01-10
Hello,

you are very kind to thank me, yet I do not think that I deserve it, except that trying to answer your question, your thread came across ugm6hr's path! I thought that you have a similar problem with bookmarks as mine, yet your problem was entirely different after all.

Regards!

---

### Post by starcannon on 2009-01-11
ugm6hr Thanks! saved me having to figure this out for myself. Thankfully no bookmarks were lost.

---

