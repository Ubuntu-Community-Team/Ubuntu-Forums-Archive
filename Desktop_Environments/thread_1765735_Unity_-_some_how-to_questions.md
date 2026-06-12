---
title: "Unity - some how-to questions"
date: 2011-05-23
forum: Desktop Environments
---

### Post by areeda on 2011-05-23
So I've been playing with Unity 3D for a few months and finally upgraded to Natty for real.

I really like Unity's use of screen real estate but I can't figure out how to do some of my basic normal functions.  So this is a list of random questions, please comment on any of them.


[LIST]
[*]Is there a comprehensive document on how to use Unity?
[*]The Applications launcher is nice for finding a program the first time but gets tiresome after a while.  Is there a way to get the menu added to the [IMG]http://ubuntuforums.org/attachment.php?attachmentid=192984&stc=1&d=1306170437[/IMG] icon? Also what is that icon called?  This is Unix, remember the concept of minimum encumbrance for the experienced user.
[*]Is there a way to move a window to another desktop when it is maximized?  I can restore to normal size and right click on the title bar then remaximize but I'm hoping for a one step solution.
[*]When a window is minimized must it disappear completely? Is alt-tab the only way to restore it?
[*]There are some programs that I would like to open multiple windows when I click on the launcher such as terminal and Firefox.  I see in /usr/share/applications a section called: [NewWindow Shortcut Group].  How do I invoke that command?  It's not shift, alt or control click.  Those were my guesses.
[/LIST]
I really like the design of Unity.  It's like getting a new higher resolution monitor for free.  I have to learn how to use it effectively and stop trying to do things the old way.  i realize that but right now it's slowing me down.

Please help me get more proficient.

Joe

---

### Post by sikander3786 on 2011-05-23
Regarding Unity, this guide is the most comprehensive one found on the web I believe.

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

For getting to the menu, you can press <Super> (Windows Logo Key) and you would see the "Dash". Or you can click the Applications icon in Launcher.

For moving windows between desktops, what I use to do is click the Workspace Switcher in Launcher and then drag the window to desired workspace no matter it is maximized or not.

When a window is minimized, should it disappear completely? Guess I didn't understand part of your query. Off topic, you can use Alt + F9 to minimize windows. Can configure shortcuts by pressing the logout button > System Settings > Keyboard Shortcuts.

For opening a new window, mouse middle click opens a new instance of any app. Or Alt + F1 to focus the launcher, arrow keys to move to your desired app and press <Space>.

[http://ubuntu4beginners.blogspot.com/2011/04/multiple-instances-of-same-application.html](http://ubuntu4beginners.blogspot.com/2011/04/multiple-instances-of-same-application.html)

Here are a few things we've tried to put together for Unity users. Hope it would help.

[http://ubuntu4beginners.blogspot.com/search/label/Unity](http://ubuntu4beginners.blogspot.com/search/label/Unity)

---

### Post by areeda on 2011-05-23
Thank you Sikander!  That's very helpful.  I'm sure after reading those links I'll feel less like a noob.  If I may impose, a bit of follow up.

> **sikander3786 said:**
> For getting to the menu, you can press <Super> (Windows Logo Key) and you would see the "Dash". Or you can click the Applications icon in Launcher.If I understand correctly, this is the normal way to get the pages of icons to launch an app.  What I'm looking for is something quicker like a simple menu corresponding to System or Themes or Office Apps like in previous versions.  When I know what I want it's much quicker.

[quote=sikander3786]For moving windows between desktops, what I use to do is click the Workspace Switcher in Launcher and then drag the window to desired workspace no matter it is maximized or not.[/quote]Exactly what I was looking for.

[quote=sikander3786]When a window is minimized, should it disappear completely? Guess I didn't understand part of your query. Off topic, you can use Alt + F9 to minimize windows. Can configure shortcuts by pressing the logout button > System Settings > Keyboard Shortcuts.[/quote]I guess what I expected was an icon like Gnome put on the bottom bar somewhere to be able to see what's minimized.  If it disappears completely and Alt-Tab shows the list, I can live with that.  It's better than using 5% of the screen all the time.

[quote=sikander3786]For opening a new window, mouse middle click opens a new instance of any app. Or Alt + F1 to focus the launcher, arrow keys to move to your desired app and press <Space>.[/quote]Excellent!

_You've been very helpful_.  I now have something to read.  Thanks again for the links.  Maybe my next questions won't be so basic.

Joe

---

### Post by Copper Bezel on 2011-05-23
> I guess what I expected was an icon like Gnome put on the bottom bar somewhere to be able to see what's minimized.
Do you mean other than the Launcher icon? If you minimize a window and click its icon, it'll restore as you'd expect.

---

### Post by areeda on 2011-05-23
> **Copper Bezel said:**
> Do you mean other than the Launcher icon? If you minimize a window and click its icon, it'll restore as you'd expect.D'Oh  of course.

I haven't quite gotten used to that and keep missing those ticks that tell me it's minimized not launching a new one.

That's what I was looking for, I guess my nose got in the way

---

### Post by sikander3786 on 2011-05-24
If you noticed, when a specific app is running, a small arrow is displayed in front of its icon in Launcher. Is that what you were looking for?

Another alternative to launching apps category-wise is to right-click the Applications icon in Launcher.


Or click the Applications icon and on the right corner of "Search Box", you would spot a drop down menu for categories.

In the next version of Ubuntu i.e, 11.10, that menu is being integrated to the Dash button right-click functionality as I heard.

---

### Post by areeda on 2011-05-24
> **sikander3786 said:**
> If you noticed, when a specific app is running, a small arrow is displayed in front of its icon in Launcher. Is that what you were looking for? Yes. And now that I found it I think it's a good way to do it.

> Another alternative to launching apps category-wise is to right-click the Applications icon in Launcher.

Or click the Applications icon and on the right corner of "Search Box", you would spot a drop down menu for categories.

In the next version of Ubuntu i.e, 11.10, that menu is being integrated to the Dash button right-click functionality as I heard.
This is The real challenge of man-machine interfaces.  There are a lot of choices and even for the experts only some are familiar.  How to organize and make it easy for the novice but quick for the expert?

Right clicking the App Icon is a nice trick saves one level.  Also installing compiz-config and making the display bigger helps.

Menus on the Dash button were my first thought to address this.  Perhaps if the Applications searcher had Nautilus type options (Icon View, List View, Compact View), or the right click on the Applications Icon had cascading menus it could be more efficient.

I'm finding plenty of ways to make my work easier.  Mostly by me adapting to Unity rather than the other way around.

Joe

---

### Post by sikander3786 on 2011-05-25
Just wanted to make a note that if a specific app is running but not minimized, you'd see small arrows on both sides of the icon. If minimized, only on the left side of the icon. If multiple windows say 3, 3 small arrows would be displayed on the right side of the icon.

We are getting used to Unity :)

---

### Post by areeda on 2011-05-25
I found a cool one by accident Super-W (win logo-W) brings up all the open windows on all desktops and let you select them.

I haven't found where that key combination is set and what it's called but I've been using it often.

---

### Post by Copper Bezel on 2011-05-25
It's called Scale. It's in CompizConfig's Window Management plugins section.

---

