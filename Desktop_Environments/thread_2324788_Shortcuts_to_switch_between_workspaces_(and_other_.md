---
title: "Shortcuts to switch between workspaces (and other actions)"
date: 2016-05-16
forum: Desktop Environments
---

### Post by Kennedy_Richard_Si on 2016-05-16
Hello, I've used ubuntu actively for couple of years, never learning to much to be considered an intermediate user, but tweaking enough to be able to control lots of things. I had to put ubuntu aside because of other projects I was working on and so it was for 2 or 3 years. Now I'm back and decided to jump into xubuntu, since I have a low spec notebook (my former notebook is undergoing maintenance) and wanted to customize my notebook gradually (instead of cluttering it with software I don't use). Xubuntu uses Xfce environment, which makes things different.

Problem is, I couldn't set workspace related shortcuts by following **Menu > Settings > Keyboard(Application Shortcuts Tab)** anymore. I searched the web for a solution and couldn't find any. So I started tweaking other menus.

To my surprise, those shortcuts are present under **Menu > Setting > Window Manager (Keyboard Tab)**.

There you'll be able to set shortcuts for various windows and workspaces related actions (switch between workspaces, jump to specific workspaces, moving window to adjacent or specific workspaces, etc).

Since I didn't find any source on the web for my problem I thought It would be useful to register it here (even if it is already solved), so people looking for that particular setting find this answer.

Kennedy Richard.

---

### Post by egeezer on 2016-05-18
Xubuntu is just about the most user-configurable desktop of the *buntus.  I've always used the learn-by-trying-it method, but there is plenty of documentation at;

[http://docs.xfce.org/start](http://docs.xfce.org/start)

---

### Post by mikodo on 2016-05-19
Yes, there are so many easy gui ways to customize. Then, playing with config files is a whole new world beyond that in Xfce.

For gui, here are some I use. Yes, some are the ones you mentioned:

Settings Manager > KeyBoard     (I use some default and some I make myself there).

Settings > Window Manager > Keyboard       (Again some default I use, some I make myself).

Just an example of KeepassX, as one of the more frequent apps I open but, I open lots like thunar, FF, on and on:

KeepassX =  Alt + K       Make: Settings > Keyboard > Scroll to bottom > Add > add keepassx > open > find keepassx click on it > enter Alt + K

Window Management by key-strokes in Xfce has lots of options to use. One needs to decide which they like:  [http://xubuntu.org/news/window-resizing-in-xubuntu-and-xfce/](http://xubuntu.org/news/window-resizing-in-xubuntu-and-xfce/)

One can use launchers. Here is an example of a making one I used to use, when I made launchers from panel for a .pdf file I open everyday:

Stick a launcher in the panel and do like this for file launching. The file is called BP obviously.

Command = exo-open /home/mikodo/MyStuff/Documents/BP.pdf

For auto launching apps or services, one can use like I do to open my desktop upon start up in the inverse:

Settings Manager >> Session and Start up >> Application Autostart >> Add: xcalib = xcalib -i -a  && then I have a key-combo to toggle it as wanted.

Then of course, one can change config files but, that is more involved and I usually need to do what the pros do like ToZ so, I won't lay claim to those. :)

I keep a text file of all the key-presses I use, to set them again on fresh installs.

---

### Post by oldos2er on 2016-05-20
> **Kennedy_Richard_Si said:**
> Problem is, I couldn't set workspace related shortcuts by following **Menu > Settings > Keyboard(Application Shortcuts Tab)** anymore. I searched the web for a solution and couldn't find any. So I started tweaking other menus.

To my surprise, those shortcuts are present under **Menu > Setting > Window Manager (Keyboard Tab)**.

Yeah, window manager actions via keyboard shortcuts are kept separate from Application shortcuts, which makes sense really. Window manager actions is a much broader area than simple app launching.

---

