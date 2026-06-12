---
title: "Themes, Icons, etc. in Fluxbox"
date: 2007-02-05
forum: Desktop Environments
---

### Post by teejay17 on 2007-02-05
Does anyone know how I can get my themes, icons, etc. to stay once I shut down/reboot in Fluxbox. Currently, my personalizations, including desktop background, all disappear when I restart and my desktop goes back to whatever default Fluxbox "style" that was there before.
Now, to get more specific: I am configuring these items in "Gnome Control Center" and everything I want other than window borders gets configured like I want them to be. Nonetheless, these configurations also disappear on shutdown/reboot.

---

### Post by yabbadabbadont on 2007-02-05
You probably need to start gnome-settings-demon (spelling?) in your ~/.fluxbox/startup file.  Or you could install something like gtk-theme-switch to configure your .gtk* files directly.

Example:
```
/home/bubba $ ls -l .gtk*
-rw-r--r-- 1 bubba bubba 152 2007-02-05 01:56 .gtkrc
-rw-r--r-- 1 bubba bubba 160 2007-02-05 02:08 .gtkrc-2.0
-rw-r--r-- 1 bubba bubba 125 2007-02-05 00:54 .gtkrc.mine

/home/bubba $ cat .gtkrc
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/bubba/.themes/Ana/gtk/gtkrc"

include "/home/bubba/.gtkrc.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT

/home/bubba $ cat .gtkrc-2.0 
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/bubba/.themes/Ana/gtk-2.0/gtkrc"

include "/home/bubba/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT

/home/bubba $ cat .gtkrc.mine 
style "gtk-utf-8"
{
fontset="-adobe-helvetica-medium-r-normal-*-12-*-*-*-*-*-iso8859-1"
}
widget_class "*" style "gtk-utf-8"

```
You can set the icon theme by adding: gtk-icon-theme-name="iconthemenamehere" to your .gtkrc-2.0 file.

---

### Post by RedSquirrel on 2007-02-05
> **teejay17 said:**
> Does anyone know how I can get my themes, icons, etc. to stay once I shut down/reboot in Fluxbox. Currently, my personalizations, including desktop background, all disappear when I restart and my desktop goes back to whatever default Fluxbox "style" that was there before.
Now, to get more specific: I am configuring these items in "Gnome Control Center" and everything I want other than window borders gets configured like I want them to be. Nonetheless, these configurations also disappear on shutdown/reboot.

I wouldn't use GNOME Control Center to configure things in Fluxbox.

Definitely use the gtk-theme-switch. It's in the repositories. You can create a .gtkrc-2.0 file manually, but there's no need to do that since gtk-theme-switch does everything for you.

Once it's installed, run it in a terminal with:

```
switch2
```What are you using to set the background? GNOME Control Center?

Try this instead:

