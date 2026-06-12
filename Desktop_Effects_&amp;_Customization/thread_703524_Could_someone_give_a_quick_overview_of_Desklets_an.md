---
title: "Could someone give a quick overview of Desklets and Screenlets?"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by PiggiePaul on 2008-02-21
I've heard about these and seen some examples, but I'm not really sure where a Desklet ends and a screenlet begins.

I've seen things like Weather reports, Computer info, etc, just on the screen somewhere (a bit like the new bar in Windows Vista, but anywhere on screen rather than in a column on the right) 

Then, I've also seen things that look like the bar at the bottom of a Apple iMac screen (Basically, just very pretty quick launch icons)

Now, I'm not really sure which is which, (or they can cross over function?)

And/Or how you go about getting them?

The custom icons sets, and/or the areas to put them on.

Like, I can just drag out some BIG icons and put them along the bottom of the screen to make it look a bit like an Apple, without doing anything. (albeit they don't bounce up and down like the iMac icons do)

So, anyone feel like a little explanation of what's what, and if/what software you need to actually host these icons/features in the 1st place?

Thanks :)

==== EDIT =====

Oh and are Widgets ubuntu related to? or are OUR versions just called Desklets and Screenlets?

---

### Post by chipants on 2008-02-21
desklets and screenlets pretty much serve the same purpose. the provide "desktop widgets" much like OS X's dashboard. these widgets are usually small and simple, single-purpose graphical tools. as you mentioned, weather forecasts. there are also calculators, rss readers, system performance graphs, media player integration tools, and all sorts of things.

choosing which you want to use is more a matter of personal preference. gdesklets is available in the repos. i personally find gdesklets to be less polished than other solutions. also, there aren't as many quality gdesklets available as other similar frameworks.

i use screenlets on my system. ([http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home))

i find that screenlets are more stable, and easier to configure than the alternatives. i don't believe screenlets are in ubuntu's repositories. however, following the instructions on the aforementioned website, you can easily install screenlets (and stay up-to-date) via their own repositories.

---

### Post by spiderbatdad on 2008-02-21
Desklets are at least functional, in fact you have several available to add to your panel, such as weather report, or system monitor. gdesklets is in synaptic to offer you some applets which are functional and add "eye candy" if you can still call them that. Screenlets seem to be entirely useless. Like clutter on your desktop. Some folks just can't work in a clean environment and need stuff lying around...thus you have screenlets. I think you can stiil get them at getdeb.net. They are not stable and even less so in a composite environment.

Widgets are entirely different. Though some operating system refer to them as if they were desklets. In terms of GTK they are the aspects of the panels and menus...the gui really.

---

### Post by chipants on 2008-02-21
almost forgot to mention the apple dock-like things.

well, there are definitely widgets (screenlets) available that let you add launchers. however, these are generally not very polished or well-integrated into gnome.

if you want a quick launcher/task manager similar to OS X's dock, i would recommend using AWN (avant window navigator). there are alternatives, but AWN seems to be the most reliable and customizable right now. you are able to add launchers by simply dragging menu items into the dock. also, you can add 'applets' to the dock, which are similar to desktop widgets/screenlets, except for the fact that they reside in the dock only.

