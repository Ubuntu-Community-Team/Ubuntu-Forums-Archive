---
title: "Dual monitor hotkeys?"
date: 2006-07-08
forum: Desktop Environments
---

### Post by detrate on 2006-07-08
I've recently made the switch to ubuntu and I'm trying to get my setup up to speed.  I run dual monitors off a single ATi (sigh) video card and have gotten things ~pretty much~ the way I want them.

One thing I'm lacking however, is the ability to 'flip' a window from one monitor to the other, an ability I had on windows via my dual monitor management program "UltraMon".

This is quite and annoyance for me because I've become reliant on the feature.  I've done searchs relating to ubuntu, x, xorg.conf, gnome, etc. and have sadly yielded no answers.  The closest I've come is window placement upon opening of an application through xorg.conf.

So I ask you forum, is there hope?  Can I configure my window management to use a hotkey to 'flip' my applications?

---

### Post by orb9220 on 2006-07-08
The closest to what you describe is to right-click title bar of window which gives you move to workspace right or left.

But if you mean display 0 or 1 in same workspace then I know I can't because they are not seperate monitor.

Twinview on Nvidia means one giant desktop of 2560x1024 over two display's.

And I still haven't read even about setting up actual two display with different resolution's and actual 2 monitor's

Good luck.

---

### Post by detrate on 2006-07-09
unforutunately, I do want to go from screen 0 to screen 1, not switch workspaces.

---

### Post by RawMustard on 2006-07-09
The only thing you could do is set where certain windows open by using devilspie I think, window management in gnome is quite pathetic for dual screen users :(

---

### Post by detrate on 2006-07-09
Thanks RawMustard but that doesn't really do the trick...

I don't mind changing window managers if it means I can gain this ability.

---

### Post by Wolki on 2006-07-09
Superswitcher has this functionality in 0.3:

[http://www.gnomefiles.org/app.php?soft_id=1231](http://www.gnomefiles.org/app.php?soft_id=1231)

It's a pretty nifty program, allowing you to do all sorts of cool tricks with windows, but it will steal your super keys, so you will lose keyboard shortcuts you have put there.

You probably can do a similar effect with wmctrl, but since I don't have a double screen (and thus no clue how exactly they work), I can't really help you with that.

---

### Post by detrate on 2006-07-09
Superswitcher looks nice... but it's not really what I need. I need to move applications from monitor to monitor, not workspace to workspace.

---

### Post by TheMono on 2006-07-09
In the new features added to it, it lists <super><super> as being a hotkey to switch a window from one screen to another, not one workspace to another.

Could be what you're looking for?

---

### Post by detrate on 2006-07-10
After grabbing the dev packs nessecary to build superswitcher, I did a make, make install and tried the bin.  Much to my dismay, the super buttons had no effect, workspace options included.

I'm pretty sure this has to do with my keyboard, a logitech mx duo that is currently running of ubuntu's default drivers.

Can anyone confirm / deny these alegations before I go ahead and royally mess up my system trying to get my logitech drivers to work? :-P

**EDIT**: I just set my xorg.conf to run off drivers similar to my keyboard as suggested on [this page](http://docs.tenshu.net/Logitech-MX-Duo-mini-HOWTO/x26.html), however the results are still the same.  My super (windows) keys do not seem to be working.

---

### Post by Wolki on 2006-07-10
First, try to disable numlock and see whether it works then - I have that problem with superswitcher, and some other people too, but appartently not everyone.

Then, try playing with the Alt/Windows key options in the kayboard control panel, they might help.

---

### Post by larrybrazos on 2007-09-26
i am looking for this functionality also.  ultramon is amazing for hotkeys and dual monitor management.

since xorg.conf sets it up as one large screen, i am not sure how you would let it know to bounce from screen to screen.

for those of you familiar with ultramon and linux development, what would it take to make an ultramon-like porogram for linux where each desktop is considered sepearte or considered together, but you have the ability to hotkey windows back and forth?

---

### Post by detrate on 2007-11-29
> **larrybrazos said:**
> for those of you familiar with ultramon and linux development, what would it take to make an ultramon-like porogram for linux where each desktop is considered sepearte or considered together, but you have the ability to hotkey windows back and forth?

If this was created I might switch back.

:popcorn:

---

### Post by mellocello2003 on 2007-12-07
I've been looking for something that does this as well.  Did people have a good experience with superswitcher?  Looking at the docs, it doesn't seem to do the trick.

I found something online that may be able to get people this kind of functionality, but the paradigm seems a bit different.  It's still workspace oriented, but it has the concept of binding screens to different workspaces.  Apparently it's not fully supported in Gutsy, but it is in Hardy.
EDIT:  I figure that this means, using xmonad, one could bind workspace 1 (containing window A) to screen 1 and bind workspace 2 (containing window B) to screen 2.  Then, the two could be flipped, effectively mimicking the "move window to next screen" functionality in Ultramon.

[http://www.xmonad.org](http://www.xmonad.org)

[http://packages.ubuntu.com/hardy/source/xmonad](http://packages.ubuntu.com/hardy/source/xmonad)


I'm going to try to see if I can get it working on Gutsy when I go into work on Monday...


If anyone hears anything about getting an Ultramon like functionality in Ubuntu, let me know!!  I came to rely on it heavily when I did software development at my previous job, and now I want the same type of functionality in Ubuntu linux at my current job.

---

