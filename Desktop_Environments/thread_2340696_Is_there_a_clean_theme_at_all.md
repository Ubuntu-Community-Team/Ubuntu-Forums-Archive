---
title: "Is there a clean theme at all?"
date: 2016-10-21
forum: Desktop Environments
---

### Post by Loggy on 2016-10-21
For a long time I have been running an ancient 32 bit 8.04 LTS Kubuntu, which I had nicely set up so if it ain't broke, don't fix it.  

Memory problems and other issues have got the better of me so I bit the bullet and upgraded to 64 bit Kubuntu 16.04 LTS. 

I can't get a clean desktop - I use 4 workspaces, twin screens and usually have quite a lot of xterms open as well as documents, editors, browsers etc.

I tried Unity to start with but among other things, the animation annoyed me so much that I ran back to a fresh Kubuntu install.

I've browsed all the themes (although not tried them all) but they all appear to make things more messy, which gets in the way of thinking and work, rather than simple, sharp and clean

I want:

1) To have a white 255,255,255 background with black font 0,0,0 in all windows (xterm, browser, LibreOffice etc) not a murky muddy white and dark grey font that makes me check my glasses all the time and peer closely to see what I've typed,

2) To have a simple outline round each window so I can see which is which then they overlay becauseh there is no delimitation on my present theme (Oxygen),

3) To have the Task Manager ribbon (which I have at the top) stretch across both screens (they are identical).

Most things can be customised but for this sort of detail, the options for each theme item are just a dropdown of the options from the list of themes that I have downloaded.

Short of investing in a new video card and a 4K screen, is there a simple way to do this?  A file that can be edited and not overwritten with updates?

---

### Post by vasa1 on 2016-10-21
> **Loggy said:**
> ...
Most things can be customised but for this sort of detail, the options for each theme item are just a dropdown of the options from the list of themes that I have downloaded.
...
What does that mean?

Why don't you find a theme that comes *closest* to what you want and then tweak that? I'm assuming you aren't using one of those newer "compiled" themes.

---

### Post by Loggy on 2016-10-21
@vasa1 I am using Oxygen v 0.9 which is indeed the closest that I can find so far.  

Clicking on All Setting > Appearance > Desktop Theme > Details tab and selecting Oxygen there are a series of dropdowns for Colour Scheme, Panel Background, Kickoff etc.  The source offered for each of these on the right is a list of the corresponding items for the (8) themes I have installed, plus a File option.  

I have installed the extra themes from the Get New Themes button but selecting and Applying one doesn't make that theme available in Appearance - only the default Breeze and Breeze Dark are there and .config/kdeglobals file doesn't change.

I don't want to modify the kdeglobals file because that would be changed if anything was updated.

---

### Post by ajgreeny on 2016-10-21
Your new version of Kubuntu is nothing like the one you used in Kubuntu-8.04, which used KDE 3.5.9 (I think that was the version) instead of the KDE Plasma 5 DE of 16.04.

If you would really like something that looks and acts the same as Kubuntu-8.04 it might be worth you looking at Trinity desktop, details of which are shown in the Askubuntu page at [http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available) and which is a new fork of that older version of KDE.

It is not available as an iso image file which you can then install from a DVD or USB, but is simply a PPA repository (details in that link) which you can either add to an installed *ubuntu OS, or you can if you think you are able to deal with a command-line install, add trinity to a minimum install iso which you can get from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD).

This is the way I did it in a virtual installation in VBox, just out of interest, as I used to like KDE 3.5.9, but having been using Xubuntu for many years I now find that I do not like KDE 3.5.9 as much as I used to.  You could also. of course, move to another DE such as the XFCE in Xubuntu which you could easily configure to look as clean and simple as you wish.  Worth considering perhaps?

---

### Post by buzzingrobot on 2016-10-22
I've found themes added via Get New Themes may not show in the list until the Settings tool is restarted.  Some may not show at all.  My guess is that not all old KDE4 themes are compatible with Plasma 5. (Oxygen was rewritten). AFAIK, all those themes are pulled from the kde-looks.org site. (The Slim Glow theme works well for me.)

If you do resort to playing with KDE config files, you'll likely find they're in different locations.  Plasma 5 is incompatible with KDE4 and there's no supported upgrade path.

The Q4OS distribution uses Trinity on a Debian Stable base.

---

### Post by Loggy on 2016-10-27
Many thanks @ajgreeny and @buzzingrobot.  Trinity fits the bill - nice and clean look to it.

I did have a clash with an image that was owned by KDE.  I will dig out the reference and post a mesage on the Trinity forum.

I also downloaded a mini.iso and xubuntu which I will try in a VM when I've a moment or three.

---