installation instructions are here: [http://wiki.awn-project.org/index.php?title=Installation](http://wiki.awn-project.org/index.php?title=Installation)

---

### Post by northern lights on 2008-02-21
Screenlets/Desklets are equivalent to Widgets. Personally I don't like such stuff - clutters your desktop, hogs resources. Still, you can get 'em [here]("http://www.screenlets.org/index.php/Home").

The "mac-like thingy" on the bottom is not screenlet by definition (gdesklets had something like it, dunno maybe screenlets also do) - it's a dock. Opposed to the dang weather report (I have a window) or the daily joke, a dock is quite useful. I don't wanna deny the existence of kiba-dock and AWN, but in my opinion cairo-dock is by far the best. Download [this]("http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.5.1_i686-32bits.deb") and [this]("http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.1_i686-32bits.deb") package, install 'em (easiest way would be choose "Open With GDebi package installer" when downloading, should that not be installed either, you can do so via "Add/Remove..." in the "Applications" menu) and start the dock with "cairo-dock".

---

### Post by PiggiePaul on 2008-02-21
> **chipants said:**
> desklets and screenlets pretty much serve the same purpose. the provide "desktop widgets" much like OS X's dashboard. these widgets are usually small and simple, single-purpose graphical tools. as you mentioned, weather forecasts. there are also calculators, rss readers, system performance graphs, media player integration tools, and all sorts of things.

choosing which you want to use is more a matter of personal preference. gdesklets is available in the repos. i personally find gdesklets to be less polished than other solutions. also, there aren't as many quality gdesklets available as other similar frameworks.

i use screenlets on my system. ([http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home))

i find that screenlets are more stable, and easier to configure than the alternatives. i don't believe screenlets are in ubuntu's repositories. however, following the instructions on the aforementioned website, you can easily install screenlets (and stay up-to-date) via their own repositories.

Thanks, will take a look at your link.

So, do I take it, these things are not compatible with each other, and you have to choose the system that uses it own TYPE of screenlet/desklet?

Is there no Standard format that some adhere to?

Obviously I'd like to choose the system that had the most graphically "Polished" versions.

---

### Post by chipants on 2008-02-21
> **spiderbatdad said:**
> Desklets are at least functional, in fact you have several available to add to your panel, such as weather report, or system monitor. gdesklets is in synaptic to offer you some applets which are functional and add "eye candy" if you can still call them that. Screenlets seem to be entirely useless. Like clutter on your desktop. Some folks just can't work in a clean environment and need stuff lying around...thus you have screenlets. I think you can stiil get them at getdeb.net. They are not stable and even less so in a composite environment.

Widgets are entirely different. Though some operating system refer to them as if they were desklets. In terms of GTK they are the aspects of the panels and menus...the gui really.

i have to disagree here. desktop widgets can be very useful, and not just clutter. for example, having a desktop widget clearly showing processor usage and other system stats has proven quite valuable to me regularly. i do lots of studio recording on my machine, and watching processor load is very critical when doing multitrack recording. and to have that sort of thing available at a glance is awesome. also, having quick launchers in an auto-hiding dock has been very useful. much quicker than fiddling about in application menus.

now, desklets in a panel can be very functional. however, gdesklets also provides desktop widgets which i have found to be rather unstable on multiple systems i have tried them out on.

btw, screenlets have given me absolutely no trouble whatsoever (yet). and, i do use a compositing WM.

---

### Post by chipants on 2008-02-21
> **PiggiePaul said:**
> Thanks, will take a look at your link.

So, do I take it, these things are not compatible with each other, and you have to choose the system that uses it own TYPE of screenlet/desklet?

Is there no Standard format that some adhere to?

Obviously I'd like to choose the system that had the most graphically "Polished" versions.

sadly, there really is no universally accepted standard. you really need to use screenlets/desklets/widgets/whatever written specifically for the framework you have installed.

it's sorta annoying, indeed. i personally have been happiest with screenlets, as far as quality of available screenlets and stability goes.

btw, somewhere else in this thread, somebody mentioned cairo dock as opposed to AWN. cairo dock is very nice, as well. it all comes down to preference, i suppose.

---

### Post by PiggiePaul on 2008-02-21
I guess, perhaps I should clarify what I "Think" I  might be after, then perhaps it would be easier to decide what is the most suitable to achieve this.

I'm thinking of a Icon dock at the bottom of the screen (like on an iMac, so I can load BIG icons of the programs I tend to use every day for quick instant access.
Basically just like (as I say) an iMac does with OSX/Leopard.

Secondly, it might be nice to have say something on the right (like in Vista) where I used to have a YouTube search, an Ebay search etc feature, And perhaps a popup reminder thing to warn you when birthdays type things come up.

---

### Post by PiggiePaul on 2008-02-21
Again, a bit thank you (to all) for your replies.

I've just taken a look of a video of Cairo-dock and must say I'm impressed and looks like something I may well go for.

As we're running uBuntu and have the Compiz Fusion addon running, I see it has a option called WIDGET LAYER.

Is this compatible with Cario Dock, or is this for something else?

===== EDIT =====

But then AWN looks nice too ;)

---

### Post by chipants on 2008-02-21
actually, the widget layer thing is pretty neat. i'm not sure if you can make it work with cairo dock. but, i actually use it with screenlets. have you seen, on mac os x, the way that desktop widgets (aka, the dashboard) are on a different 'layer', only becoming visible when you activate the dashboard? well, that's what the widget layer does. for example, all screenlets give you many options regarding how they should be displayed. they can always sit on top of all windows and always visible, they can always be below windows but still always visible, or they can be invisible unless a hotkey is pressed. just like os x's dashboard.

it looks like you'll need a two-pronged approach to what you want/need.

first, you need a dock. choose cairodock or awn. they are the best two out there.

secondly, you'll need a desktop widget framework, such as gdesklets, adesklets, screenlets. (on KDE, there is also superkaramba, but doesn't work too well with gnome)

