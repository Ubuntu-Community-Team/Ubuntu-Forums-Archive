---
title: "Trouble with maximized windows using KDE/kwin"
date: 2011-06-23
forum: Desktop Environments
---

### Post by zellis on 2011-06-23
Okay, I've just installed KDE4.6.2 onto my pre-existing installation of Natty Narwhal by installing the kde-standard metapackage. Trying to run KDE with the kwin window manager, I have two, possibly related problems.

First: every single window is opening up automatically maximized. This includes dialog boxes. I can find nothing to suggest why this is the default behaviour for all windows, and can't find anything that will change it.

Second: when a window is maximized, it has no titlebar. I can reduce them to normal size by right clicking the window in the task manager and unticking the "maximize" option. This then gives the window a titlebar. But if the window is then maximised again, the titlebar goes away again.

I currently have Unity, Ubuntu Classic and KDE available as options for desktop environments. I would like to use KDE, but this default window behaviour is infuriating. It doesn't show up in the other environments so far, just in KDE. Please help.

---

### Post by zellis on 2011-06-27
Incredible.

Apparently there's an option for the kwinrc config file which makes KDE draw maximized windows without titlebars. [Here]("http://majewsky.wordpress.com/2010/03/24/the-kwin-button-applet/#comment-831") I discover that adding the line &#8220;BorderlessMaximizedWindows=true&#8221; to the [Windows] section of kwinrc makes KDE behave the way it's behaving on my system against my will. Is this documented somewhere?

So I add "BorderlessMaximizedWindows=false" to the [Windows] section of my kwinrc file, do "kwin --replace" and it works! My titlebars are back.

Some of my windows aren't defaulting to maximized when I open them either, although that started happening before I modified the kwinrc file, so they may not be related.

Two questions remain for me (1) is the change to the kwinrc going to be persistent? and (2) how (and where) was the configuration for kwin originally set to the behaviour that I didn't want?

---

