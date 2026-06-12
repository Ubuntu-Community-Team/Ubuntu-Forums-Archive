---
title: "Need Tips On Making Kubuntu Look Good"
date: 2008-02-06
forum: Desktop Environments
---

### Post by nullfactor on 2008-02-06
Due to an interesting problem with my wife's nVidia video card not working in Gnome, I thought I would try it in KDE... amazingly, it works beautifully!  However, the default KDE (and all included themes) are fugly to say the least.

Can anybody direct me to an easy (and updated) how-to on getting KDE to look awesome?

Any help would be appreciated.

---

### Post by nullfactor on 2008-02-06
So, nobody knows of any good how-to's?

---

### Post by p_quarles on 2008-02-06
[kde-look.org](http://www.kde-look.org/) has a lot of good resources for theming KDE.

---

### Post by nullfactor on 2008-02-06
P-QUARLES - Since I'm a COMPLETE noob when it comes to KDE, could you help me figure out what windows manager KDE uses?  I'm pretty convinced it's not Compiz-fusion, like what Gnome uses.  

I'm actually digging KDE more than Gnome, at this point.  It just has a better feel to it.  But there are a few things in Gnome that I miss... mainly just eye-candy stuff.  Such as, the good old desk cube, wobbly windows, etc.  Is there a way to get such things in KDE?  If not, it's not a killer.

---

### Post by p_quarles on 2008-02-06
Kubuntu's default window manager is Kwin. You can install and run compiz if you like, though.

---

### Post by Whiffle on 2008-02-06
If you search sypnaptic/aptitude for kwin you can get several different styles to install for the titlebars/frames/etc.  If you search for kde-style, you can get several different styles that render the widgets to choose from.  Also, if you want it to look like gnome, you can install qtcurve (search for it on kde-look.org).  KDE has nearly endless theming possibilities.  Also, there are more iconsets available both through apt and on the internet.  

All of it is controlled, at least on mine, with kcontrol.  Kubuntu has a default control center wanna be thing that is annoying, but if you run kcontrol (alt+f2, kcontrol), you can get all the available options.  Its all under the Appearance section.  Any other questions just ask.

---

### Post by nullfactor on 2008-02-06
WHIFFLE - Sounds great.  Also sounds overwhelming!  I've somehow managed a fairly decent desktop with just what comes default.  It took all day to figure it out, but at least it's easy on the eyes.  heh heh heh  I think I'll take everything you just listed and go through them to see what else I can mess up... I mean, customize.  Thanks!

---

### Post by Ubuntiac on 2008-02-06
You can install compiz fusion from the package manager (Kmenu->System->Adept Manager), although it needs a couple of other bits and pieces to start up automatically each login (ie a file called something like compiz.sh with compiz --replace in it placed in ~/.kde/autostart).

If you can wait, Hardy is due out in april that has dekstop effects all usable from a nice, easy gui.

As far as making your system nice, I'd download the OS-K icon set from kde-look.org. It is much, much nicer than the defaults. Easy to install, too. Just go to Kmenu->System Settings->Appearence->Icons and there's a button to browse for the file. Choose the tar.gz you downloaded from kde-look and after about a minute of looking like its just stalled you'll have a new, shinier icon theme. :)

---

### Post by AlanR8 on 2008-02-06
Hmm....

Been running K for a year now and will not swap to U.

First thing I do is change all the fonts. I import, from a Doze machine, Aerial, Comic Sans, Tahoma, Times New Roman and Trebuchet.

I then change all the fonts to 8 and Tahoma. I also apply the same font to the GTK styles so Firefox looks like it does under Doze.

Next I change the default desktop icon size to 32

I also, in Konqueror, NOT Dolphin,  select Detailed list view for file browsing, and this is what I get!

---

### Post by Christmas on 2008-02-06
I never had extraordinary results making my KDE desktop look awesome, but I tried some styles and tuning. What I did:
* Panel background: used a black and grey combination, and changed the colors of taskbar (KControl -> Desktop -> Taskbar -> Use custom colors). Also change the colors for clock, KDict or whatever applets you may have.
* If you want, try panel transparency, you may like it
* Use a style which you find the nicest (for me that is QtCurve - take it from [http://www.kde-look.org/](http://www.kde-look.org/); it's easy to compile)
* Install the package needed to make GTK apps use a KDE style of your choice (i'm using Debian so I don't know the exact name which Ubuntu uses, however try 'apt-search gtk engines' and see what's the package; try gtk2-engines-qtcurve); once the package is installed, you can find a configuration dialog in KControl -> GTK Styles and Fonts
* Change Konsole's background, I use one a darker variant made by me from the Night Fear wallpaper on kde-look.org
* Find a color theme to match your panels' color, mine is a nice brown one (I'll upload the .kcsrc file)
* Change the default icon theme, I recommend using Project Dark Glass, you can download it from kde-look.org, just search for it
* Get a set of nice wallpapers
* Randomly browse kde-look.org, you may get into something which you like
* Finally, install superkaramba, its widgets are really nice looking on a desktop

I can't provide a screenshot at this moment since I don't have all of the above set, but here are some taken a while ago:

---

### Post by Nythain on 2008-02-06
few things here...
first, gnomes window manager is NOT compiz-fusion... its metacity... compiz/beryl/fusion are composite window managers that can be installed into/onto any desktop environment (not sole wm environments like a fluxbox system though)

second... its been my experience that, once you learn WHERE everything is, kde is considerably more customizable than gnome in many areas... the problem is, things are scatttered throughout kcontrol so far its hard to track everything down

---