you can place widgets anywhere you want on your screen, so if you want them on the right side, like vista, that should be no problem no matter what widget framework you use. i know there is a really nice screenlet for quick searches in a variety of search engines. also, many many clocks. not sure about ebay searches.

---

### Post by PiggiePaul on 2008-02-21
> **chipants said:**
> actually, the widget layer thing is pretty neat. i'm not sure if you can make it work with cairo dock. but, i actually use it with screenlets. have you seen, on mac os x, the way that desktop widgets (aka, the dashboard) are on a different 'layer', only becoming visible when you activate the dashboard? well, that's what the widget layer does. for example, all screenlets give you many options regarding how they should be displayed. they can always sit on top of all windows and always visible, they can always be below windows but still always visible, or they can be invisible unless a hotkey is pressed. just like os x's dashboard.

it looks like you'll need a two-pronged approach to what you want/need.

first, you need a dock. choose cairodock or awn. they are the best two out there.

secondly, you'll need a desktop widget framework, such as gdesklets, adesklets, screenlets. (on KDE, there is also superkaramba, but doesn't work too well with gnome)

you can place widgets anywhere you want on your screen, so if you want them on the right side, like vista, that should be no problem no matter what widget framework you use. i know there is a really nice screenlet for quick searches in a variety of search engines. also, many many clocks. not sure about ebay searches.

Thanks, yeah, I think I'll follow your advice, and just sort the dock out first.

I was initially going to go with Cairo Dock, but then (after searching this forum) there was a posting from someone about the code being really old and messy and some new version was going to be started? then it seemed AWN is the new one on the block. 

But then I see Cairo Dock is still up to date (release wise) so not sure what's going on there.

I did like the way the icons grew as you moved over them in Cairo dock, but I think I saw a video of AWN which showed it could do the same and a lot more besides.

From the links I've found, it does look like you can get Cairo Dock as a deb self installing package, but not the latest version of AWN (unless you compile it yourself)

On the GetDeb site is a version (poss not quite the latest) but comments about it not working 100% by some, and all other add-on files you need, which all seems (to me) a bit confusing really :confused:

---

### Post by northern lights on 2008-02-21
In case you wanna try cairo:

 gave you the links for the newly released cairo-dock (1.5.1 - Feb 18th). A friend of mine ran them - They were buggy on his comp, so I'd recommend sticking to [ version 1.4.6]("http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.4.6.3_i686-32bits.deb"). Also install the [plugins]("http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.4.6.3_i686-32bits.deb").

---

### Post by PiggiePaul on 2008-02-21
> **northern lights said:**
> In case you wanna try cairo:

 gave you the links for the newly released cairo-dock (1.5.1 - Feb 18th). A friend of mine ran them - They were buggy on his comp, so I'd recommend sticking to [ version 1.4.6]("http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.4.6.3_i686-32bits.deb"). Also install the [plugins]("http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.4.6.3_i686-32bits.deb").

Thanks for those links.

Will try and do a little more reading up before I decide which dock to go with.

The comments about AWN taking more system power to run, kinda concerns me.

---

### Post by chipants on 2008-02-21
> **PiggiePaul said:**
> Thanks for those links.

Will try and do a little more reading up before I decide which dock to go with.

The comments about AWN taking more system power to run, kinda concerns me.

hmmm. i don't notice any amazing amount of system resources being devoured by AWN. although, maybe there used to be a problem. i've only been using it for a couple of months. and, there actually is a repository you can add to have AWN installed and updated. see the instructions at:

[http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29](http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29)

it's very, very easy.

there are, btw, many icon effects when mousing over launchers in AWN. grow, bounce, glow, squish, spin. my main gripe is that right now, there is no option to have the dock anywhere but on the bottom edge of the screen. i'd actually prefer to move it to the left side. oh, well.

---

### Post by PiggiePaul on 2008-02-21
> **chipants said:**
> hmmm. i don't notice any amazing amount of system resources being devoured by AWN. although, maybe there used to be a problem. i've only been using it for a couple of months. and, there actually is a repository you can add to have AWN installed and updated. see the instructions at:

[http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29](http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29)

it's very, very easy.

there are, btw, many icon effects when mousing over launchers in AWN. grow, bounce, glow, squish, spin. my main gripe is that right now, there is no option to have the dock anywhere but on the bottom edge of the screen. i'd actually prefer to move it to the left side. oh, well.

Ok, going to have a try with AWN using your link.

Not sure if this is in any way related, but I JUST did the 1st part of the instructions on that link which was to edit your software sources list by changing an option to get from more (I forget the exact term) places, and just after that I had a system update come thru. ubuntu's update manager is downloading 29 updates.

