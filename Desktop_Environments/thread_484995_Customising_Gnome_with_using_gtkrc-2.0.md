---
title: "Customising Gnome with using gtkrc-2.0"
date: 2007-06-26
forum: Desktop Environments
---

### Post by Beamerboy on 2007-06-26
I have been playing with my desktop to make some changes which override the theme settings for gnome-panel to allow me to have a nice dark gnome-panel whilst still having light grey window backgrounds in my theme.  You can see the result here:

[http://www.paladine.org.uk/test/images/Screenshot.png](http://www.paladine.org.uk/test/images/Screenshot.png)

I did this because I like the UbuntuStudio menubars but did not like the dark grey which is used for the window background in the theme and wanted a way to still have nice panels without having to have the dark window background.

Now I would like to change the background of the Ubuntu menu widget to match the gnome panel.  At the momentwhen I click on Applications, Places or System the menu background is light grey, I would like it to use a background image and to use a button type image like I have on my task bar for when I hover or click on a menu item.

I have found instructions for changing tooltips but I can't find anything for changing the menu background.  Does anyone know how to do this and the syntax I need to put in my gtkrc-2.0?

Thanks in advance

Paladine

---

### Post by darkmatter on 2007-06-26
It is relatively easy to change the menubar item. It just requires the use of a pixmap. in your case I would recommend a semi-transparent image as the applet's colour varies from the in application menubars (they use the same image, so its really just a matter of consistency)

The syntax looks like this:
```

style "menubar"		
{
engine "pixmap"
{
  image
    {
      function			= BOX
      recolorable		= TRUE
			state = PRELIGHT
     file				= "<path to>/menubar-item.png"

      border			= { 10, 10, 10, 10 }
      stretch			= TRUE
    }
  }
}

class "GtkMenuBar" 		        	style "menubar"
widget_class "*MenuBar.*"               style "menubar"

```

And that should do it :)

---

### Post by Beamerboy on 2007-06-26
That worked for the actual Menu buttons on the Panel but not for the background on the drop down menus.  I would like to change the drop down menus as well.

Thanks bud,

Paladine

---

### Post by Beamerboy on 2007-06-26
Darkmatter helped me out with my menu's in irc so I figured I may as well post them now they are done :)

[http://www.paladine.org.uk/test/images/Screenshot.png](http://www.paladine.org.uk/test/images/Screenshot.png)

Paladine

---

### Post by ComplexNumber on 2007-06-26
the theme is looking nice, i think :)
i can't see the difference between the older screenshot and the latest one, though.

---

### Post by Beamerboy on 2007-06-26
> **ComplexNumber said:**
> the theme is looking nice, i think :)
i can't see the difference between the older screenshot and the latest one, though.

Yeah I just copied the new screenshot straight over the old one hehehe.  The old one had generic clearlooks menus (light grey with flat blue highlight for hover and active menu items).

Paladine

---

### Post by ComplexNumber on 2007-06-26
> **Beamerboy said:**
> Yeah I just copied the new screenshot straight over the old one hehehe.  The old one had generic clearlooks menus (light grey with flat blue highlight for hover and active menu items).

Paladine
i was wondering why :D. i was flicking between the screenshots, but i couldn't see any difference.

btw do you have a name for the theme yet?

---

### Post by Beamerboy on 2007-06-26
> **ComplexNumber said:**
> i was wondering why :D. i was flicking between the screenshots, but i couldn't see any difference.

btw do you have a name for the theme yet?

I guess I could call it Clearlooks+Ubuntustudio+Hax0red-Panel&Menus

I wasn't really planning on doing anything with it, I just wanted to have something similar to UbuntuStudio but with light grey window backgrounds instead of dark grey.  It all just started out as trying to customize the panel to override the default theme settings so I could have my light window backgrounds but still have a nice dark panel that was similar to the UbuntuStudio Titlebars.

It is my first ever theme modification, in 15 years of Unix based OS' I have never used anything but default themes for my GUI.

I am interested in building a complete theme now, but there is precious little information out there on GTK+ theming, about the best I could find today was on live.gnome.org and there was very little there really for a beginner.

Maybe when I finish the other 20 or so projects I have on at the moment I will be able to put more time into generating a full theme from scratch and throw it up on gnome-looks or gnome-art if people are interested.  I have a lot to learn yet though.

Fortunately Darkmatter is a good friend and he is good at this stuff, so I should be able to pick his brains ;)

Paladine

---

### Post by ComplexNumber on 2007-06-26
just do what i did and have a look at other themes, then change a few things here and there to see the effect. 
here are some good resources:
[http://developer.gnome.org/doc/API/2.0/gtk/](http://developer.gnome.org/doc/API/2.0/gtk/)
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)
[http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

i agree with you that there really is virtually nothing out there on theming, so looking at other peoples themes and seeing how it's done really is the only viable way.

i've released some of my own themes [here]("http://opticaldellusion.deviantart.com/"):

i try to do something different that i've never seen before. i'm not really interested in doing what has already been done, so no mac/vista clones will be coming from me.

i'm still quite a beginner, but if darkmatter isn't available, feel free to ask and i'll see what i can do.

---

### Post by Beamerboy on 2007-06-26
> **ComplexNumber said:**
> just do what i did and have a look at other themes, then change a few things here and there to see the effect. 
here are some good resources:
[http://developer.gnome.org/doc/API/2.0/gtk/](http://developer.gnome.org/doc/API/2.0/gtk/)
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)
[http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

i agree with you that there really is virtually nothing out there on theming, so looking at other peoples themes and seeing how it's done really is the only viable way.

i've released some of my own themes here:
[http://opticaldellusion.deviantart.com/](http://opticaldellusion.deviantart.com/)
i try to do something different that i've never seen before. i'm not really interested in doing what has already been done, so no mac/vista clones will be coming from me.

i'm still quite a beginner, but if darkmatter isn't available, feel free to ask and i'll see what i can do.

Thanks for the links, I will give them a read.

I never even realised my theme resembled anything to do with Vista since I have never paid any attention to Vista and have never seen the Vista desktop.  But I only sleep ~15 hours a week so I like a nice dark desktop as it is easier on my old eyes.  My desktop background has been solid black for years and I find the light coloured gnome-panels have a nasty habit of causing screen burn on my LCD monitors since they are always present (I don't go for that autohide malarky).

I guess my theme is similar to the Web 2.0 type GUIs but I just like how easy it is on my eyes :)

Your themes on deviant art look nice but I would probably find all that colour a little distracting, I spend around 30-50 hours at a time in front of my PC so the easier on my eyes the better :D

I will give you a shout if I have any problems, thanks again for the links.

Paladine

---

### Post by ComplexNumber on 2007-06-26
no worries, mate.

i don't think you will need any more than those links. they're all the ones that i know, so they are the only ones that i can go by.

i had been doing mainly dark themes, but my latest has been a light one. colour stands out a lot more on dark themes, i think. they're also a lot more difficult to get right compared to light themes.


>  I never even realised my theme resembled anything to do with Vista 
i didn't either. your theme doesn't look like vista IMO.

---

### Post by kwaanens on 2007-10-16
> **Beamerboy said:**
> Now I would like to change the background of the Ubuntu menu widget to match the gnome panel.

How did you manage to do that?
I want to change the background and font colour of the drop down menus for the panel menu *only*.

The docuemntation for small tweaks to gtkrc-2.0 is really hard to find.

- Ketil

---

