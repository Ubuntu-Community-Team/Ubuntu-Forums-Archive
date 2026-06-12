---
title: "How do I get my applications menu like this:"
date: 2006-02-19
forum: Desktop Environments
---

### Post by naked on 2006-02-19
In the first video, true transparency, the applications menu seems to have a Windows xp spin, but I kind of like it.  I would at least like to play with it more.  Is this a new gnome feature that will come out with dapper?

Here is the site with the video.  You see this guys application menu about half way through, streaming the flash format is fastest for me.

[http://www.novell.com/linux/xglrelease/](http://www.novell.com/linux/xglrelease/)

Thanks!

L

---

### Post by RAOF on 2006-02-19
That work has been done on a Novell branch of Gnome.  While it could be merged back into the main branch of Gnome (if the Gnome devs think it is a sufficiently good idea - that is in no way finalised yet) it won't be in Gnome 2.14, which is what Dapper (will) has.

---

### Post by naked on 2006-02-19
Hum.  So then could Novell be classified as bleeding edge? 

What is Novell's flavor of linux called, is it free?  

Thanks for the post!

L

---

### Post by RAOF on 2006-02-19
I belive that Novell make Suse linux, and there is OpenSuse, which is free.  I think.

---

### Post by anthro398 on 2006-02-20
Xgl is also included in the Flight 4 Dapper Drake release so it will be included in Ubuntu 6.04.

---

### Post by RAOF on 2006-02-20
[QUOTE=anthro398]Xgl is also included in the Flight 4 Dapper Drake release so it will be included in Ubuntu 6.04.[/QUOTE]
But Xgl is not the variant Gnome stuff.  You **won't** get that in Dapper.

---

### Post by anthro398 on 2006-02-20
> But Xgl is not the variant Gnome stuff. You won't get that in Dapper.

Sorry.  I don't follow.

---

### Post by RAOF on 2006-02-20
Ok, a quick bit of linux-gui-architecture ;)

He's talking about the WindowsXP-like "applications" menu, with a field for searching, frequently used programs, etc.  This is a modification to **Gnome**.  Gnome is a "desktop envionment" - it handles windows, themes, etc.  Gnome draws stuff to the **X server**, which is what actually runs your graphics card.  **XGL** is a new X server, which does all of it's drawing using the 3D support of your graphics card, meaning that:
1) It can be much faster - even integrated graphics chips are powerful enough to handle drawing GUI type stuff without troubling the CPU
2) It can do all sorts of cool effects easily - transparency, changing colours, deforming windows, etc, because it can just tell the graphics card to do all the work.

Xgl is available in Dapper right now (and the visual effects it allows are really **stunning**).  The different "applications" menu is not, and will not, get into the main Gnome release in time to be included in Dapper.  If it gets in there at all.

---

### Post by anthro398 on 2006-02-21
Oh, right.  Thanks.  I have a general understanding of the x windows system, but I didn't notice the start menu in the video.  I, for one, despise the default XP start menu.  The very first thing I do on new XP installs is change the menu back to classic.  I guess I can see how others might like it, though.  Thanks for pointing that out to me.

Although, the more I look at it, the more it grows on me.

[IMG]http://www4.ncsu.edu/~jjtuttle/gnostart.png[/IMG]

---

### Post by linuxishard on 2006-02-21
I use Dapper.. and it does al that stuff like transparency an stuff,, But i ges development and all that means that there are a few bugs, i cant change any of the defualt settings to much without it crashing,, ALOT 
 i want to totaly replace  my taskbars and stuff compleatly with nicer ones, does anyone know how i can do this with dapper,

---

