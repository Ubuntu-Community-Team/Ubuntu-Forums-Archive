---
title: "Fluxbox questions"
date: 2007-10-26
forum: Desktop Environments
---

### Post by Montsegur87 on 2007-10-26
How can I put the right-click menu in the panel , so my mother can be happy :P

I dont find a way to edit the double click event on a window , so that it maximizes.

---

### Post by kerry_s on 2007-10-26
use a different panel. fluxbox panel is limited. what file manager are you using? some come with panels, for instance if your using thunar, you then have xfce4-panel you can use, rox has 1 to, otherwise you can just use a panel program. there is also always the option of using a different wm that has the correct kind on panel, like icewm or jwm for instance.

---

### Post by TeaSwigger on 2007-10-26
IceWM is light and has a conventional task bar and start menu.

You can create a start menu in the Fluxbox panel, actually. It looks like the eventual Fluxbuntu release will have it configured that way. But you'd have to compile Fluxbox yourself with that option. Unfortunately I don't recall the details and I've never tried it. I do seem to recall that it was discussed somewhere in one of these threads about the Fluxbox:

[http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)
[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

Luck :)

---

### Post by Montsegur87 on 2007-10-26
Thanks for the answers , I tried Openbox but it semmed ugly and I had to make my menu again ...

Any Idea on my first problem? I want windows to maximize/minimize on double click , not to shade.

---

### Post by TeaSwigger on 2007-10-27
Hello again. Hm actually I don't know, never fooled with it, but the first place I'd look for customizing that kind of action is in the ~/.fluxbox/init file.

In case you don't know, if you don't have that file copy the one found in I think /usr/share/fluxbox, those are for you to copy and customize with in a copy in your home folder. Hope that helps. :)

---

### Post by Montsegur87 on 2007-10-27
Thanks TeaSwigger for the tip.

I was able to customize many things in that file , like which items should be shown in the panel but the problem persist.

I'll play around with

```
session.screen0.titlebar.left:	Stick 
session.screen0.titlebar.right:	Minimize Maximize Close 
```

and see what happens.

---

### Post by mojoman on 2007-10-27
Have a look at this thread, post 36 might be what you're looking for.

[_http://ubuntuforums.org/showthread.php?t=371144&page=4_]("http://ubuntuforums.org/showthread.php?t=371144&page=4")

---

### Post by RedSquirrel on 2007-10-28
> **Montsegur87 said:**
> How can I put the right-click menu in the panel , so my mother can be happy :P

The link mojoman provided can do this, or you can use a different panel, as suggested by kerry_s.


> **Montsegur87 said:**
>  I dont find a way to edit the double click event on a window , so that it maximizes.

Off the top of my head, I don't think there's an easy way to do this. The following link describes how to edit the source code to do what you want. I haven't tried it because it's not something I need...

[http://fluxbox-wiki.org/index.php/Make_dblclick_titlebar_maximize](http://fluxbox-wiki.org/index.php/Make_dblclick_titlebar_maximize)

---

### Post by Montsegur87 on 2007-10-30
Thanks! I never thought of modifying the source code :P

I got fluxbox code via SVN , modified the elseif block , then

```
sh autogen
make
sudo make install
```

however , the fluxbox in my system is the one in the repositories =\ 

Do i have to uninstall fluxbox and then install the modified svn version in order to have the menu?

---

### Post by RedSquirrel on 2007-10-31
You could uninstall the one from the repositories if you like. You still have to make some changes to tell your system where to find the new fluxbox.

By default, the fluxbox you compile is installed in /usr/local/bin, whereas the fluxbox from the repositiories is in /usr/bin.

If you use a display manager (e.g., gdm) you'll have to modify the /usr/share/xsessions/fluxbox.desktop file. Change the lines that refer to /usr/bin/startfluxbox to /usr/local/bin/startfluxbox.

The compiling instructions in the Howto in my signature discuss this. ;)


EDIT:

I should mention as well that you will have to modify your ~/.fluxbox/startup file. Change the line 'exec /usr/bin/fluxbox' to 'exec /usr/local/bin/fluxbox'. See my Howto. :)

---

### Post by Montsegur87 on 2007-10-31
Thanks for the reply , it makes sense. I'll try this things and comment my experience.

---

### Post by rjmdomingo2003 on 2007-11-01
[FONT="Trebuchet MS"][/FONT]As an alternative, you can try idesk.

Set an icon wherever in your desktop, and configure the .ideskrc file command to singleRightClick (I think). Then, have the command for the icon to execute your ~/.fluxbox/menu.

As an example, refer to this link: [http://ubuntuforums.org/attachment.php?attachmentid=48020&d=1193501724](http://ubuntuforums.org/attachment.php?attachmentid=48020&d=1193501724). 
One of these (text)icons at the bottom can be renamed Menu, then do as above.

---

