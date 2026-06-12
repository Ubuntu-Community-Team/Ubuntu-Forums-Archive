---
title: "Panel transparency issues"
date: 2011-04-07
forum: Desktop Environments
---

### Post by mchamartin on 2011-04-07
Hoping this is a simple/easy thing to fix, but I haven't had much success googling around for it.  So I'm trying to go for a floating wing panel in the upper right corner with a transparent background.  I've mostly got it, but as you can see in the attachment, it isn't perfect.  Not sure how to get rid of the white bookends, how to get rid of the black background on the clock, or how to make the white border around the Show Desktop button go away (the border is transparent space on the icon file itself).  Transparencies on the panel seem to manifest as solid white, which I guess explains the icon's border and the bookends, but I don't know how to fix that.


EDIT: This is marked "solved" now -- short version, it is impossible to remove the panel's handles, but replacing gnome-panel with AWN achieves the desired effect.

---

### Post by Krytarik on 2011-04-07
This earlier post of mine should give you a good start, if not solve it:
[http://ubuntuforums.org/showthread.php?p=10622129#post10622129](http://ubuntuforums.org/showthread.php?p=10622129#post10622129)

What theme are you using?

---

### Post by mchamartin on 2011-04-08
I'm basically using ColorBit, but I've modified it pretty extensively, mostly through blind trial and error.  This is the first time I've really tried messing with my theme at all, aside from just switching between the pack-in and some downloaded themes.  So I don't even really know everything I've done to it.

I tried modifying ColorBit similarly to how you described in that post, but it didn't do anything.  Then I tried modifying Ambiance as you described and switched to that, but still nothing.

---

### Post by Krytarik on 2011-04-08
Ok, at first I was reluctant to reply, because I of course tested it with Ambiance, and I know that it works, if applied correctly.

But just yet I dowloaded "ColorBit-2", if you are referring to those (?), there are some that match the name:
[http://gnome-look.org/content/show.php/ColorBit?content=86093](http://gnome-look.org/content/show.php/ColorBit?content=86093)

And, besides some weird colors, I noticed that the panels are not set up correctly. I, too, have white or dark lines below the panels/items.

But before I start to tinker with its code, please attach your modified version.

---

### Post by mchamartin on 2011-04-08
Sorry, I think I wasn't completely clear what I meant before.  When I said I'd modified it a lot I meant I've modified the whole look of the system, I've messed with lots of settings in Emerald and GNOME Color Chooser and Compiz, not that I had edited the actual theme files very much or that everything I'd done directly pertained to the panel.  All I've done as far as editing the ColorBit theme files is placing hashmarks in front of lines calling for the panel background.  I've still gone ahead and attached ColorBit from my .themes so you can take a look at it, though, but I don't know that it'll differ greatly from what you've downloaded (except it looks like you might have a newer version -- pretty sure mine was 1.1).  This doesn't include the icons or anything else that I'm using, but I'm thinking that stuff should be irrelevant, right?  Like I said, this is the first time I've really tried to mess with themes, so I don't really know what I'm doing.

I also went ahead and attached an image of what the taskbar looks like when I switch to Ambiance as modified the way you described in the post you linked to.  You can see it's basically the same except that switching themes obviously switches icons.  The white bars on either side and the white border around the Show Desktop icon otherwise remain.  I'm kind of confused as to why transparency works fine for all the other icons but not this one.

I should probably mention vis-a-vis the original list of problems, I don't think there's actually a black background behind the clock, it just happens that the desktop image has a black field right there that perfectly coincides with the placement of the clock.  So that part is a non-issue, just me overlooking something obvious (there is no white spot behind the Show Desktop icon to account for that issue, and the white border follows it wherever I place it on the panel).

---

### Post by Krytarik on 2011-04-08
> **mchamartin said:**
> (except it looks like you might have a newer version -- pretty sure mine was 1.1).
Then you happen to use this one?:
[http://gnome-look.org/content/show.php/ColorBit?content=79006](http://gnome-look.org/content/show.php/ColorBit?content=79006)
Please upgrade to the newer version first, like it's also mentioned in the description.
I hope it doesn't change the general look of the theme in a way that you *don't* like.
> **mchamartin said:**
> This doesn't include the icons or anything else that I'm using, but I'm thinking that stuff should be irrelevant, right?Yeah, exactly.
> **mchamartin said:**
> 
I also went ahead and attached an image of what the taskbar looks like when I switch to Ambiance as modified the way you described in the post you linked to.  You can see it's basically the same except that switching themes obviously switches icons.  The white bars on either side and the white border around the Show Desktop icon otherwise remain.  I'm kind of confused as to why transparency works fine for all the other icons but not this one.Actually, the "white borders" around the Show Desktop applet belong to the icon. ;-) And these white bars are actually "hide buttons", you can disable them via the panel's properties.
> **mchamartin said:**
> 
I should probably mention vis-a-vis the original list of problems, I don't think there's actually a black background behind the clock, it just happens that the desktop image has a black field right there that perfectly coincides with the placement of the clock.  So that part is a non-issue, just me overlooking something obvious (there is no white spot behind the Show Desktop icon to account for that issue, and the white border follows it wherever I place it on the panel).
Could you please post a screenshot of the panel on a less disturbing background!? At first I took some of the details of the background as graphical issues of the panel, it seems.

---

### Post by mchamartin on 2011-04-08
All right, I upgraded ColorBit to the newer version you linked earlier.  I didn't realize those white bars were hide buttons, but I don't think it would have mattered since they're already disabled (and have been disabled all along) in the panel properties.  It actually seems like they aren't really hide buttons, they just mark where the hide buttons are supposed to go.  When I click on them as they are, nothing happens.  If I go into panel properties and enable hide buttons, they become solid white and they do hide the panel.  When I disable them again, they just go back to how they were before.

Re: the Show Desktop icon, in GIMP it shows transparency in the area that manifests as a white border on the panel.  Is that area not actually transparency?  If not, what should I do to get rid of the white border around it?

I've attached two more images here, the panel as it appears in the upgraded ColorBit without any modifications whatsoever, and as it appears with just one modification shown below.  I changed the background to one of the pre-loaded Ubuntu ones that should make the panel easier to see for the second image.

```
###########################################################
# Panel Selection - Just one can be uncommented at a time #
###########################################################

**#include "panel-gray.rc"  # Comment out to disable gray panels and ...** (this is the part I changed, commenting out the line)
#include "panel-dark.rc"  # Uncomment to get dark gray panels.
#include "panel-white.rc"  # Uncomment to get white panels.
```

---

### Post by Krytarik on 2011-04-08
Ok, it turned out that
- these bars are actually 'handles', not hide buttons, I just didn't see them before in Ambiance because they are grey on grey
- the 'background' of the Show Desktop applet icon is indeed transparent, I didn't check that before because its rounded corners suggested the other thing to me

Both of these are pointing to one cause, that the background color of the panel reverts to white if you simply disable all "panel*.rc"s, besides some other ugly side-effects, like the style of the handles.

So, instead of simply disabling it at all, only outcomment the line that specifies the background image, like this, in "panel-gray.rc":

.../ColorBit-2/gtk-2.0/panel-gray.rc:
```
################################################
# Panels:
################################################
# Note: Uncommenting means to delete the "#" at the beginning of a line. 
#Commenting out means to add a "#" at the beginning of a line. The "#" tells the theme wether to ignore the line or not.

style "panel"
{

xthickness = 0
ythickness = 0

      fg[NORMAL]            = "#ffffff" #TEXT ON NORMAL PANEL BUTTONS
      fg[PRELIGHT]            = "#303030" #TEXT ON MOUSEOVERED PANEL BUTTONS
      fg[ACTIVE]            = shade (1.6, @selected_fg_color) # TEXT ON ACTIVE PANEL BUTTON
      fg[SELECTED]            = shade (1.6, @selected_fg_color) #
      fg[INSENSITIVE]            = "#6B6B6B"

     bg[SELECTED]            = "#2C2C2C"

    bg[NORMAL]               = "#3c3c3c"  # Makes panel background dark.
    bg[PRELIGHT]             = "#3c3c3c"  # Makes panel button prelight dark.
    bg[ACTIVE]               = "#333333"  # Makes pressed buttons dark.

[B][COLOR=Red]    #bg_pixmap[NORMAL]         = "/panels/panel-bg-gray.png"
[/COLOR][/B] [COLOR=Red][B]   #bg_pixmap[ACTIVE]         = "<parent>"
    #bg_pixmap[SELECTED]         = "<parent>"
    #bg_pixmap[INSENSITIVE]         = "<parent>"
    #bg_pixmap[PRELIGHT]         = "<parent>"
[/B] [/COLOR]
```

---

### Post by mchamartin on 2011-04-08
All right, so doing that got rid of the string of dots that marked the edge of the notification area, which is an improvement.  The Show Desktop icon's border is now transparent, so also an improvement.

The handles are still there, but they turned black now.  The indicator applet and Show Desktop icon both have underlines now, which is a little bit confusing.  In the panel-gray.rc file, right under the part that you quoted in your post is the part that actually controls the handles, so I tried to change the handles to transparent images, but that didn't get rid of them.  It seems the theme's default handle images are already transparencies with three little circles down the middle, so replacing them with fully transparent images just removes those three little circles while the black field otherwise covers the handle space.  Knowing now that these things are called handles allowed me to google a little bit more effectively, and it seems like this is a problem people have been having for the past few years.  I've found a couple supposed solutions, none of which are working for me, so now I'm starting to wonder whether it's actually possible to do this at all.  They almost certainly can't be gotten rid of, because without the handles there is no where on the panel to right click so that you can add applets, add new panels, edit the panel's properties, etc.  I'm not sure whether it's possible to turn them transparent either.  That seems to be the big question a lot of people are having in these search results.

---

### Post by Copper Bezel on 2011-04-08
I think the stubbornness of those handles is the reason Wingpanel exists. = ) I've never seen anyone actually get rid of them. What you have is fairly pretty, and as you said, the handles do serve a function. (I'd be more annoyed with the fake transparency at this point, since your maximized windows will seem to have a hole in them.)

