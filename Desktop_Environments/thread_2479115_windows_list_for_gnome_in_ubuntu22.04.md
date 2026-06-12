---
title: "windows list for gnome in ubuntu22.04"
date: 2022-09-14
forum: Desktop Environments
---

### Post by centguy2 on 2022-09-14
what is the extension of gnome3 that has Windows List at the bottom of the screen for Ubuntu22.04?
 This is to allow a simple 
switch to a window with a mouth click. Eg., Currently I need to go to Terminal on the dock, and click on the Terminal to show all Terminal and then choose. This is so inefficient and annoying in the long run.

Or there is already a good substitute for Windows List that I do not know? Also I can switch between workspaces with a mouse click.

All these are the useful features in the ubuntu20.04 and they are still working well. I hope gnome retain good base without relying too much on the extension, which come and go and this
upset users sometime.

---

### Post by deadflowr on 2022-09-15
Window List is part of the gnome-shell-extensions package.
Among other extensions.
gnome-shell-extensions are extensions created by gnome developers.

I've never done a mouth click, is it easy?

---

### Post by tea for one on 2022-09-15
> **centguy2 said:**
> what is the extension of gnome3 that has Windows List at the bottom of the screen for Ubuntu22.04? 
Show Applications > Extensions > Built In > Window List
Or use the search facility within Extensions

---

### Post by centguy2 on 2022-09-18
When I first use Activities to search for extension, there was no result with extensions ( may have to check this again on another 
Ubuntu 22.04 installation on another computer). 

But from the help, I did 

apt install gnome-shell-extensions

and indeed it works!

To get it work properly, it seems I need to log out and log in.

Now Activities -> Search show  Extensions, which is great,

Then I find the Windows List as mentioned. Hurray!!! this put me back to the good old gnome2 day experience.

Thank you. I am starting to like Ubuntu more and more (was using CentOS for 10+ years until it was basically killed)!

---

### Post by deadflowr on 2022-09-19
Ubuntu desktop only ships with 3 extensions, ubuntu-dock, appindicator, and desktop icons.
>  this put me back to the good old gnome2 day experience.
If gnome2 experience is sought just use the mate desktop.

---

### Post by pantazi on 2022-09-19
> **deadflowr said:**
> 

I've never done a mouth click, is it easy?

Lisp?

---

### Post by tea for one on 2022-09-19
> **deadflowr said:**
> Ubuntu desktop only ships with 3 extensions, ubuntu-dock, appindicator, and desktop icons.
Yes, thank you - absolutely correct.
I'm sure that I successfully managed to confuse centguy2 with my erroneous conviction that gnome-shell-extensions were part of the default installation.
Apologies for the faux pas.

[COLOR="#0000FF"]gnome-shell-extension-manager[/COLOR] is also a useful package.

---

### Post by centguy2 on 2022-09-19
Using MATE is like going backward for me.  I want a good old functional gnome2 desktop features (super good for productivity) and to move on 
with time with Gnome3+great extensions     which should be the way forward.   It seems the gnome-extensions has totally 
replaced the gnome-tweaks thing which is a bit messy in ubuntu20.04.   

I hope Dash to Dock  is also considered a built-in since it is a super nice feature!   Right now it seems the user has
to work a bit harder to get this going. (At least I still to work on it I think).   ... or may be not, it may have been in the lastest gnome-extension by default 
already. (I am still using ubuntu 20.04 here so I have to boot to ubuntu22.04 to confirm).

---

### Post by centguy2 on 2022-09-19
*I've never done a mouth click, is it easy?*

Try it and it should be clear. If not, write back to ask. 

A mouse click can maximize and minimize a window at will. This is mandatory for a person (like me) who uses a least separate 5 windows daily and switching windows is a must have feature (to save time and to allow me to focus)!

---

### Post by centguy2 on 2022-09-19
It is a click on any  tab on the Window List at the bottom of the Desktop.

---

### Post by centguy2 on 2022-09-19
Oh great, on Ubuntu22.04, the Extensions already included  Ubuntu Dock, which is exactly the Dash to Dock thing I need. 
So the extensions has everything we need, there is no need to download tweaks, and configure Dash to Dock!

Cool!

---

### Post by centguy2 on 2022-09-19
One last thing, to configure Dash to Dock, we need to first enable it in Extenisons-> Ubuntu Dock.

And then go Settings-> Appearance -> Dock and there will be a bunch of things we can change. I like to put the dock on the Right side. and change the icon size.

But to put the dock customization in the Settings -> Appearance is a bit strange. If I have not used Dash to Dock before I won;t know where to find it!

---

### Post by centguy2 on 2022-09-20
On another installation of ubuntu22.04 I realize why I was so confused by all this business. 
Apparently I have searched for `Extension' in activities and somehow Extension Manager shows up
and I installed/ran Extension Manager 0.3.0
which does not show Window List since I had not gotten it through gnome-shell-extensions.
Search Activities with `Extension' is supposed to ideally show gnome-shell-extensions but it does not.

Once I have installed gnome-shell-extension, now it appears two very similar apps are doing the same
job: Extension Manager 0.3.0 and Extensions 42.4.  I think they better make up their minds which one to 
support because having redundancy is just so confusing.

---

### Post by vanadium on 2022-09-20
> **centguy2 said:**
> 
Once I have installed gnome-shell-extension, now it appears two very similar apps are doing the same
job: Extension Manager 0.3.0 and Extensions 42.4.  I think they better make up their minds which one to 
support because having redundancy is just so confusing.
Free software is not centralized. These two apps are totally different projects. "Extensions 42.4" is kind of "official" (Gnome) and provides functionality that formerly was exposed in Gnome Tweak. "Extension Manager 0.3.0." is a very recent project that allows to search extensions from an app instead of using the Gnome Shell extensions website, and in addition provides the functionallity of "Extensions". It was quickly adopted in the Ubuntu 22.04 Universe repository because it allows to do what the snap version of Firefox could not do anymore.

---

### Post by ActionParsnip on 2022-09-21
ALT + TAB then click a window...does that work OK?

---

### Post by Dennis N on 2022-09-21
> Also I can switch between workspaces with a mouse click.
For this, I use the gnome-shell extension "Workspace Indicator".

---

