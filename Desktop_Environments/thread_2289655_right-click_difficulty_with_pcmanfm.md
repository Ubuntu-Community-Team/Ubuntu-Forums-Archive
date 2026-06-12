---
title: "right-click difficulty with pcmanfm"
date: 2015-08-05
forum: Desktop Environments
---

### Post by Shay_Walters on 2015-08-05
[I]I run Lubuntu 14.04 LTS.   When I use the right-click in the pcmanfm file manager, the context menu that comes up is often underneath the mouse pointer.  (But not always).    If it is, then when I release the mouse button, it selects whatever happens to be underneath the mouse pointer.  Sometimes this is just "Copy Path(s)", but sometimes it is "Move to Trash" or something else.
    How can I change the mouse-click action so that the context menu requires a separate click from the mouse to activate? 

[/I]

---

### Post by Rex Bouwense on 2015-08-06
I had a similar problem when I initially chose open files with one click.  I changed that option in preferences and that problem has disappeared.  Are you using the open with a single click option?

---

### Post by Shay_Walters on 2015-08-08
It was worth a try, but I was not using that option.   I tried turning it on and back off, but it didn't help.

---

### Post by tea for one on 2015-08-09
> **Shay_Walters said:**
> It was worth a try, but I was not using that option.   I tried turning it on and back off, but it didn't help.

What is your setting under:-

PcManFM > Preferences > General > Delay auto selection in single click mode?

My setting is 0.6 (if that is useful)

---

### Post by Shay_Walters on 2015-08-09
> **tea for one said:**
> What is your setting under:-

PcManFM > Preferences > General > Delay auto selection in single click mode?

My setting is 0.6 (if that is useful)

I have the "Open Files with single click" disabled, so that setting is greyed out, but I had tried it with several settings, and ended up leaving it at 1.00.   I just tried that again and enabling it and changing that setting seems to have no effect on the right-click action.   I don't have this problem on my laptop.  If I quickly hit the right mouse button, the context menu stays up there and allows me to make a selection with a separate click, so it must be some setting I've messed up on my desktop.    I'm starting to think that it's a system setting and that it shows up in pcmanfm because that's where I most frequently encounter the need to right-click.

---

### Post by tea for one on 2015-08-09
Yes - it's a bit baffling. 

Are you using the default theme because some themes are built with more care than others and you never know........?

Secondly, a system setting to double check, please have a quick look at:-

Main menu > Preferences Keyboard Input Methods > Advanced > Share the same input method among all applications.

I think that this should be ticked.

---

### Post by Shay_Walters on 2015-08-09
I am using the default theme and I do have that checked to share the input method among all applications.  I appreciate the thought.  I had most likely looked at that previously because I've been hunting for a solution to this problem for a while, but I don't think it would have occurred to me to try changing that setting.

  Do you know if there is a config file somewhere that might control the click actions or timings of the mouse?  It used to be that I would look for something like this under /etc/X11, but I can't keep track of where everything gets moved to.

If I'm careful and remember to do this, I can have the mouse moving to the left when I click it, and that way when the context menu pops up, it's no longer under the mouse pointer, and things operate correctly.  It's when the mouse is stationary or moving at all to the right, the context menu is under the mouse pointer and whatever happens to be under it  gets selected as soon as I release the mouse from clicking it.  (Usually too quickly for me to even read what got selected.)  The other thing I try to remember to do is to hold the mouse button down and make my selection before releasing it.  But I work with another OS at work and holding the mouse button down doesn't work there, so I can't really get myself trained to do this all the time.

---

### Post by vasa1 on 2015-08-09
If you're using the default version of PCManFM it should be 1.2.0. This version is still a gtk2 app. So you should be able to create a simple hidden text file in your home folder called *.gtkrc-2.0.mine*. If you already have this file, edit it to include this line:```
gtk-double-click-time=1000
```. If you're creating a new file, just the line should be enough. Save the file. Close other apps including PCManFM. Then restart PCManFM and see if you get any relief.

Take a look at Frank's posts here: [http://forum.lxde.org/viewtopic.php?f=8&t=501](http://forum.lxde.org/viewtopic.php?f=8&t=501)

There's also *gtk-double-click-distance=...*

---

### Post by Shay_Walters on 2015-08-10
Apparently I was mistaken about using the standard theme. I was using ClearLooks theme. Changing the theme back to Ambience fixes this problem. I finally found the answer here: [https://bbs.archlinux.org/viewtopic.php?id=141922](https://bbs.archlinux.org/viewtopic.php?id=141922)

and also here: [https://bbs.archlinux.org/viewtopic.php?id=95173](https://bbs.archlinux.org/viewtopic.php?id=95173)


Both of these mention fixing the problem by changing the theme.
I will try to figure out what aspect of the theme affects the mouse actions, but at least I don't have to deal with this issue while I look for it. Thanks to everyone who responded with suggestions.

---

### Post by Shay_Walters on 2015-08-10
Oops - spoke too soon.   Changing the theme changes how this acts, but I still get it happening sometimes, just not as often.  So I guess I haven't solved my problem after all.   Trouble now is that when it happens, it always seems to select "Move to Trash", so when I right-click on something, it disappears.  At least I know how to get it back.

---

### Post by tea for one on 2015-08-10
> **Shay_Walters said:**
> Apparently I was mistaken about using the standard theme. I was using ClearLooks theme. Changing the theme back to Ambience fixes this problem. I finally found the answer here: [https://bbs.archlinux.org/viewtopic.php?id=141922](https://bbs.archlinux.org/viewtopic.php?id=141922)

and also here: [https://bbs.archlinux.org/viewtopic.php?id=95173](https://bbs.archlinux.org/viewtopic.php?id=95173)


Both of these mention fixing the problem by changing the theme.
I will try to figure out what aspect of the theme affects the mouse actions, but at least I don't have to deal with this issue while I look for it. Thanks to everyone who responded with suggestions.

I mentioned the theme as a possible source of the problem because I have experienced odd mouse behaviour with themes in Gnome Shell. I have Ubuntu with Gnome Shell on my desktop and Lubuntu on my old netbook.

I use these themes for Lubuntu and so far so good. [http://www.ravefinity.com/p/download-ambiance-radiance-colors.html](http://www.ravefinity.com/p/download-ambiance-radiance-colors.html)

Anyway, it's always nice to solve these irritations and hopefully other users will benefit.

Kind regards

---

### Post by tea for one on 2015-08-10
> **Shay_Walters said:**
> Oops - spoke too soon.   Changing the theme changes how this acts, but I still get it happening sometimes, just not as often.  So I guess I haven't solved my problem after all.   Trouble now is that when it happens, it always seems to select "Move to Trash", so when I right-click on something, it disappears.  At least I know how to get it back.

That's a pity, I had hoped that this was solved. I do not have any more suggestions at the moment but I'm sure somebody else will try and help soon.

---

