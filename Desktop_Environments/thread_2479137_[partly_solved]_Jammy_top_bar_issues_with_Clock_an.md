---
title: "[partly solved] Jammy: top bar issues with Clock and font colour"
date: 2022-09-15
forum: Desktop Environments
---

### Post by col48 on 2022-09-15
Fresh install of Jammy, now down to the annoying relatively trivial things.

I added Tweaks, Applications indicator, Places Status indicator.

I am using a user theme (ie gnome-shell.css) for the top bar which looks like this:
```
#panel {
  color:black;
  font-size:18px;
  font-weight:bold;
  background-color:green;
  height:3.50em;
  }
```(OK in reality I don't want it quite this big, but this size exaggerates the issue so I can see it clearly)
But:
issue 1. all the text in the top bar is white - or maybe a very pale pink - not black.
issue 2. although the font size generally is set by the theme, that for the Clock seems to be fixed at 12px - a bit too small for me.

Issue 3. Clock seconds.
I also would like the Clock to show seconds, but even with Tweaks>Top Bar>Clock seconds set to true it does not do it.  I've also used dconf-editor to try to set what is probably the same flag - no difference.

All in one thread in case they are connected.

---

### Post by col48 on 2022-09-18
I have found a solution for Issues 2 and 3.

Issue 1: the css reference at [www.w3schools.com>cssref>color]("https://www.w3schools.com/cssref/pr_text_color.asp") suggests this should be the key which would change the text colour. But in the context of top bar themes, it doesn't - the reference is of course about css for websites not this rather special context.

Perhaps this issue is insoluble with the tools to hand.

Issues 2 and 3: I added the Gnome extension 'Date Menu Formatter'.  This has settings for the font size for the clock as well as a variety of options for the display of date and time information.  The information panel which shows the options is incomplete in one crucial regard for Option 3.  It is possible to show seconds with ss (eg hours and minutes and seconds  k : mm : ss).

---

### Post by Dennis N on 2022-09-18
For the clock, you could have set the seconds to display in Tweaks > Top Bar > Clock.

Using the new Yaru themes as an example, the font color and size are set in this section of gnome-shell.css, so look there.

```
/* Global Values */
stage {
  font-size: 12pt;
  color: #F7F7F7; }

```

In 22.04, only the Yaru themes will use the accent color selected in Appearance > Style, so if you use some other theme, you loose this feature.

---

### Post by col48 on 2022-09-19
@Dennis N
I have no idea why, but *for me* the settings in Tweaks > Top Bar > Clock were not affecting the display (even after a Reboot) which is why I was trying other options.
Thanks for the tip about Yaru.

A great feature of Linux is that there is usually more than one way of doing things, so if one approach does not bear fruit, there are others to try.

---

### Post by BlueAZ on 2022-10-19
Hi,   I've been searching for a way to make the top bar icons big enough to see, ever since I fresh-installed Jammy.  Why are they so tiny by default?  Is no one else over 40?!

Saw your ref to Date Menu Formatter, took a look, and it does have features I want.  Downloaded the zip package, unzipped, tried to install, no dice.  I'd already checked for it in Ubuntu Software; it's not there and it won't install from the downloaded package.  Tried Synaptic, no dice.  Tried in Terminal, no dice.  Why is this so hard?  How can I install this????

---

### Post by Dennis N on 2022-10-19
> **BlueAZ said:**
> Hi,   I've been searching for a way to make the top bar icons big enough to see, ever since I fresh-installed Jammy.  Why are they so tiny by default?  Is no one else over 40?!

Saw your ref to Date Menu Formatter, took a look, and it does have features I want.  Downloaded the zip package, unzipped, tried to install, no dice.  I'd already checked for it in Ubuntu Software; it's not there and it won't install from the downloaded package.  Tried Synaptic, no dice.  Tried in Terminal, no dice.  Why is this so hard?  How can I install this????

To find and install gnome-shell extensions, you should be using gnome-shell extension manager. You can install this from Ubuntu Software. Use the one the arrow points to in the image.

---

### Post by col48 on 2022-10-20
@BlueAZ Dennis N got there first - no need to download a zip, what he illustrates did it for me.

---

### Post by BlueAZ on 2022-10-20
> **Dennis N said:**
> To find and install gnome-shell extensions, you should be using gnome-shell extension manager. You can install this from Ubuntu Software. Use the one the arrow points to in the image.

Thanks Dennis N!  I was able to install the extensions manager and have explored it.  When I found the place it looked like I could enlarge the top bar icons, I tried it.  If I made it even one point bigger, the icons just disappeared.  Tried logging out & back in, still just little dots where my icons should be.  Oh well.  Any other suggestions?

---

### Post by Dennis N on 2022-10-20
> Oh well. Any other suggestions? 
When the font size in the code block shown in post #3 is increased, I think the width of the top bar increased and the icons resized.  For the Yaru gnome-shell themes, each theme has a [FONT=Courier New]gnome-shell.css[/FONT] file. The code shown is in that file. The gnome-shell themes are in [FONT=Courier New]/usr/share/gnome-shell/theme[/FONT]. 

The downside is that increasing the font size increases it everywhere else controlled by gnome-shell, like top bar menus and desktop notifications.

---

### Post by col48 on 2022-10-21
For what it's worth, this is what I have done which tweaks the underlying Yaru theme, affecting the top panel (where the 'Activities' 'Applications' etc headings sit along with the Clock and mini-panel for LogOut etc).  I don't know if it would work for any other theme...

0. The Gnome Tweaks Extension has been installed
1. Let's call the theme variation JamToday
2. Create $HOME/.themes/JamToday/gnome-shell/gnome-shell.css
This file looks like this (I haven't changed this since the original post!)
```
#panel {
  font-size:18px;
  font-weight:bold;
  background-color:green;
  height:2.50em;
  }
```
3. Now in Applications>System Tools>Tweaks>Appearance there are some dropdown  entries.  The wider, RH one for Shell should drop a list of Yaru based themes with JamToday at the top, although it may be that the very first time you have to navigate (using the narrower, LH, dropdown) to the file created just now to add it to the list (I can't remember).  I have not experimented with any of the other dropdown settings.

I have not touched the original Yaru theme files.

PS I'm over 40, too.  By a long way.

---