If you want it any prettier than that, you might look into an alternate panel. Wingpanel's nice, although I think it's changing directions at the moment. I like [Avant Window Navigator (testing)]("http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive"), and it does real transparency and rounded corners, but it would be a bit of a resource hog if it's only providing your system tray.

---

### Post by Krytarik on 2011-04-09
Apparently, it's indeed impossible to make the background of the handles transparent.

But I figured why some 'buttons' have a dark line below them, it's because those lines are included in the respective image files, I removed those dark lines, backed up the original files.

I also applied my own panel matches to it, to make sure that they are definitely correct.

And I fixed the permissions of all files/directories.

Attached the complete theme package.

You can lessen the impact of the handles background color a bit by setting a color that matches your wallpaper:
```
################################################
# Panels:
################################################
# Note: Uncommenting means to delete the "#" at the beginning of a line. 
#Commenting out means to add a "#" at the beginning of a line. The "#" tells the theme wether to ignore the line or not.

style "panel"
{

xthickness = 0
ythickness = 0

      fg[NORMAL]            = "#ffffff" #TEXT ON NORMAL PANEL BUTTONS
      fg[PRELIGHT]            = "#303030" #TEXT ON MOUSEOVERED PANEL BUTTONS
      fg[ACTIVE]            = shade (1.6, @selected_fg_color) # TEXT ON ACTIVE PANEL BUTTON
      fg[SELECTED]            = shade (1.6, @selected_fg_color) #
      fg[INSENSITIVE]            = "#6B6B6B"

     bg[SELECTED]            = "#2C2C2C"

[COLOR=Blue][B]    bg[NORMAL]               = "#3c3c3c"  # Makes panel background dark.
[/B][/COLOR]    bg[PRELIGHT]             = "#3c3c3c"  # Makes panel button prelight dark.
    bg[ACTIVE]               = "#333333"  # Makes pressed buttons dark.

    #bg_pixmap[NORMAL]         = "/panels/panel-bg-gray.png"
    #bg_pixmap[ACTIVE]         = "<parent>"
    #bg_pixmap[SELECTED]         = "<parent>"
    #bg_pixmap[INSENSITIVE]         = "<parent>"
    #bg_pixmap[PRELIGHT]         = "<parent>"

```
But, like Copper said, it indeed looks weird regarding maximized windows if you have a non-expanded panel of this style, because it blocks the whole area anyway.

