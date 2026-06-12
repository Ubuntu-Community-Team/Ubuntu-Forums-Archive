---
title: "The Ubuntu/Gnome Dark Theme mega thread"
date: 2008-06-24
forum: Desktop Environments
---

### Post by Technoviking on 2008-06-24
I created this thread to help discuss and solve problems people have using darker themes in Ubuntu/Gnome.

Please comment in this thread if you have other fixes or suggestion you would like to share.

---

### Post by Technoviking on 2008-06-24
[From [http://www.mikesplanet.net/2008/06/using-dark-themes-in-ubuntu/]](http://www.mikesplanet.net/2008/06/using-dark-themes-in-ubuntu/])

Using dark themes in Gnome has always has some issues. Due to issues in Gnome and GTK apps, some application have problems like dark fonts on dark background, text areas grayed out, and multiple issues with OpenOffice. Here is a quick guide to solve many of the problems I encountered using dark themes in Gnome.

**1. Firefox Fixes**
Firefox has issues display certain CSS field properly with dark themes. This is a big problem in Firefox 2, but can still happen in Firefox 3. Install this userContent.css to /home/username/.mozilla/firefox/RandomProfile_name/chrome and restart Firefox.
[B]
2a. Dark System Themes (Ubuntu Studio)[/B]
The easiest solution for a dark theme in Ubuntu is to install the UbuntuStudio-theme package.
```
sudo apt-get install ubuntustudio-theme
```
or if you want the full metapackage with icons, GDM theme, etc..
```
sudo apt-get install ubuntustudio-look
```
The Ubuntu Studio theme is a beautiful theme created by the Ubuntu Studio team, which fixes many of the problem with dark themes in Gnome.
[B]
2b. Other Dark Themes[/B]
Since Linux is all about choice, we want to use other dark themes for Gnome and workaround issues these themes have. First, we still want to install the ubuntustudio-theme package.
```
sudo apt-get install ubuntustudio-theme
```
Then we will use UbuntuStudio theme on certain applications that have problems with dark themes (OpenOffice, Banshee, Thunderbird,etc&#8230;).

To get an application to use another theme you want to add the following to the command the launches a program &#8220;*env GTK2_RC_FILES=/usr/share/themes/UbuntuStudio/gtk-2.0/gtkrc*&#8220;. Right click on the gnome menu applet and choose Edit Menus. Goto the application you want using a different theme (in this example OpenOffice Writer), right click the application and select Properties. Change the **Command** from
```
ooffice -writer %U
```
to
```
env GTK2_RC_FILES=/usr/share/themes/UbuntuStudio/gtk-2.0/gtkrc ooffice -writer %U
```
OpenOffice Writer should now use UbuntuStudio theme instead of the system theme you have set.

[[IMG]http://www.mikesplanet.net/images/darkthemess.png[/IMG]]("http://www.mikesplanet.net/images/darktheme.png")
Theme Details:
Theme: Moomex Ultimatum 0.4
Font: UnDotum Bold
Icons: Jungle Black
Wallpaper: Radiant from [http://interfacelift.com](http://interfacelift.com)

---

### Post by el-mar01 on 2008-06-28
Heres another screenshot of the problem .. in Hotmail the widget text is barely visible:

[IMG]http://i29.tinypic.com/64359v.png[/IMG]

I don't understand why this isn't fixed when if there was a problem like this in Windows it would be fixed overnight.

---

### Post by Anzan on 2008-06-28
Here is something someone might find useful.

I'm using a combination of different elements for a dark theme but the one for Controls is SlicknesS-black.

Over the decades, some of my oldest files have gone from some Mac free office program from 1987 to Word for Mac to Word as such and then Open Office Writer. When I opened one this morning that file had whitish text on a white background instead of grey. No idea why. Some old cruft that was not evident until changing the system theme. 

If you run into this: Go to Format/Page/ and choose "no fill" for
background.

---

### Post by Anzan on 2008-06-28
Oh, Mike. I wanted to thank you for the information you've posted. It's helped my desktop considerably.

---

### Post by rainwalker on 2008-06-28
> **el-mar01 said:**
> Heres another screenshot of the problem .. in Hotmail the widget text is barely visible:

[IMG]http://i29.tinypic.com/64359v.png[/IMG]

I don't understand why this isn't fixed when if there was a problem like this in Windows it would be fixed overnight.

That's kind of a crazy assumption. Anyway, why don't you file a bug report? Maybe no one else is aware of the problem.

---

### Post by rage-against-windows on 2008-06-28
I love a dark desktop but all the ones for Ubuntu/Gnome are either too dark or the fonts disolve into the background. (I have bad eyes). I finally found a cure by using the Polycarbonate theme located at [http://art.gnome.org/download/themes/gtk2/1230/GTK2-Polycarbonate.tar.gz](http://art.gnome.org/download/themes/gtk2/1230/GTK2-Polycarbonate.tar.gz), along side of the gnome Gartoon Icon theme located in the repository. It gives a dark feel but all the colors stand out and seperate easy for people with "old" eyes. Heres a sample of the desktop running Polycarbonate [http://www.wyked-rage.info/my_images1/SemiDarkDesktop.png](http://www.wyked-rage.info/my_images1/SemiDarkDesktop.png). They also make a Polycarbonate dark version for the younger crowd who still have a good set of peepers.

---

### Post by rainwalker on 2008-06-28
Also, you can install the package "gnome-color-chooser" to customize your colors system-wide

---

### Post by Spaceman9 on 2008-06-28
The best looking black theme for Gnome I've ever seen is in PCLOS2008.1 [http://linuxgator.org/home/index.html](http://linuxgator.org/home/index.html) theme [http://www.tuxmachines.org/gallery/v/pclosgnome/](http://www.tuxmachines.org/gallery/v/pclosgnome/)

The problem I have with most black themes is they usually make everything black except the text. Everything blends into a black hole. PCLOS Gnome has a good balance between black and lighter values which makes things easy on the eyes while still providing a slick, really cool looking black theme.

I'd never give up Ubuntu though.

---

### Post by benerivo on 2008-06-29
The next full release of Ubuntu (Intrepid Ibex), has a darkish theme called new human. I temporarily linked to the Intrepid reps, to upgrade the ubuntu artwork package, so i can have it as my theme in gutsy.

[Some screenshots]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_alpha1&num=1").

---

### Post by rainwalker on 2008-06-29
> **benerivo said:**
> The next full release of Ubuntu (Intrepid Ibex), has a darkish theme called new human. I temporarily linked to the Intrepid reps, to upgrade the ubuntu artwork package, so i can have it as my theme in gutsy.

[Some screenshots]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_alpha1&num=1").

Wow...I have to say, that theme looks horrible.
What happened to black? That's more of a gross mud brown...

---

### Post by prasadz8 on 2008-06-29
> **rainwalker said:**
> Wow...I have to say, that theme looks horrible.
What happened to black? That's more of a gross mud brown...

You want black? Here's Audacious' GTK2 Theme!!
I manage to get it out from my themes folder and I'm posting it on DeviantArt. Do check my other works too! Go Ubuntu.

[CENTER][IMG]http://fc05.deviantart.com/fs26/i/2008/178/f/9/aud_Default_by_prasadz8.png[/IMG]
aud-Default DARK THEME is at this [[COLOR="DarkRed"][SIZE="4"]link[/SIZE][/COLOR]]("http://prasadz8.deviantart.com/art/aud-Default-89906866").

I give full credit to the creators of Audacious.
Please follow the link for further details on installation instructions.
Don't forget to visit my [deviants]("http://prasadz8.deviantart.com/") too!!
[[IMG]http://a.deviantart.com/avatars/p/r/prasadz8.jpg[/IMG]]("http://prasadz8.deviantart.com")[/CENTER]

---

### Post by rainwalker on 2008-06-29
Umm...that theme has been made; it's called Divinorum, I recognize those controls. I used to use that theme all the time before I found the Aurora engine

---

### Post by ethana2 on 2008-07-02
I am one of those that thinks New Human already looks pretty good, except the title bars..

But they still have those unsightly arrows at the ends of scroll bars.  Raise your hand if you don't have a scroll wheel or touchpad..

---

### Post by Technoviking on 2008-07-03
The [Moomex]("http://www.gnome-look.org/content/show.php/Moomex-Theme?content=57063&PHPSESSID=ea905cf08ade68755d4bbc1b43469b61") theme is a nice dark theme also. The advantage of it is that it only makes the menus dark and not the windows by default.

---

### Post by apostate on 2008-07-11
> **rainwalker said:**
> Wow...I have to say, that theme looks horrible.
What happened to black? That's more of a gross mud brown...

I have to agree, that theme is perfectly hideous. What on Earth is so awesome about using brown on a freaking desktop? If they intend to re-work the Ubuntu desktop look, couldn't they just ditch the brown, and move boldly forward with black, blue, grey, green??! For one version, would it kill them?

---

### Post by VargasTheBlind on 2008-07-11
I use the SlicknesS-Black theme, and I love it...no problems in Hardy, except one - the search field in the Add/Remove Manager goes off-white with the text having the same color, but only when text is inputted, not while it's empty. Still, it's only a VERY minor nuisance.

---

### Post by Sealbhach on 2008-07-11
I just downloaded this theme here: LUX.

No problems so far, working nicely.

[http://linux.softpedia.com/get/Desktop-Environment/Themes/LUX-36880.shtml](http://linux.softpedia.com/get/Desktop-Environment/Themes/LUX-36880.shtml)


[IMG]http://www.softpedia.com/screenshots/thumbs/LUX-36880-thumb.png[/IMG]

---

### Post by damis648 on 2008-07-11
I think Neutronium Gilouche and Slickness are the best, IMO.

---

### Post by nufros on 2008-11-12
el-mar01, here's a Greasemonkey script that helped me with that same problem :)

[http://userscripts.org/scripts/show/36850]("http://userscripts.org/scripts/show/36850")

---

### Post by kogger on 2009-02-23
Does anyone have an idea on a fix for Skype? Skype uses light gray on light blue when you select a name, which for some reason gets virtually unreadable with a dark theme.

[http://i119.photobucket.com/albums/o147/kingofgoldoa/skype-screenshot.png](http://i119.photobucket.com/albums/o147/kingofgoldoa/skype-screenshot.png)

---

### Post by Cynik on 2009-03-08
Well, for dark controls and colours with a white center -- try Ubuntu Dust. They provide firefox fixes too; it looks great without actually reducing readability.

---

### Post by zee-q on 2009-03-10
hello
i am new on ubuntu i want to install black theme for my ubuntu

how could i start 
thanks in advance

and please be some some brief

---

### Post by rainwalker on 2009-03-10
> **zee-q said:**
> hello
i am new on ubuntu i want to install black theme for my ubuntu

how could i start 
thanks in advance

and please be some some brief

Go to [www.gnome-look.org](www.gnome-look.org)
Find a theme you like
Save it somewhere
Go to System > Preferences > Appearance
Drag and drop the theme (usually a .tar.gz file) into that window and it should install

---

### Post by hictio on 2009-03-10
IMHO, the best way (or at leat, the fastest) of getting a Dark Theme running is, provided that you have Compiz installed and enabled, to use the [Negative plugin](http://wiki.compiz-fusion.org/Plugins/Neg) :D

The only problem you might find its bumping onto an already dark theme website, like, for instance, the Compiz' one.

---

### Post by viktiglemma on 2009-03-25
I use a dark theme called LimeLight which is good. The one and only problem I have is the default color of URL links (and email addresses) in GNOME. They have a dark blue color and that does not go well with deep gray. To see the color, go to System -> About GNOME for example.

Does anyone have any idea how to change this dark blue link color?

---

### Post by QkiZ on 2009-07-06
[http://gnome-look.org/content/show.php/Ubuntu+Dark?content=107771&PHPSESSID=f3ce938fdec41dfd9720a6d0c95defc0](http://gnome-look.org/content/show.php/Ubuntu+Dark?content=107771&PHPSESSID=f3ce938fdec41dfd9720a6d0c95defc0)
modified ubuntu human theme

---

### Post by booksnmore4you on 2009-12-28
> **Spaceman9 said:**
> The best looking black theme for Gnome I've ever seen is in PCLOS2008.1 [http://linuxgator.org/home/index.html](http://linuxgator.org/home/index.html) theme [http://www.tuxmachines.org/gallery/v/pclosgnome/](http://www.tuxmachines.org/gallery/v/pclosgnome/)




That theme is called SlicKness

---

### Post by mister_playboy on 2009-12-29
This is a very nice thread... I'm using Ubuntu Studio and building from there. :)

---

### Post by booksnmore4you on 2009-12-31
> **Cynik said:**
> Well, for dark controls and colours with a white center -- try Ubuntu Dust. They provide firefox fixes too; it looks great without actually reducing readability.

There is actually a Firefox theme based on Ubuntu Dust, called Ubuntu Dust.  You can search for it.

---

### Post by EdwardMorris on 2010-01-29
Hi all,

    I love the Dark themes like Black Fate and Divirum, but unfortunately, I can not get it to work right with eclipse, my most used program. While eclipse looks phenomenal using Grey themes like Neutronium Gilouche and such, it looks very poor in themes like Dark Fate, just because the toolbar separators don't render correctly and the same is with the lines in between the frames (which are very clear in NG). Is there any possible workaround to this? I love DF too much to give up on it....

---

### Post by atlantique on 2010-06-03
> **prasadz8 said:**
> You want black? Here's Audacious' GTK2 Theme!!
I manage to get it out from my themes folder and I'm posting it on DeviantArt. Do check my other works too! Go Ubuntu.

[CENTER][IMG]http://fc05.deviantart.com/fs26/i/2008/178/f/9/aud_Default_by_prasadz8.png[/IMG]
aud-Default DARK THEME is at this [[COLOR=DarkRed][SIZE=4]link[/SIZE][/COLOR]]("http://prasadz8.deviantart.com/art/aud-Default-89906866").

I give full credit to the creators of Audacious.
Please follow the link for further details on installation instructions.
Don't forget to visit my [deviants]("http://prasadz8.deviantart.com/") too!!
[[IMG]http://a.deviantart.com/avatars/p/r/prasadz8.jpg[/IMG]]("http://prasadz8.deviantart.com")[/CENTER]


aud-Default is really a great theme!  Thanks  prasadz8  for your work. I have been using it for more than a year! It is probably one of the best I have seen! Certainly the one I like best. Of course I do like dark themes.


**[prasadz8]("http://prasadz8.deviantart.com/")**

---

