---
title: "Nautilus - where has &quot;Open With&quot; gone?"
date: 2010-08-03
forum: Desktop Environments
---

### Post by denham2010 on 2010-08-03
Hi,

Wondering if it is just me (being so used to Xfce and Thunar), but why is it when I right click on a .desktop file in Nautilus, I only have the "Open" option, not "Open with"?

I would like the option to be able to open them in gedit to make any changes I need.

Any other file I right click on has the "open with" option, just not .desktop files.

It is extremely frustrating as the displayed name is not always the same as the filename for .desktop files.

Currently it requires me to ls in the terminal to find out the file name before entering gedit <filename>. Even then it can be hit and miss because the filename may not be the name that is displayed.

Has Nautilus always done this? I am so used to Thunar in Xfce where no matter what file you right click on, you have the "open with" option.

Cheers.

---

### Post by mc4man on 2010-08-03
Don't recollect seeing the open with on .desktops.

Here have always  used nautilus actions to create a 'Open in Gedit' option.

Otherwise you could open the terminal, type gedit <spacebar>, drop the .desktop into terminal, click in terminal to return focus and enter on keyboard.
(nautilus action way is better..

---

### Post by denham2010 on 2010-08-03
Thanks for your reply.

I have installed nautilus-actions and created an action to open in gedit, but it refuses to appear for .desktop files.

This is really frustrating. I don't see why I should have to install and 'extras' package for something that should be a standard default option (besides the point I know, but still).

Grrr......moved to Gnome from Xfce due to libmobiledevice libraries not working with Thunar (still uses hal not udev) and now I lose this bit of basic functionality.

I know it doesn't seem like much, but it is just so annoying. I am of 2 minds now, do I give up libmobiledevice and not be able to sync my ipod touch in xfce, or do I give up "open with" functionality???

I know I could just install Thunar and be done with it, but that is going to pull in a lot of libraries that I do not need, and is really just a work around, not a solution).

Hmmmm......

---

### Post by mocoloco on 2010-08-03
You're not missing anything, Nautilus has always been like that.  As someone who uses XFCE frequently this drives me nuts.  The simplest way I deal with it is to open gedit, then drag and drop the launcher onto it.  Works grabbing menu items to drag and drop too.

---

### Post by mc4man on 2010-08-03
> I have installed nautilus-actions and created an action to open in gedit, but it refuses to appear for .desktop files.

Never had any issue there - basically just command of gedit, parameters of
%M
Did you do a restart? 
(I'm using nautilus-actions 2.30.2 which doesn't require a restart - older version may.

---

### Post by denham2010 on 2010-08-03
Thanks for that mocoloco. It just goes to show how ingrained my xfce habits are. I didn't even think of dran'n'drop.

I must say, my shift to gnome, while not uncomfortable, has been awkward. I am just so used to doing things the xfce way.

mc4man, that is exactly the command I have set up in nautilus actions. I haven't done a restart as I'm in the middle of encoding some video files, but I am using Ubuntu 10.04, with nautilus-actions from the repositories. So I assume this is the most recent version that doesn't require a restart.

The action I created is appearing in the right click context menu, just not for .desktop files. Seems there is something overriding the action for this file type.

Cheers.

---

### Post by mc4man on 2010-08-03
Got me, only thing I can think to ck. is the conditions - filetype set to * should work for all files - screen

you could try setting just for .desktop to see what happens, use - 
*.desktop

---

