---
title: "Lubuntu scrollbar width (again)"
date: 2013-09-16
forum: Desktop Environments
---

### Post by kimble2 on 2013-09-16
My question is the same as [http://ubuntuforums.org/showthread.php?t=1853165](http://ubuntuforums.org/showthread.php?t=1853165) (2011, now closed) - 
how can you increase the scrollbar width. The answer given is to choose a theme with a wider scrollbar, but no theme-name is mentioned, and I can't find any that have a wider scrollbar in Lubuntu-13.04.

From memory, I have seen the scrollbar slider drawn as 3 .png files, "top", "middle", and "bottom" - middle being stretched as appropriate. But I can't find where these are now.

---

### Post by vasa1 on 2013-09-16
[B]I suggest you or a mod edit the title of the question to remove "openbox" and use Lubuntu instead.
[/B]> **kimble2 said:**
> My question is the same as [http://ubuntuforums.org/showthread.php?t=1853165](http://ubuntuforums.org/showthread.php?t=1853165) (2011, now closed) - 
how can you increase the scrollbar width. The answer given is to choose a theme with a wider scrollbar, but no theme-name is mentioned, and I can't find any that have a wider scrollbar in Lubuntu-13.04.

From memory, I have seen the scrollbar slider drawn as 3 .png files, "top", "middle", and "bottom" - middle being stretched as appropriate. But I can't find where these are now.
The .png files are in path-to-theme/gtk-2.0/images. I don't know about gtk-3.0 apps. I stopped using the theme as soon as I realized images would need to be edited.

I suggest you try out **Greybird** which is part of **shimmer-themes** from the software center. This theme allows you to modify a lot of things by editing text files rather than editing images.

Make a copy of /usr/share/themes/Greybird to ~/.themes. Rename ~/.themes/Greybird to something else like "MyGreybird" to reduce confusion. Edit ~/.themes/MyGreybird/gtk-2.0/gtkrc to modify
```
	GtkScrollbar		::slider-width				= 9
```
This line is present in the

####################
## Default Styles ##
####################

section near the top of the file.

Then, edit ~/.themes/MyGreybird/gtk-3.0/gtk-widgets.css in the /* default */ section (near the top of the file) to modify the values in one or both of  
```
    -GtkScrollbar-slider-width: 9;
```
and
```
    -GtkRange-slider-width: 9;
```

You may need to switch themes back and forth or even log out and back in to get the changes to take effect.

Edit: Please note that when you install the shimmer-themes package, apt-get will also want to install a theme "engine" (gtk2-engines-murrine). That is necessary.

---

### Post by kimble2 on 2013-09-16
Thanks for that detailed help.
Does it imply that I first drop Openbox in favour of metacity/compiz?
I have tried that before and got into such a horrible mess that I had to reinstall Lubuntu.
Maybe that's where I (vaguely) remember the .png files from.

---

### Post by vasa1 on 2013-09-17
> **kimble2 said:**
> ...
Does it imply that I first drop Openbox in favour of metacity/compiz?
....
Sorry, I did not meant to imply in any way at all that you should drop Openbox. I just meant to say that "openbox" has nothing to do with the question as far as I can tell.

By the way, if the advice proffered solved your issue with the scrollbar width please mark the thread SOLVED. If it hasn't solved your issue, what problem as you still facing?

---

### Post by kimble2 on 2013-09-17
OK, it's my confusion that's the problem.

I think I've cracked it now:
sudo leafpad /usr/share/themes/*Lubuntu-default*/gtk-2.0/scrollbar.rc
Edit GtkRange::slider-width = 20
Logout
Login

This at least works for LX apps, Firefox and Thunderbird.
It doesn't work with any of my K apps, but that's OK as they were wider anyway.

---

### Post by vasa1 on 2013-09-17
> **kimble2 said:**
> OK, it's my confusion that's the problem.

I think I've cracked it now:
sudo leafpad /usr/share/themes/*Lubuntu-default*/gtk-2.0/scrollbar.rc
Edit GtkRange::slider-width = 20
Logout
Login

This at least works for LX apps, Firefox and Thunderbird.
It doesn't work with any of my K apps, but that's OK as they were wider anyway.
That's great. I never thought of editing the file you did.

---

