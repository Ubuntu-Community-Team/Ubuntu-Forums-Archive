---
title: "What theme is this desktop using?"
date: 2007-04-14
forum: Desktop Environments
---

### Post by sagara on 2007-04-14
I've found this screenshot on gnome-look.org and I've been trying to find out what theme and icons is this person using.

Screenshot:

[[IMG]http://img295.imageshack.us/img295/6418/53192screenlets1tx8.th.jpg[/IMG]](http://img295.imageshack.us/my.php?image=53192screenlets1tx8.jpg)


What I find interesting is that his gnome bars are semi-transparent but they **keep whatever theme** he is using.  As in, this is not a simple Panel Properties>Background>Solid color + add transparency. **Is this effect achieved through beryl?**

Anybody know the theme, icons and how to achieve that effect?

---

### Post by amohanty on 2007-04-14
I dont think you can do that through beryl. You can however design a background image to look like it and set it to that.

AM

---

### Post by Skidpad on 2007-04-14
If you look at the border buttons, it looks like a modified Vista theme to me.  Also, you can see the Beryl icon in the upper right corner (next to the Gmail icon).  Perhaps someone who uses Beryl can chime in regarding the transparency levels...

---

### Post by amohanty on 2007-04-15
Just verified it, make a transparent (partially in this case) png that is the same heigt as the panel and set the panel background to it and that should work :)

AM

---

### Post by maxamillion on 2007-04-15
> **amohanty said:**
> Just verified it, make a transparent (partially in this case) png that is the same heigt as the panel and set the panel background to it and that should work :)

AM

That is one way to do it, but I am almost positive Beryl can accomplish that without creating a png... I've seen alot of screenshots with semi-transparent panels still holding their gtk theme while running beryl.

---

### Post by amohanty on 2007-04-15
I played around with beryl settings and emerald a lot and did not find anything that let me do that. Aquamarine or some other theme manager possibly?? I have'nt used those. But it would be cool if one didn't have to create a transparent png for every background.

AM

---

### Post by mcduck on 2007-04-15
> **maxamillion said:**
> That is one way to do it, but I am almost positive Beryl can accomplish that without creating a png... I've seen alot of screenshots with semi-transparent panels still holding their gtk theme while running beryl.

You can also set the transparency for the panel with Beryl's Set-plugin (Window Management/Set Window Attribs by Various Criteria), but that makes _everything_ in the panel transparent, including all your applets and launchers..

In the end, if you don't mind not having real transparency I'd say the background image is the best way to do this.

---

