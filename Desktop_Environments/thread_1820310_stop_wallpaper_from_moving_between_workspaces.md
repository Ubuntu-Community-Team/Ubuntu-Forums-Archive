---
title: "stop wallpaper from moving between workspaces"
date: 2011-08-07
forum: Desktop Environments
---

### Post by kedmond on 2011-08-07
In Ubuntu 10.10, when I moved to different workspaces the wall paper wouldn't slide around.  I have the same wallpaper for all workspaces.  Currently, when I switch between workspaces the wall paper slides too.

I totally forget how to configure this.  I can't find it in Compiz anywhere.  Thanks!

---

### Post by SalHelder on 2011-08-07
Not sure if I follow you, but isn't that related with the workspace switcher option?

---

### Post by kedmond on 2011-08-07
Sorry, it's difficult to explain.

It should be related to the workspace switcher option.  Basicaly, imagine the wallpaper doesn't move when you switch workspaces.  All your windows slide by as you move to the new workspace, but the wallpaper just stays still.

---

### Post by Frogs Hair on 2011-08-07
That sounds like normal behavior , each work space uses the same background unless you are using the Compiz wallpaper plug-in . :confused:

---

### Post by hakermania on 2011-08-07
Can you record/provide as with a screenshot that points out the problem?
I don't get it.

---

### Post by kedmond on 2011-08-07
It's not something I can take a screenshot of.

And it IS normal behavior.  I'm not saying it's a problem, I'm just saying that in Ubuntu 10.10 I had it set up so that the wallpaper never moved when you switched workspaces.

Imagine this: You have two workspaces next to one another.  You have no windows open at all.  Currently, if I switch to the neighboring workspace, the wallpaper slides by, as it should.  The way I had it set up was that the wallpaper didn't move at all.

It's not a big deal, I was just curious if there was a simple solution.

---

### Post by hakermania on 2011-08-07
Oh, got it, you mean that you "see the workspaces move, the movement isn't instant (like in 10.10 and before I think?), you can see the wallpaper slide by while you're changing workspace", I got it!
But I cannot help you :/

---

### Post by SalHelder on 2011-08-07
Are you sure you were using Compiz? I can't replicate that at all, and I've been switching options for quit a while now. Just try to activate metacity's compositing to see if it works now.

1. Turn off Compiz. If you need install fusion-icon, launch it and in the notification area will show up an icon that will allow you to chose another window manager, pick metacity.

2. Go to gconf-editor

3. Then go:
Apps > Metacity > general.

4. And check the compositing_manager.

With this the desktop stays the same place when you switch workspaces, but I don't think you can do that with Compiz.

---

### Post by kedmond on 2011-08-07
OH wow...I had no idea.  Thanks again for the help!

---

