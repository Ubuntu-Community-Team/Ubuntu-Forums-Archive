---
title: "Weird looking space between hidden pannel and window"
date: 2014-08-18
forum: Desktop Environments
---

### Post by Plex3000 on 2014-08-18
Hi everyone,

Well I installed gnome desktop and I'm using the gnome2 version, the one with the 2 panels, but i customized it: i installed a dock and I have 2 top panels, one for global menu in the center, and one for system tray/clock/user/power button to the right. Both autohide, but they only hide like 99%, so I can still see a little border of them, and I cannot use that tiny space with windows since the panel is occupying that space, so it is really annoying that if I have a bright-color background like white or any other bright color, and then I maximize a window, I can see that line of my desktop, also if I click there, like my browser tabs are on top, and i click the topmost coordinate of the screen to change a tab, I click the desktop instead and it's annoying. 

Is there a way to hide the gnome panels 100% ? I've been looking at the settings and I find nothing :(

Hope you guys can help me out, or it's inevitable? Visually it does not bother me if I have a dark background, but it's annoying that i click the desktop instead of my browser tabs, you know, anyways, thanks in advance :) 

Attachments::
--1: Example of my desktop with a light background, as you can see eventhough the 2 panels autohide, they can still be visible, (as I marked in blue), and I don't want that.
--2: Example of when I have a maximized window, if you look close you can see a pixel line between the top end of the image and the border of the window.
--3: Same as No.2 but with a bright green background so you can see clearly what I'm talking about.

---

### Post by mcduck on 2014-08-20
Due to the way how gnome-panel is programmed to work, it's not possible to completely hide it. The unhiding mechanism doesn't look for screen edges, but for the mouse to be over the panel itself, and because of that the panel is restricted to minimum of 1px being always visible. Otherwise you'd have no way to unhide it. (Even changing the hidden panel size to 0px through gconf or gsettings is ignored and the panel uses the minimum 1px limit instead.)

---

### Post by Plex3000 on 2014-08-21
Ahh crap :/ Wellp, so be it then, Thank you for your reply, sad but it's good to know though. Thanks a lot :) Do you know any other DE or panel interface where I can have my desktop like I have it now but fully hiding those top panels?

---