### Post by kevinlyfellow on 2007-04-15
Its positively emerald.  Check this theme out (not the same, but vistaish also...)
[http://themes.beryl-project.org/theme_details.php?id=113](http://themes.beryl-project.org/theme_details.php?id=113)

---

### Post by sagara on 2007-04-15
> **mcduck said:**
> You can also set the transparency for the panel with Beryl's Set-plugin (Window Management/Set Window Attribs by Various Criteria), but that makes _everything_ in the panel transparent, including all your applets and launchers..

In the end, if you don't mind not having real transparency I'd say the background image is the best way to do this.

mduck could you please give me step by step instructions on how to set this up in beryl?  I got to Window Management/Set Window Attribs by Various Criteria menu but no matter how I played with the opacity box I couldn't get the gnome panels to be transparent...

---

### Post by mcduck on 2007-04-15
Go to Opacity, click on the '+' button, set it to 'Window Type', click the 'Grab'-button and click on your panel. Then set the opacity to whatever you want.

Alternatively just type the right entry in yourself: "w:Dock:70" (the last number is the opacity you want, from 0 to 100). There are some other settings that work too, like using Window Class or Class Title (Gnome-panel for both).

If you only want to do this for one panel, not for all, use "Window Title" instead of "Window Type".

---

### Post by sagara on 2007-04-15
mcduck you were right on the money.  Using that trick you can achieve the transparency effect he has.  Thanks!

So, anybody know what is the GTK theme he is using?

---

### Post by Fixxxer on 2007-04-19
I believe it's LiNsta2: [http://www.gnome-look.org/content/show.php/LiNsta2?content=43054]("http://www.gnome-look.org/content/show.php/LiNsta2?content=43054")

---

### Post by ComplexNumber on 2007-04-19
> **Fixxxer said:**
> I believe it's LiNsta2: [http://www.gnome-look.org/content/show.php/LiNsta2?content=43054](http://www.gnome-look.org/content/show.php/LiNsta2?content=43054)its not linsta because linsta has a white background. the one in the screenshot in the first post in this thread has a dark grey background.
i would say that the gtk theme is probably neutronium([click]("http://gnome-look.org/content/show.php/Neutronium?content=46153")). the window manager being used is beryl.

---

### Post by sagara on 2007-04-19
> **ComplexNumber said:**
> its not linsta because linsta has a white background. the one in the screenshot in the first post in this thread has a dark grey background.
i would say that the gtk theme is probably neutronium([click]("http://gnome-look.org/content/show.php/Neutronium?content=46153")). the window manager being used is beryl.

Actually Fixxer had it right...

It is indeed the **LiNsta2 theme**.  The theme is originally black, but using beryl's *Window Management > Set Windows Attribute by criteria* he added transparency to the gnome bar.  The red background and the black mixed together gave that purpleish look.

Awesome, thanks guys!! :) 

All that is left is his icon set!

---

### Post by ComplexNumber on 2007-04-20
> **sagara said:**
> Actually Fixxer had it right...

It is indeed the **LiNsta2 theme**.  The theme is originally black, but using beryl's *Window Management > Set Windows Attribute by criteria* he added transparency to the gnome bar.  The red background and the black mixed together gave that purpleish look.

Awesome, thanks guys!! :) 

All that is left is his icon set!
its definitely  not linsta2....100% guaranteed. for a start, the menubar on linsta2 is dark grey - in that screenshot, its turquoise.
i've just installed mplayer and it doesn't follow the gtk theme, so that makes a difference.
its closer to  nocturn than linsta2. nocturn is the 1st screenshot whilst linsta2 is the 2nd.

the icon set is a custom made exquisite (see 3rd screenshot). there isn't any icon set that looks exactly like that on gnome-look or art-gnome. as it happens, i've added a few icons to several themes and changed which themes are inherited.

---

### Post by Fixxxer on 2007-04-20
> its definitely not linsta2....100% guaranteed. for a start, the menubar on linsta2 is dark grey - in that screenshot, its turquoise.
i've just installed mplayer and it doesn't follow the gtk theme, so that makes a difference.
its closer to nocturn than linsta2. nocturn is the 1st screenshot whilst linsta2 is the 2nd.

Check the second screenshot from the link I posted, there the menu bar is the same color...

---

### Post by sagara on 2007-05-19
Everyone, thanks a lot for your input!

For those interested here is the breakdown of this theme:
**GTK2 theme:** [LiNsta2]("http://www.gnome-look.org/content/show.php/LiNsta2?content=43054")
**Beryl emerald theme:** [vistaq modified]("http://www.beryl-themes.org/content/show.php/vistaq+modified?content=51237")
**Icon theme:** [Aero]("http://www.gnome-look.org/content/show.php/Aero?content=35437")

Note that he modified the icon theme a bit.  For the firefox and IE icon you can get them here: [http://www.aqua-soft.org/board/showthread.php?t=43153](http://www.aqua-soft.org/board/showthread.php?t=43153)

The desklets (calendar, clock, weather)  he is using are called **screenlets**.

**Wallpaper:** I found it but now i lost the link...

---

### Post by marmiteOlz on 2007-05-20
[http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO_SETUP_SEMI-TRANSPARENT_PANELS](http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO_SETUP_SEMI-TRANSPARENT_PANELS)

saw this dont know if it helps or anygood for later reference

---

