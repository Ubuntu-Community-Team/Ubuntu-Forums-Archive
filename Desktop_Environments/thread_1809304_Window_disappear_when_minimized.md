---
title: "Window disappear when minimized"
date: 2011-07-21
forum: Desktop Environments
---

### Post by bitsonhj on 2011-07-21
hello guys.

When ubuntu started,after login screen, i got some error messages but i just close them.I just though its a small bug(not paying attention).
[COLOR=Red]
Alright ,HERE IS MY PROBLEM. [/COLOR]

When i open ,for example, mozilla ,a rectangle shows up in the bottom panel,like it always does.BUT NOW,nothing shows up .look at the picture.
[IMG]http://i277.photobucket.com/albums/kk47/bitsonhj/Screenshot-3.png[/IMG]

Now,when i minimize them, i dont know where the whole window disappear.But i know its not close,because when playing a video on youtube and i minimise the video, i can still hear the sound.

Also,take notice in the picture that, the icon showing the 'workspace' in the bottom right, has also disappear.


SO,just help me to get them back on screen.

Thanks in advance

---

### Post by enimeizoo on 2011-07-21
If I remember right, you can remove the taskbar on a gnome panel. That is probably what you did. Try to right-click the bottom panel and see if there is an option to add stuff to it. Probably something like taskbar, task manager ... (haven't used gnome in a while, can't help much, sorry)

---

### Post by Krytarik on 2011-07-21
Of course, you could just try re-adding "Window List" and "Workspace Switcher" to your panel. Therefore, just right-click on it, then you will get the point.

But it seems like they are still present in the panel's config but they are crashing upon loading the panel (exact error messages would have helped here). So, it seems like there is something wrong with the settings. So, just reset them to their default, then re-add your double-pair of Eyes and Chromium:
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```Greetings.

---

### Post by bitsonhj on 2011-08-07
ok thanks 'krytarik' .Everything is back and working fine . once again ,thanks

---