Amarok (music player) is one of the revision updates.
Some library stuff, and about 2MB of Compiz Fusion bits too
 
Perhaps it's just coincidence?
But they appear to be coming from "gutsy-backports."

---

### Post by chipants on 2008-02-21
> **PiggiePaul said:**
> Ok, going to have a try with AWN using your link.

Not sure if this is in any way related, but I JUST did the 1st part of the instructions on that link which was to edit your software sources list by changing an option to get from more (I forget the exact term) places, and just after that I had a system update come thru. ubuntu's update manager is downloading 29 updates.

Amarok (music player) is one of the revision updates.
Some library stuff, and about 2MB of Compiz Fusion bits too
 
Perhaps it's just coincidence?
But they appear to be coming from "gutsy-backports."

gutsy-backports contains software backported to gusty from the next release. stuff that didn't make it into gusty when initially released. so, you're probably just ending up with newer versions of software that aren't available in the regular repos. i wouldn't worry too much about it. but, it is probably not a coincidence.

---

### Post by PiggiePaul on 2008-02-21
> **chipants said:**
> gutsy-backports contains software backported to gusty from the next release. stuff that didn't make it into gusty when initially released. so, you're probably just ending up with newer versions of software that aren't available in the regular repos. i wouldn't worry too much about it. but, it is probably not a coincidence.

Cheers, yeah, it seem a bit of a coincidence ;)

Still, everything (I think) still works so that's ok!

Installed AWN using the instructions on that site, using the command line instruction:

 sudo apt-get install avant-window-navigator awn-manager

Which worked perfect, although all I have is an empty box on the screen.
(I've dragged a few icons onto it now of the apps I use)

but I have no themes, applets or launchers in the menu's :(

Perhaps there's an addon pack, but then again, perhaps it's best to add the bits I only need.

I'll have to ask around if there is a "default" add-on pack I should have got as well as standard?

---

### Post by rainwalker on 2008-02-21
Just to let you know, the version of screenlets on the screenlets website isn't updated anymore (as far as I know) because the original creator/maintainer no longer had the time to mess with them. They are now being carried on by Whise, who updates them regularly and posts them on [www.gnome-look.org](www.gnome-look.org)
Here's the link:[http://www.gnome-look.org/content/show.php/?content=73346](http://www.gnome-look.org/content/show.php/?content=73346)

Also, here's the page I used to install AWN: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
I think you said you already got it running, but I figured I'd show that to you anyway

---

### Post by chipants on 2008-02-21
> **rainwalker said:**
> Just to let you know, the version of screenlets on the screenlets website isn't updated anymore (as far as I know) because the original creator/maintainer no longer had the time to mess with them. They are now being carried on by Whise, who updates them regularly and posts them on [www.gnome-look.org](www.gnome-look.org)
Here's the link:[http://www.gnome-look.org/content/show.php/?content=73346](http://www.gnome-look.org/content/show.php/?content=73346)

Also, here's the page I used to install AWN: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
I think you said you already got it running, but I figured I'd show that to you anyway

actually, you're right and wrong, i think. the original author of screenlets, is no longer working on it. however, the official site provided repos that are currently updated. apparently by Helder Fraga. that is what i'm using.

---

### Post by chipants on 2008-02-21
> **PiggiePaul said:**
> I'll have to ask around if there is a "default" add-on pack I should have got as well as standard?

as a matter of fact, there is. i am actually using a different repository than the one suggested in the instructions i linked. (i didn't realize that when i posted the link)

anyway, in the repo i'm using, the package is called 'awn-core-applets'. try apt-getting that. there are tons of useful applets.

---

### Post by rainwalker on 2008-02-21
> **chipants said:**
> actually, you're right and wrong, i think. the original author of screenlets, is no longer working on it. however, the official site provided repos that are currently updated. apparently by Helder Fraga. that is what i'm using.

Whise = Helder Fraga

---

### Post by chipants on 2008-02-21
> **rainwalker said:**
> Whise = Helder Fraga

yes, i see that. what i was trying to make clear is that the current version that is distributed on gnome-look.org, is the same version available (well, kind of) on the screenlets website. the installation instructions on screenlets.org point to the repository maintained by whise/helder fraga.

it's sort of confusing since the download page points to the old package from the original author. however, on the FAQ page, instructions are given to get/install the actual current version.

[http://screenlets.org/index.php/FAQ#Just_get_the_newest_package:](http://screenlets.org/index.php/FAQ#Just_get_the_newest_package:)

it's pretty non-intuitive, if you're just looking for something to download.

---

### Post by rainwalker on 2008-02-22
Ah ok, I see what you're saying :)

---

