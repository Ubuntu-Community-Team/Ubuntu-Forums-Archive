---
title: "Battery indicator icon broken? (also theme &amp; icon questions)"
date: 2013-06-05
forum: Desktop Environments
---

### Post by Catslothloaf on 2013-06-05
Hi. I've been using Xubuntu for about a week now and I have a little problem. My battery status icon is a placeholder. I'm on a desktop, so I don't always see a battery indicator icon, but when I plug in a something like an iPhone, this is what I see:
  [IMG]http://i42.tinypic.com/25ipvue.png[/IMG]

That little rectangle with the no sign. 

I know I can turn off the power indicator permanatly, but I'd rather  have an indicator icon that works and looks congruent with the rest of  its' set. Can anyone help me? Im running Raring Ringtail on a Dell  Optiplex 700 series. Latest updates installed. This is a fresh system  install. I had 12.04, but I made a Raring Ringtail install disc and selected 'erase everthing and install xubuntu'. I had this same problem in 12.04, too. 

*I looked in the usr/share/icons and all the battery icons seem to be there. I also found that if I set my power settings to always display an icon, the 'battery full' icon shows up just fine. But when I plug in my phone, I get the broken placeholder icon again. It looks like there is a special 'iPhone and battery' icon in the elementary-xfce icon folder, but even when I select elementary-xfce as my icon set, the icon displayed is the same. I don't know anything about Unix-like OS's. Is there some way I can check the path that the indicator plugin uses to find the icons it displays? 

**PS**

A few icon & theme questions, if anyone would be so kind as to address them, too:

-Is it normal for the other included icon sets (humanity, GNOME, etc) to  be.. incomplete? For example, with GNOME, five out of the nine launcher  icons on my lower dock are the same kind of placeholder icon as that  seen on power indicator, and the sound indicator icon looks the same,  too. 

-Can anyone recommend me some good icon sets and / or themes that I can  download? I have XFaenza and enjoy it, but it's also the only one I've  found so far that didn't have at least three placeholder icons that seem  like they should be something else.

-Will my mail indicator always be blue as long as there are any unread messages in my gMail inbox? Even when I've 'read' every message from the past several days?

---

### Post by ohnonot on 2013-06-07
take a look at your icon sets, they have an index.theme file with a line 'inherits=...' - this points to other icon themes, usually gnome or hicolor. do you have both gnome and hicolor installed?

---

### Post by Catslothloaf on 2013-06-07
Thanks for the reply.

I checked the index.theme of the  elementary-xfce icon set, which is the set I was using when I first  noticed the problem. The inherits -gnome & hicolor- were both  declared in the file. I checked my installed packages, and hicolor and gnome were  both there.

Here is a screenshot showing what I described. But  notice my panel icons; this is what they look like with the GNOME icon  theme enabled. With elementary-xfce enabled, all of the grey rectangles  on the bottom panel show unique icons, but the grey rectangle on the top  panel shows a placeholder just as it does here.  (Although it's cut off, you can still see it in the upper right [workspaces -> _placeholder icon_ -> network indicator icon -> bluetooth indicator icon -> time -> edge of screen])[IMG]http://i.imgur.com/kOrlT4R.png[/IMG]

I am going to install the package [FONT=courier new]gnome-icon-theme-full[/FONT] [FONT=arial]in  addition to what I have now. Perhaps that will help.. although I'm  skeptical of it doing anything to fix the battery icon issue. After all,  the battery icon .png's are in my icons folder...

Any more ideas?

EDIT: Getting the full GNOME icon package fixed (most of) the broken application icons, but not my battery icon!
[/FONT]

---

### Post by ohnonot on 2013-06-08
which battery indicator? xfce4-panel plugin or sth else?
maybe it uses a different icon for phones than laptop batteries?
it is a peculiar problem though. have you tried xfce forums?

---

### Post by Catslothloaf on 2013-06-08
Yes, it's indicator plugin for the xfce4-panel package. 

I tried installing a number of additional gnome icon sets from synaptic, to see if any of their battery icons would work. I also installed some gnome themes because I wanted to see what they looked like. Strangely, after installing a number of these icon sets and themes (about 10, all at one time, which was probably a bad idea) the battery icon returned. But- my other icons (indicator and application) shrank, weidly enough. My batter indicator would be 'normal' sized but everything else would be half that size. 

Also weirdly, while the elemetary-xfce theme displayed the battery indicator icon that resided in it's //share/icons directory, when I selected Faenza-xfce, the battery indicator icon would become the 'fallback' GNOME theme battery icon. 

I decided this wan't a sufficent improvement and uninstalled all the theme and icon packages I had just download, and rebooted. That fixed the weird icon size difference, and elementary-xfce gave the met right battery icon and everything was the right size! Faenza still showed the GNOME battery indicator icon, though. Then, when I rebooted again, the battery indicator was re-broken. Back to square one. :(

I am going to check out the xfce forums and see if anyone there can help me. Thanks for the tip, and for taking a crack my issue.  

Oh, and I want to be clear that by battery indicator icon was failing to appear as soon as I finished the Xubuntu installation process- before I downloaded any additional applications or changed any settings. I think the only thing I had done before noticing the problem was set up Thunderbird and browse a few mainstrem websites. I would consider that my Xubuntu installation was corruped, but as I said, this problem occured on my previous and otherwise completely (afaik) functional Xubuntu 12.04 installation, and I chose the 'erase everything and install Xubuntu' option when I installed my current version.

---

### Post by ohnonot on 2013-06-09
no, your install is not corrupted :-)
the way gtk and the whole icon thing works is incredibly genius because it allows for customization far beyond what other operating systems offer.
so, there's a bazillion of user made icon themes, none of them is 100% complete (that's where the inherit thing comes in), but they all adhere to (more or less) the same standards, so when you change your icon theme, all (more or less) applications know where to look for the appropriate icon.
this doesn't always work 100%.
i think it would be interesting to know what the indicator shows when you have a laptop battery, but afaiu yours is not a laptop...
if you could find out (most probably on xfce forums) what icon the plugin is looking for, and if it's looking for a different icon when you plug in a phone...

---

