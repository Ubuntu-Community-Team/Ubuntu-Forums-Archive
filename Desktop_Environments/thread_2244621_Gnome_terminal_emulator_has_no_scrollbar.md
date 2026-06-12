---
title: "Gnome terminal emulator has no scrollbar"
date: 2014-09-17
forum: Desktop Environments
---

### Post by old_as_a_fossil on 2014-09-17
I'm connected using virtual Gnome terminal emulator to my Goobuntu desktop. No scrollbar appears when the screen gets full and lines go out of view. There is no menu for the terminal emulator where I can try out some options. Please help.

---

### Post by mcduck on 2014-09-17
As with most programs in Ubuntu (with Unity desktop) the terminal's menu appears in top left of the *screen*, not in the window itself. Also you can access the preferences by right-clicking inside the terminal window.

---

### Post by ajgreeny on 2014-09-17
Your problem may be that unity uses an overlay-scrollbar, which is hidden until you put your cursor over to the right hand edge of the window, when a scroll-box, not a scroll-bar should appear and allow you to grab and scroll.

I always remove the overlay-scrollbar applications from my unity desktop using synaptic package manager and go back to a standard scrollbar; just can't see the point of the overlay version myself.

---

### Post by Frogs Hair on 2014-09-17
The input/output  must also exceed the size of the default window before the overlay scrollbar becomes visible in Unity.

---

### Post by old_as_a_fossil on 2014-09-18
> **mcduck said:**
> As with most programs in Ubuntu (with Unity desktop) the terminal's menu appears in top left of the *screen*, not in the window itself. Also you can access the preferences by right-clicking inside the terminal window.

I know what you are saying. This is how the menu will appear when I'm physically at my goobuntu. But the problem I'm saying occurs when I'm remoting using a remote client that provides a Gnome virtual desktop. Here is the screenshot [http://s289.photobucket.com/user/spiderman2_photo_bucket/media/goobuntu/ScreenShot2014-09-18at51942PM.png.html?sort=3&o=0]("http://s289.photobucket.com/user/spiderman2_photo_bucket/media/goobuntu/ScreenShot2014-09-18at45916PM-1.png.html?sort=3&o=0")
There is no menu on the top left of the screen. Right clicking inside the terminal does nothing.

> **ajgreeny said:**
> Your problem may be that unity uses an overlay-scrollbar, which is hidden until you put your cursor over to the right hand edge of the window, when a scroll-box, not a scroll-bar should appear and allow you to grab and scroll.myself.

When I move the cursor to the top right edge of the window as seen in the picture, only the resize icon appears, not a scrollbox.

---

