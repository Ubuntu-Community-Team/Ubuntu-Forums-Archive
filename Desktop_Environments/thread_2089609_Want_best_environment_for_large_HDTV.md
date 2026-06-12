---
title: "Want best environment for large HDTV"
date: 2012-11-29
forum: Desktop Environments
---

### Post by derekcentrico on 2012-11-29
I've tried Unity 3D and XCFE thus far on my 1080p 42" LCD.  They aren't the greatest as the menus, icons, notification bars, etc... are very small.  Text in web-browsers and application operations are just fine on the TV.

Unity 3D just isn't big-screen friendly.

XCFE gets close with the scaling of icons and the notification bar, but the menus and launcher are not sizable it appears.

Any advice out there on an environment or hack that would enlarge everything to make desktop environment activity function decently?

---

### Post by SeijiSensei on 2012-11-29
I'm sitting across the room from my HDTV writing this posting.  I run at 1280x720 because I cannot read the text at 1920x1080.  That is the simplest solution to the problem.

On occasion I'll want to watch a media file at 1080p.  I just kick the screen temporarily into that resolution then return to 720p when I'm done.

Oh, I'm using KDE by the way, but I doubt that matters much at all in this case.

---

### Post by amethyst igor on 2012-11-30
> **derekcentrico said:**
> I've tried Unity 3D and XCFE thus far on my 1080p 42" LCD.  They aren't the greatest as the menus, icons, notification bars, etc... are very small.  Text in web-browsers and application operations are just fine on the TV.

Unity 3D just isn't big-screen friendly.

XCFE gets close with the scaling of icons and the notification bar, but the menus and launcher are not sizable it appears.

Any advice out there on an environment or hack that would enlarge everything to make desktop environment activity function decently?

In Xubuntu, clicking on the mouse opens up the menu. Choose Settings | Appearance, and select the Fonts tab. You can change from Droid Sans 10 to a larger size like Droid Sans 36. There are some other options as well that I haven't looked at.

I have never run Unity 3D with Xfce so I don't know about Unity. I just use Xubuntu with stable and solid and traditional Xfce. Xfce is pretty customizable, not quite as easy to customize as say, Linux Mint Mate, but you can adjust a lot of things and certainly fonts is one of them. Also in Xubuntu, xscreensaver just works right. VLC can disable screensaver so that it won't blank the screen. In Linux Mint Mate, prepare to watch a movie about a blank screen.

I have an 800x600 monitor, so my problem is the opposite of yours. Things look too big, not too small. But since I only use Xubuntu for HTPC, I don't care. I have one launcher for videos, another launcher for audio files, and a launcher for the screensaver slideshow. Done.

---

### Post by Cheesemill on 2012-11-30
I'm using Gnome Shell as my DE. If you install gnome-tweak-tool you can set a custom text scaling factor, increasing this works well for my big screen.

---

### Post by DrTebi on 2012-11-30
I am facing a similar problem, only that my screen packs 3840x2400 pixels into 22"... everything got very small (although still very readable at close distance).

I enlarged all text through the appearance menu:
System->Preferences->Appearance
Tab "Fonts" -- enlarge all fonts here.

Next you can set a higher dpi for all fonts through the Configuration Editor. If you don't have it installed already: Applications->Ubuntu Software Center
Search for "configuration editor" and install it.

Now open Applications->System Tools->Configuration Editor
In here, browse to
desktop->gnome->font_rendering
You will find the key "dpi" there. Set it to 120 or whatever else suits your needs.

You can further get larger scroll bars by putting a file named ".gtkrc-2.0" into your home directory with the following content:

```
style "scroll"
{
    GtkScrollbar::slider-width = 25
}

class "*" style "scroll"

```
(you will need to logout and log back in for this to work I believe)


This got me pretty usable results. My only problem now is, that the close/minimize/maximize buttons are still very small. I cannot figure out how to enlarge those :(

---