---

### Post by mchamartin on 2011-04-09
Yeah, it doesn't look great with a fully maximized window, but my current background is really dark (as you glimpsed in the earlier images of the panel) and so are my title bars, so it doesn't look as bad as it might otherwise.  Title bars on inactive windows are also pretty transparent so it looks fine except on an active, fully maximized window.  Also, since my background is a black and white night photo, the black handles blend in pretty well for now.  I get bored and change images fairly often, so it'll be something to keep in mind next time I switch images to find something that'll blend with the handles (or change the handle color to blend with the new background), but for right now it looks all right.  Here's ([http://i52.tinypic.com/2mxhmzc.png](http://i52.tinypic.com/2mxhmzc.png)) how the whole desktop looks, I'm fairly happy with it.

I could just put everything in the dock, but I don't like it to get too cluttered and it's already pretty full as it is (this is one of my biggest beefs with OSX, how annoying it is to click through to get to your apps unless you put them in the dock; my OSX dock has even less stuff in it than this one does, but I just don't want it full of stuff I barely/never use).  I also really like having the clock exactly where it is, don't really want to move it or do anything to it.  I think this looks reasonably decent, though.  Many thanks for all the help getting it to this point.

---

### Post by Copper Bezel on 2011-04-09
Wait-wait, you're already *using* AWN? Is it the testing version? If not, you can reinstall from the testing (Trunk) PPA without losing your settings.

It supports multiple panels. You can also use different styles (not themes, but styles) for the panels.

[[img]http://dl.dropbox.com/u/17749392/AWNtut/screenshotthumb.png[/img]]("http://dl.dropbox.com/u/17749392/AWNtut/screenshot.png")

[Shameless link to my how-to on the matter]("http://ubuntuforums.org/showthread.php?t=1714111&highlight=awn+dockbarx").

What you have is already very nice, though. = ) I like the backdrop!

---

### Post by Enigmapond on 2011-04-09
See this [http://www.howtogeek.com/howto/43673/how-to-make-the-gnome-panels-in-ubuntu-totally-transparent/](http://www.howtogeek.com/howto/43673/how-to-make-the-gnome-panels-in-ubuntu-totally-transparent/) It worked wonders for me.

---

### Post by Krytarik on 2011-04-09
> **Enigmapond said:**
> See this [http://www.howtogeek.com/howto/43673/how-to-make-the-gnome-panels-in-ubuntu-totally-transparent/](http://www.howtogeek.com/howto/43673/how-to-make-the-gnome-panels-in-ubuntu-totally-transparent/) It worked wonders for me.
Did you read the thread!? Making the panels transparent in expanded mode is quite simple, and the OP already managed that, as you could have seen at least in the latest screenshot. No, what seems to be impossible, is to make the handles of the panels -which appear when the panel is not expanded- transparent, too.

However, I presume that doesn't matter anymore anyway, since we just yet learned that the OP is already using AWN, and will find a much more suitable replacement for the remaining upper panel by using it for those as well.

---

### Post by mchamartin on 2011-04-10
Yeah I have no idea how, but somehow I completely overlooked the Add Dock button in AWN, so I didn't realize I could have multiple panels with it and didn't think it was possible to run multiple instances of it.  I only just installed AWN like last week so I'm still not super familiar with its features yet, but it turns out it makes this whole thing a whole lot easier to do, of course.  I haven't got the panel transparent with AWN yet, but I like the way it's looking right now. I'll probably continue tweaking it, might make it transparent or might keep the background, but either way I'm much happier with this than with the Gnome panel.  I haven't even started messing with DockBarX yet, although I did go ahead and install it.

[http://i54.tinypic.com/nleb1c.png](http://i54.tinypic.com/nleb1c.png)

Thanks again to both you guys for all the help.

---

### Post by Copper Bezel on 2011-04-10
No problem - and that's looking good! = ) For transparency in the panels, you can go to the Theme tab and hit the Customize button, and when you select the colors for the panel background, each of the colors has an opacity slider. = )

---

### Post by Krytarik on 2011-04-10
> **Copper Bezel said:**
> No problem - and that's looking good! = )
I agree!
> **Copper Bezel said:**
> For transparency in the panels, you can go to the Theme tab and hit the Customize button, and when you select the colors for the panel background, each of the colors has an opacity slider. = )
Or simply choose "None" as the "Style" option in the main "Preferences" tab.

---

### Post by mchamartin on 2011-04-10
I've gone ahead and marked this one solved.  I turned the panel transparent and like the effect quite a bit, it's exactly what I was going for before, and it took all of about five minutes to put together after days of wrestling with gnome-panel.

One final pic of how it looks with the transparency: [http://i55.tinypic.com/1zdlki8.png](http://i55.tinypic.com/1zdlki8.png)
And with Chrome maximized: [http://i55.tinypic.com/kbopk1.png](http://i55.tinypic.com/kbopk1.png)

Really pleased with this, thanks again for everything.

---

