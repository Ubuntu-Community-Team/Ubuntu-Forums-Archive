---
title: "Unity Launcher burried behind Windows"
date: 2011-08-15
forum: Desktop Environments
---

### Post by apollothethird on 2011-08-15
I'm sure it's a bug, but I would like some feedback from others.

It's often hard to use the Unity Launcher because it becomes buried behind the windows on the desktop.  I often have more than 50 windows opened at a time.  It takes a long time and a lot of work to reposition the windows so that I can see the launcher.  I usually have to use a workaround with is also cumbersome.

I have to find an empty Workspace, open the Launcher there.  Launch the new application.  Then drag it to the Workspace where I want to use it.  There are a number of other steps included to get the application up.

My question is, does anyone know how to unbury the Unity Launcher so that it's on top instead of behind the other Windows.  Also, has anyone else encountered this problem?

It's possible that many are encountering it but not noticing it.  If you only have one or two Windows opened and it's buried behind those, one would probably move the couple of windows without really thinking about it.  But when you have 10 or 20 windows that have to be moved, it becomes a serious time consuming task.

Thanks in advance for anyone who has any comments or suggestions.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2011-08-17
I found a resolution.  It appears that Unity's plugin is set to Dodge Windows by default.  I'm sure the bug is that when you try to active the Launcher it should activate on top of the Windows it dodges (the many windows).  It activated, but at times it activates behind those windows.  Since I have many windows opened it takes a long time to get all the windows out of the way so that I can see the search application window from the launcher (which is also behind all the windows).  The ALT-F2 command appears behind the windows also when this bug is effective.

The resolution is to change the Hide Launcher option from Dodge Windows to Doge Active Window.  Now I only have to move one Window when this bug activates.

By the way, toggling the Launcher from Doge Windows to Dodge Active Windows also brings it back to sanity, where its no longer behind the pile of windows.

I don't know what activates the bug, but when it happens, at least there is a resolution.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

