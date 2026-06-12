---
title: "Help me make my desktop?"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by Kougaiji on 2008-01-05
I have seen a few screenshots of desktops that have certain elements that I like. Specifically I'm looking for instructions on how to make a panel-free, icon-free (uses text/titles instead of icons themselves) desktop. I've been looking around on how to make a desktop with text/names instead of icons, but my search has been fruitless. Additionally, I assume some kind of *box would be appropriate for my quest to get rid of the panel, however I'm not sure which one (leaning toward flux).

How do create a minimalist desktop that replaces titles with icons?

What are some unique integrations of panels without actually using panels (I've seen my share of docks, and I'm aware of *box)? Is there a nice alternative that involves blending the menus/panels with the desktop background as well? I ask this because I feel like this would blend in with the "text icons" the best.

Anything else :D?


I want to use a very minimalist desktop that is efficient (doesn't use a lot of clicking to get to the place I want) and I would like to retain compiz/eyecandy.

I am looking for some screenshots of what I'm talking about as we speak. (while we're at it, can someone tell me what tint and idesk is?)


What kind of tools am I looking for here?
edit: this is [http://ubuntuforums.org/attachment.php?attachmentid=55375&d=1199538142](http://ubuntuforums.org/attachment.php?attachmentid=55375&d=1199538142) something close to the icon style i'm looking for, although not that one.

---

### Post by Dark Hornet on 2008-01-05
--Wow--thats a really cool desktop...i will be keeping an eye on this thread.

---

### Post by allforcarrie on 2008-01-05
interesting!  i dont know if Gnome can do what you are asking, i'm sure there is a program/window manager that can.

---

### Post by rjmdomingo2003 on 2008-01-06
> **Kougaiji said:**
> I have seen a few screenshots of desktops that have certain elements that I like. Specifically I'm looking for instructions on how to make a panel-free, icon-free (uses text/titles instead of icons themselves) desktop. I've been looking around on how to make a desktop with text/names instead of icons, but my search has been fruitless. Additionally, I assume some kind of *box would be appropriate for my quest to get rid of the panel, however I'm not sure which one (leaning toward flux).

How do create a minimalist desktop that replaces titles with icons?

What are some unique integrations of panels without actually using panels (I've seen my share of docks, and I'm aware of *box)? Is there a nice alternative that involves blending the menus/panels with the desktop background as well? I ask this because I feel like this would blend in with the "text icons" the best.

Anything else :D?


I want to use a very minimalist desktop that is efficient (doesn't use a lot of clicking to get to the place I want) and I would like to retain compiz/eyecandy.

I am looking for some screenshots of what I'm talking about as we speak. (while we're at it, can someone tell me what tint and idesk is?)


What kind of tools am I looking for here?
edit: this is [http://ubuntuforums.org/attachment.php?attachmentid=55375&d=1199538142](http://ubuntuforums.org/attachment.php?attachmentid=55375&d=1199538142) something close to the icon style i'm looking for, although not that one.
Glad that you liked my current desktop.

First things first, if you like this sort of minimalist desktop, with a *bow WM (window manager), you can't have compiz at the same time since they are both WM's (please correct me if I'm wrong).

Using this desktop as the "model", we use fluxbox as the WM. Read this excellent tute for fluxbox from Red Squirrel: [http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox](http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox)

For the wallpaper, an excellent source would be deviantart.com. I think a lot of people would agree, although, there are other excellent sites (i.e. customize.org, pixelgirlpresents, etc.). It's the colors from the wallpapers that I choose conky's & tint's font colors. More on them later.

For the dock icons (text), you can again get them from deviantart.com. They have a bunch of text-type icons, although, you'd have to search for what you like in the dock icons section. You'll then have to either use fbdesk, rox or idesk, which I use exclusively, for putting icons on the desktop. Here's the tute: [http://idesk.sourceforge.net/wiki/index.php/Idesk-usage](http://idesk.sourceforge.net/wiki/index.php/Idesk-usage). You just need to be patient with the icon placements.

For conky, I've built mine from source to enable rss feeds: [http://conky.sourceforge.net/](http://conky.sourceforge.net/). Instead of: 
```
./configure
```
do:
```
./configure --enable-rss
```
to have rss feeds enabled, if you prefer to. You could also incorporate symbols/fonts in conky for "uniqueness": [http://ubuntuforums.org/attachment.php?attachmentid=54177&d=1198571423](http://ubuntuforums.org/attachment.php?attachmentid=54177&d=1198571423) (my previous desktop).

Tint Task Manager (ttm or simply, tint), is a good substitute for a "visible" dock/taskbar, showing currently opened apps. Again I've built mine from source: [http://code.google.com/p/ttm/](http://code.google.com/p/ttm/). Check out this thread for a good overview & configurations of tint: [http://ubuntuforums.org/showthread.php?t=510528&highlight=post+tint](http://ubuntuforums.org/showthread.php?t=510528&highlight=post+tint). It ain't that hard to configure.

You could always use gimp for "blending" or picking colors from the background/wallpaper, and incorporate them to your menu colors. If you decide on using flux, you can easily edit your themes. A great source for themes is: [http://box-look.org/](http://box-look.org/).

Good luck on your "quest".

---

### Post by r41nz0r on 2008-01-06
Interesting I'll look around for some nice themes and desktop applets for you.

---

### Post by urukrama on 2008-01-06
rjmdomingo has already mentioned quite a bit. Here are some additions:

Openbox is another great window manager. To install and configure it, see the link in my signature.

To remove icons from your gtk theme, add the following to your /home/USERNAME/.gtkrc.mine file:

> gtk-toolbar-style = GTK_TOOLBAR_TEXT 

and make sure your /home/USERNAME/.gtkrc-2.0 file contains the following line:

> include &#8220;/home/USERNAME/.gtkrc.mine&#8221;

(If these files don't exist, create them)

Add the following to the gtkrc file of the theme you like (either in /usr/share/themes/THEMENAME/gtk-2.0/ or in /home/USERNAME/.themes/THEMENAME/gtk-2.0/ ) to remove the icons on buttons and menus (just at the top of the file):

> gtk-button-images = 0
gtk-menu-images = 0

---

### Post by Kougaiji on 2008-01-06
Thanks a lot everybody! The answers help a lot!

---

### Post by rjmdomingo2003 on 2008-01-06
> **Kougaiji said:**
> Thanks a lot everybody! The answers help a lot!
Hey, be sure to post some screenshots of your desktop(s) for us to criticize.:)

---

### Post by Dark Hornet on 2008-01-07
I'm just curious, but does this type of desktop setup take up less resources than Compiz?

---

### Post by urukrama on 2008-01-07
Yes. A lot less.

---

