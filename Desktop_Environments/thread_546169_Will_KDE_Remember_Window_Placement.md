---
title: "Will KDE Remember Window Placement?"
date: 2007-09-08
forum: Desktop Environments
---

### Post by [z]ephyr on 2007-09-08
HI all,
I've found several other threads like this in the forums, but none with any replies that are at all helpful.  I'm wondering if there is a way to get KDE to *intelligently* remember (or just know) window placement and size.  I've tried fooling with the Advanced>Special Window Settings in the top left of the application titlebar, but it never acts intelligently.  For example, it will remember that I want Firefox on my left monitor (I have 2) and that I want it to be fullscreen on that monitor.  However, this makes every firefox window fullscreen and on the left monitor.  So, "clear private data", "downloads", "preferences" are all annoyingly fullscreen.  Same with thunderbird.  It makes the 'send message' and also the 'connecting...authenticating...sending" windows the same size as the main windows.  I hate to say it, but Windows always knew what size dialog boxes should be.  'Ok - Cancel' dialogs shouldn't be fullscreen.  

-zeph

---

### Post by kellemes on 2007-09-08
Right click the caption, click configure-window-behavior -> moving -> placement..
Depending on windowstyle you can do all kinds of stuff from here.
Don't think Windows has these options as I remember.. :popcorn:

---

### Post by [z]ephyr on 2007-09-08
Well, I went to that menu, and chose "centered" placement.  Now it works exactly like I want it to, with logical dialog sizes and remembering where stuff goes.  So...what exactly is 'centered' placement?

-zeph

---

### Post by g00f on 2008-04-06
This is a pet hate of mine too. There are all sorts of window placement options except the one I and a lot of other people want ... 'remember'. When I close kontact for example, next time I run it I want it to come up in the same place it was when I closed it last time.

I know this is achieved in Windows at an application level, not by the window manager. ie the application itself needs to be coded to remember it's location and sets up that location next time it starts. Maybe that puts it in the 'too hard' basket for the window manager (KDE) to do. Shame though.

---

### Post by hazica on 2008-04-11
> **g00f said:**
> This is a pet hate of mine too. There are all sorts of window placement options except the one I and a lot of other people want ... 'remember'. When I close kontact for example, next time I run it I want it to come up in the same place it was when I closed it last time.

[..]

Maybe that puts it in the 'too hard' basket for the window manager (KDE) to do. Shame though.

Well, I just came across this post a couple of minutes ago, while I was trying to find a way to make my Kaffeine window pop up in a certain place on my desktop. After reading your post I became quite disappointed with KDE(KWin), thinking there really was no way of giving a window fixed starting coordinates.

Accidentally, though, I discovered that KWin implements just such a feature (and many similar ones)! All you have to do is open the window menu of a specific window, choose "Advanced" -> "Special Window Settings". Open the tab "Geometry", click the checkbox "Position", choose "Remember" from the drop-down menu and then enter the desired coordinates in the textbox.

Simple and powerful! That's one of the reasons why I love KDE.

Anyway, the Kwin people have done a darn good job of predicting users' needs! (Turns out it wasn't "too hard" after all)

---

### Post by g00f on 2008-04-13
> **hazica said:**
> Accidentally, though, I discovered that KWin implements just such a feature

My apologies, you're right. Reading your post made me go back & check again and the feature that I wanted is now now there. It must have been added since I last looked for it. Well done the KDE team. (I'm at the point now of the original poster, pop up dialog boxes are now the size of the main window.)

[SIZE="1"]I don't want to sound like a whinger, but it'd be nice if 'remember' was a global option for all windows instead of having to enable it individually for each window.[/SIZE]

---