[http://fluxbox-wiki.org/index.php/Background](http://fluxbox-wiki.org/index.php/Background)

OR, you can also put something like this in your menu:

```

[wallpapers] (/path/to/background/images) {background-setting-command}

```See:

[http://fluxbox.sourceforge.net/docbook/en/html/x750.html](http://fluxbox.sourceforge.net/docbook/en/html/x750.html)

That will give you a menu item that is a list of backgrounds. I found that little trick was really handy.

To make sure things stay after you leave Fluxbox, try "Restart" from the Fluxbox menu. That should make things stick around for next time. "Reload config" works in some cases too, but I think "Restart" is better.


By the way, the Fluxbox "style" you choose still controls what the window borders look like (titlebar etc.).  gtk-theme-switch only affects the other parts of the window.

---

### Post by teejay17 on 2007-02-06
> **RedSquirrel said:**
> I wouldn't use GNOME Control Center to configure things in Fluxbox.

Definitely use the gtk-theme-switch. It's in the repositories. You can create a .gtkrc-2.0 file manually, but there's no need to do that since gtk-theme-switch does everything for you.

Once it's installed, run it in a terminal with:

```
switch2
```What are you using to set the background? GNOME Control Center?

Try this instead:

[http://fluxbox-wiki.org/index.php/Background](http://fluxbox-wiki.org/index.php/Background)

OR, you can also put something like this in your menu:

```

[wallpapers] (/path/to/background/images) {background-setting-command}

```See:

[http://fluxbox.sourceforge.net/docbook/en/html/x750.html](http://fluxbox.sourceforge.net/docbook/en/html/x750.html)

That will give you a menu item that is a list of backgrounds. I found that little trick was really handy.

To make sure things stay after you leave Fluxbox, try "Restart" from the Fluxbox menu. That should make things stick around for next time. "Reload config" works in some cases too, but I think "Restart" is better.


By the way, the Fluxbox "style" you choose still controls what the window borders look like (titlebar etc.).  gtk-theme-switch only affects the other parts of the window.
Thanks, I'm going to work on this. You're input is always valued; you might remember one of my other posts, "[Fluxbox Anyone?]("http://www.ubuntuforums.org/showthread.php?t=328138")" and your direction went a long way in helping me get Fluxbox installed in the first place. :guitar:

---

### Post by dico on 2007-02-06
These Links helped me while i styled my Fluxbox:

[HowTo style fluxbox](http://tenr.de/howtos/style_fbox/style_fbox.html)
[Fluxbox Style Guide](http://wiki.archlinux.org/index.php/Fluxbox_Style_Guide)

You can also install fluxconf with apt-get.

---

### Post by teejay17 on 2007-02-06
> **dico said:**
> These Links helped me while i styled my Fluxbox:

[HowTo style fluxbox]("http://tenr.de/howtos/style_fbox/style_fbox.html")
[Fluxbox Style Guide]("http://wiki.archlinux.org/index.php/Fluxbox_Style_Guide")

You can also install fluxconf with apt-get.
Is fluxconf fairly easy to use?

---

### Post by dico on 2007-02-06
It doesn't hurt ;)

---

### Post by RedSquirrel on 2007-02-06
> **teejay17 said:**
> Thanks, I'm going to work on this. You're input is always valued; you might remember one of my other posts, "[Fluxbox Anyone?]("http://www.ubuntuforums.org/showthread.php?t=328138")" and your direction went a long way in helping me get Fluxbox installed in the first place. :guitar:



Glad I could help. :)

As I mentioned back in that "Fluxbox, Anyone" thread, Fluxbox does take a bit of work to make it look exactly as you want, but that's one of the great things about Fluxbox: you **can** make it look *exactly* as you want (or pretty darn close, anyway) with just a bit of effort. [With some other environments you're sort of stuck with  things as they are since they're not as configurable.] 

Here are the links I used most often when I was learning how to configure Fluxbox:

Fluxbox Community Doc
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

Fluxbox-wiki
[http://fluxbox-wiki.org/index.php/Fluxbox-wiki](http://fluxbox-wiki.org/index.php/Fluxbox-wiki)

Fluxbox-wiki FAQ
[http://fluxbox-wiki.org/index.php/Faqs](http://fluxbox-wiki.org/index.php/Faqs)

Fluxbox Documentation
[http://fluxbox.sourceforge.net/docbook.php](http://fluxbox.sourceforge.net/docbook.php)


I also worked with that Fluxbox style guide from Arch linux (mentioned by dico). That's useful if you're going to get into configuring the contents of the style file itself, which you might want to do eventually.

And if you're interested, "Mr..Yeti" has made a Human style for Fluxbox. Check this out:

[http://ubuntuforums.org/showthread.php?t=317273](http://ubuntuforums.org/showthread.php?t=317273)

All you have to do with the "Human-fluxbox-style-0.1.tar.gz" file attached to that post is unpack it in your ~/.fluxbox/styles directory. Don't know if you like the Human theme, but I thought it was kind of a neat idea. In Fluxbox, I use the Operation style with IndustrialTango as the theme (most of the time).

Have fun!


PS - Oddly enough, I am using mostly XFCE these days since I decided one evening to download & install Xubuntu 6.10 for something to do. It's pretty good, but Fluxbox is more fun for me because it's so "hands on". I love getting my hands dirty editing text files for configuration.

---

### Post by teejay17 on 2007-02-07
> **RedSquirrel said:**
> Glad I could help. :)

As I mentioned back in that "Fluxbox, Anyone" thread, Fluxbox does take a bit of work to make it look exactly as you want, but that's one of the great things about Fluxbox: you **can** make it look *exactly* as you want (or pretty darn close, anyway) with just a bit of effort. [With some other environments you're sort of stuck with  things as they are since they're not as configurable.] 

Here are the links I used most often when I was learning how to configure Fluxbox:

Fluxbox Community Doc
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

Fluxbox-wiki
[http://fluxbox-wiki.org/index.php/Fluxbox-wiki](http://fluxbox-wiki.org/index.php/Fluxbox-wiki)

Fluxbox-wiki FAQ
[http://fluxbox-wiki.org/index.php/Faqs](http://fluxbox-wiki.org/index.php/Faqs)

Fluxbox Documentation
[http://fluxbox.sourceforge.net/docbook.php](http://fluxbox.sourceforge.net/docbook.php)


I also worked with that Fluxbox style guide from Arch linux (mentioned by dico). That's useful if you're going to get into configuring the contents of the style file itself, which you might want to do eventually.

And if you're interested, "Mr..Yeti" has made a Human style for Fluxbox. Check this out:

[http://ubuntuforums.org/showthread.php?t=317273](http://ubuntuforums.org/showthread.php?t=317273)

All you have to do with the "Human-fluxbox-style-0.1.tar.gz" file attached to that post is unpack it in your ~/.fluxbox/styles directory. Don't know if you like the Human theme, but I thought it was kind of a neat idea. In Fluxbox, I use the Operation style with IndustrialTango as the theme (most of the time).

Have fun!


PS - Oddly enough, I am using mostly XFCE these days since I decided one evening to download & install Xubuntu 6.10 for something to do. It's pretty good, but Fluxbox is more fun for me because it's so "hands on". I love getting my hands dirty editing text files for configuration.
Thanks! I am having fun. I take my time, go at it at my own pace, and that way there I don't find it overwhelming; these links you've provided are going to be great evening reads after work, and the experimentation afterwards will be real fun.
When I get really stuck I just boot back into (X)Ubuntu for a bit, to regroup and so on. 
I have used XFCE too, although on my particular little laptop (old laptop!) Fluxbox is the quickest yet. I have Ubuntu, Xubuntu and Fluxbox GUIs on it, and I didn't find there was that much difference between the slowness in Ubuntu and Xubuntu on this particular machine.
Maybe on another box I'll see more of a difference?

---

### Post by teejay17 on 2007-02-07
> All you have to do with the "Human-fluxbox-style-0.1.tar.gz" file attached to that post is unpack it in your ~/.fluxbox/styles directory. Don't know if you like the Human theme, but I thought it was kind of a neat idea. In Fluxbox, I use the Operation style with IndustrialTango as the theme (most of the time).
Really? So I just open the tar.gz file direct it toward that directory?
That style is so awesome!

---

### Post by teejay17 on 2007-02-07
Okay, I tried unpacking this Human theme directly to the Fluxbox styles directory (~/.fluxbox/styles directory) and now it doesn't seem to be present in the list. 
Perhaps I'm missing a step, or doing something incorrectly?

---

### Post by RedSquirrel on 2007-02-08
> **teejay17 said:**
> Thanks! I am having fun. I take my time, go at it at my own pace, and that way there I don't find it overwhelming; these links you've provided are going to be great evening reads after work, and the experimentation afterwards will be real fun.


Yeah, I found that reading throught the Community Doc was a good way to get started. After that, the Fluxbox Wiki is good since you can just read through the list of HOWTOs and the FAQ and try things out.


> 
When I get really stuck I just boot back into (X)Ubuntu for a bit, to regroup and so on.
I have used XFCE too, although on my particular little laptop (old laptop!) Fluxbox is the quickest yet. I have Ubuntu, Xubuntu and Fluxbox GUIs on it, and I didn't find there was that much difference between the slowness in Ubuntu and Xubuntu on this particular machine.
Maybe on another box I'll see more of a difference?It really depends on the hardware. I noticed a huge difference between GNOME and XFCE, the latter being much smoother. Everything about the desktop is quicker. For example, when I was browsing the menus in GNOME, they seemed to take a moment to load when I switched from one menu to another. In XFCE, there is no delay. My understanding is that Fluxbox is one of the **very** light window managers, whereas XFCE is *lighter than GNOME* but still may not be light enough for machines that don't have much RAM.


> Okay, I tried unpacking this Human theme directly to the Fluxbox styles directory (~/.fluxbox/styles directory) and now it doesn't seem to be present in the list.
Perhaps I'm missing a step, or doing something incorrectly?Hmmm...

Do you have a "Human" directory under the style directory?

**~/.fluxbox/styles/Human**

In the Fluxbox menu, there should be a menu item for "User Styles" or something like that. Unfortunately, I don't have Fluxbox on this computer at the moment, so I can't say exactly what it's called. The "User Styles" menu item has all of the styles that are in ~/.fluxbox/styles, and hence the Human style should be in there if everything worked correctly. The Human style will not be in the same menu list where the other Styles are (the ones that come with the Fluxbox package).


What did you use to unpack the tar.gz file?

I put the .tar.gz file in the ~/.fluxbox/styles directory and then I used a terminal like this:

```

tar xvzf Human-fluxbox-style-0.1.tar.gz 

```That should create the "Human" directory in the styles directory.

After that, I put the tar.gz file in another directory for safe keeping (otherwise the tar.gz filename will appear in your Fluxbox menu).

**Important:** remember to Restart Fluxbox to make sure the menu gets updated. (fluxbox menu -> Restart)

---

### Post by adamJ5 on 2007-05-18
BUMP!

This thread should be stickied!

---

