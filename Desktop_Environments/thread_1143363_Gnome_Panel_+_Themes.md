---
title: "Gnome Panel + Themes"
date: 2009-04-29
forum: Desktop Environments
---

### Post by MadJester on 2009-04-29
I'm new to Ubuntu, but not new to Linux.  I'm trying to make sense of all the theme options with Compiz, Emerald, GTK, Metacity, etc.  

I am using 9.04 w. Compiz + Emerald.  Frequently when I install a theme, it will overwrite my transparent settings for the panel everywhere the panel is not blank.  I believe that this is because it sets a background image for those sections instead of a solid color, though I could be mistaken on this.  I would like the entire panel, including the Applications, Places, and System menus to stay transparent.  I don't know where to override this behavior though.  Many of the themes I am trying to use, leave the middle of the panel transparent, but fill in the sides.  How can I change this behavior, or modify a theme to not theme the panel?

[IMG]http://img208.imageshack.us/img208/224/screenshot42709.png[/IMG]
By [themadjester]("http://profile.imageshack.us/user/themadjester") at 2009-04-29

---

### Post by UbuntuNerd on 2009-04-29
there's actually no easy way of doing this I have managed to get my panels all black by using this [theme](http://www.4shared.com/file/86610410/14e4ffca/32768-DarkerTheme03tar.html?signout=1) if you really want your panel to be completely clear the only way I can think of is by removing the areas that don't change and replacing them with icons

---

### Post by UbuntuNerd on 2009-04-29
look at this screen shot

---

### Post by MadJester on 2009-04-29
Where is the panel theme being set?  Can I modify the theme to not theme the panel?  I thought that Emerald themes didn't theme the panel.

---

### Post by UbuntuNerd on 2009-04-29
emerald is just the window decorator, you can also right click on an empty space of your desktop scroll to the bottom and click on (Change Desktop Background)
when the menu opens make sure you have (Theme) selected and hit customize in the next menu play around with those settings, you can use different themes and mix and match

---

### Post by MadJester on 2009-04-30
Is this what GTK themes theme?  If so, is there a way to edit the theme and change the image the panel uses as its background to a solid color?

---

### Post by Eneerge on 2009-04-30
In the gtkrc file for the theme, they've probably specified an image or color for the MenuBar which is causing your problem.  Look in /usr/share/themes/your-theme or whereever your theme is located and locate the gtkrc file, edit it, and see if you can play with the settings to fix it or establish some sort of compromise.

Or, you can change the 'engine type' for the gnome-panel.  gnome-color-chooser gives you a gui for doing this.  You can make the panel render using a different theme's settings or you could create an entirely new theme specifically for the panel to fix your problem.  This is probably the easiest and quickest way, because you will probably find an engine that already does what you need it to do (make the menu transparent).


EDIT:  Ok, it looks like you're using the new wave theme which you can't fix by doing the 'easy' option above.  However, you can do this to fix your problem:
gksu gedit "/usr/share/themes/New Wave/gtk-2.0"
- Now search for the following string: "# Panel Matches"

This should bring you close to the end of the document that sets styles to each panel element.  You need to comment all of these lines out by putting a # in front of each line.
EG: #class "*Mail*"                     style "panel"

Comment everything out below the # Panel Matches line, save, and then reload your theme

---

### Post by marcoc2 on 2009-05-14
I have the same issue and I've tryed everything to remove this background (menu-bar image) out the panel.

Here it is:
[IMG]http://img27.imageshack.us/img27/9393/panelthing.png[/IMG]

I commented out all the "panel" matches in gtk2.0 folder files and nothing happens..

It is pissing me off :(

---

### Post by urosg3 on 2009-05-15
Try a Gnome-color chooser, from Synaptic, there you can set up panel background independently.

---

### Post by marcoc2 on 2009-05-15
Thanks urosg3,  good advice ;). 

This solved part my of my problem, because it changed the button colors of the bottom panel.

---

### Post by Sarai the Geek on 2009-05-15
Have you tried setting a background image for your panel? There's a transparent "glass" one in here: [http://www.gnome-look.org/content/show.php/Gnome+Panels+Package?content=79793](http://www.gnome-look.org/content/show.php/Gnome+Panels+Package?content=79793)

---

### Post by marcoc2 on 2009-05-15
Thanks Sarai the Geek, another good advice. This title bars background are awesome.

But this do not replace the start-menu buttons background.

---

### Post by urosg3 on 2009-05-15
> **marcoc2 said:**
> Thanks urosg3,  good advice ;). 

This solved part my of my problem, because it changed the button colors of the bottom panel.

You can select button colors also on Gnome color chooser, in Engines tab, then chek Panel and preferences. Also on Buttons tab you can select every button color system wide.

Cheers

---

### Post by marcoc2 on 2009-05-15
There is no "Preference" button in "Panel" option. There is for "Buttons" but I didn't find a place to change colors.

gnome-color-chooser 0.2.3

---

### Post by urosg3 on 2009-05-15
> **marcoc2 said:**
> There is no "Preference" button in "Panel" option. There is for "Buttons" but I didn't find a place to change colors.

gnome-color-chooser 0.2.3

&#1054;pen engine tab. Then in middle of list select engine for panel, and then on the right side find preferences. I post you a picture if you need.[IMG]http://img14.imageshack.us/img14/908/screenshotgnomecolorcho.png[/IMG]

---

### Post by urosg3 on 2009-05-15
And this is box (red one) for lower button color.[IMG]http://img211.imageshack.us/img211/908/screenshotgnomecolorcho.png[/IMG]
Cheers

---

### Post by marcoc2 on 2009-05-16
Thanks one more time urosg3.

I use Hardy at the work, so gnome-color-chooser worked diferent there from here, at my home, that i use Jaunty. (and Jaunty has the newer version 0.2.5)

I picked "crux" to panel style here and the buttons didn't turn into purple/yellow color like happened using Hardy.

And what I meant to the "preferences" button is that there is no options to this button to "crux' panel style.

Thanks for the pictures.
Its a little bit hard to choose all the right colors to everithing, but my problem is solved :p

---

