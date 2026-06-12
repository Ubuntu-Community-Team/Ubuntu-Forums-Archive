---
title: "KDE's Plasma in Gnome"
date: 2009-02-12
forum: Desktop Environments
---

### Post by SpriteSODA on 2009-02-12
Hi guys, 
I'm a gnome user, and I love gnome. When KDE 4.2 came out I tried it but overall I find gnome more fitting to my needs. However, the Plasma panels are simply gorgeous! a google search came up with this:

[http://people.fruitsalad.org/adridg/bobulate/index.php?/archives/668-Plasma-everywhere.html](http://people.fruitsalad.org/adridg/bobulate/index.php?/archives/668-Plasma-everywhere.html)

the writer claims that he run Plasma in Gnome, and I ask - how is it done?

Thanks.

---

### Post by SpriteSODA on 2009-02-13
bump

---

### Post by jacksaff on 2009-02-13
The writer is a developer who is working on porting kde4 to solaris. He is not even running linux, let alone ubuntu.
If you want to see if what he does works in ubuntu then you need to have kdebase-workspace installed and run plasma while in a gnome session. I doubt this will work but htere's no harm in trying. It's not clear on that blog what sort of tweaks he might have made while compiling the kde packages, but it does sound like he didn't have to do anything at all to gnome which is promising...

---

### Post by Darkshade on 2009-02-13
I have both Gnome and KDE installed on my system and just tried running Plasma in Gnome. Plasma took over my whole desktop (wallpaper, plasmoids, panel, right click menu, etc), the Gnome panels were still visible on top, which means you can just chose the one that suits better your needs/taste, etc.
On the other side - it will probably not run if you don't have KDE4.x or all the dependencies, which I guess are a lot.

And just from curiosity - why would you want to do all this anyway? IMHO better give KDE4.2 a try, or if all you want are the panels (which you won't get separate from the whole plasma desktop) you can recreate that look easily with some dock/panel backgrounds in Gnome.

---

### Post by SpriteSODA on 2009-02-13
I tried KDE 4.2 and it just wasnt my cup of tea, Gnome is more fitting to my taste. But, the plasma panels are gorgeous, and simply no manipulation to the gnome-panel will ever be this impressive. In addition, the Screenlet application is inferior to the new shiny Plamsa.
Anyway, thank you Darkshade, I might try installing the required dependencies and have a go at it.

---

### Post by josephellengar on 2009-05-06
> **SpriteSODA said:**
> I tried KDE 4.2 and it just wasnt my cup of tea, Gnome is more fitting to my taste. But, the plasma panels are gorgeous, and simply no manipulation to the gnome-panel will ever be this impressive. In addition, the Screenlet application is inferior to the new shiny Plamsa.
Anyway, thank you Darkshade, I might try installing the required dependencies and have a go at it.

I'd still like to do this as well.  Screenlets don't even work anymore in jaunty.  Or, bump.  Sorry about dusting off an old thread but I didn't want to start another one.

---

### Post by prafjessor on 2009-05-09
> **idigchess said:**
> I'd still like to do this as well.  Screenlets don't even work anymore in jaunty.  Or, bump.  Sorry about dusting off an old thread but I didn't want to start another one.

Just do it. It works like a charm. Well, as long as you dont right-click certain plasmoids, that is. But other than that, it's fine. Install Plasma in synaptic and the dependencies will follow. Here's how my desktop looks like right now:

[http://pici.se/405930](http://pici.se/405930)

---

### Post by GamePad64 on 2009-05-31
> **prafjessor said:**
> Just do it. It works like a charm. Well, as long as you dont right-click certain plasmoids, that is. But other than that, it's fine. Install Plasma in synaptic and the dependencies will follow. Here's how my desktop looks like right now:

[http://pici.se/405930](http://pici.se/405930)
Sorry for bump, but.. What version of KDE do you use and how could you make to be only ICONS in the KDE's taskbar?

---

### Post by afrodeity on 2009-11-25
I'm doing exactly the same thing right now. Plasma is great. Only problem is it brings the default KDE lower panel with it along with a whole bunch of applications I don't need. What would be the steps needed to strip down the Kubuntu-Desktop so that one just has plasma, which is all you need. No point in running two systems. Also there is a bit of an overhead, and anything to cut down on unecessary resources would be of great help to those on lower end machines. :)

---

### Post by Zorael on 2009-11-25
> **GamePad64 said:**
> Sorry for bump, but.. What version of KDE do you use and how could you make to be only ICONS in the KDE's taskbar?
That would be by using the STasks or "Smooth Tasks" (new name, I think) plasma widget. **plasma-widget-stasks** is in the Karmic repos.

At the time of writing, there's also a very fresh build of Smooth Tasks in Sam Rog's PPA ([ppa:samrog131/ppa](https://launchpad.net/~samrog131/+archive/ppa?field.series_filter=karmic)). But that's a non-Canonical software source, so add it at your own risk.

---

### Post by afrodeity on 2009-11-27
Still think there's a better way to get plasma widgets in gnome. Must be a solution to running a full kde setup. Resources, overhead, I'm on a Celeron with only an entry level graphics card.

---

### Post by josephellengar on 2009-11-27
Is there any way to have the Plasma without the kde kicker bar?  I hate that bar.  And my other quarrel with the whole setup is that plasma takes over the right click menus, background, etc.  It certainly makes gnome prettier (as gnome is fugly- but extremely functional- normally), but that is simply  not enough given how poorly integrated everything feels.  Any ideas?

---

### Post by Zorael on 2009-11-27
> **rossholley said:**
> Is there any way to have the Plasma without the kde kicker bar?  I hate that bar.  And my other quarrel with the whole setup is that plasma takes over the right click menus, background, etc.  It certainly makes gnome prettier (as gnome is fugly- but extremely functional- normally), but that is simply  not enough given how poorly integrated everything feels.  Any ideas?
Kicker is KDE3 lingo, nowadays it's a plasma panel (of which you can have several). :3 Can you right click it and pick *Panel options -> Remove this Panel*?

As for the desktop right-click context menu, I believe that's very hard-coded. Without it, you wouldn't be able to set up any plasma widgets either. Likewise the background (though you can just change it to your GNOME wallpaper). Essentially plasma *is* the desktop workspace framework, and managing wallpapers and panels and widgets and context menus is its job. (The GNOME equavilent would be gnome-desktop, I guess.)

If at all of interest, the cashew can be removed with a special widget; there isn't a built-in option to do this. I get mine from Sam Rog's PPA ([ppa:samrog131/ppa](https://launchpad.net/~samrog131/+archive/ppa)), but if you'd prefer to compile it yourself, [it's on kde-look.org](http://kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009)```

```. [Here's another one](http://kde-look.org/content/show.php/Stealth+Cashew?content=108460) that will let you change its transparency. And in KDE 4.3, you can move it from the corner so that it's a tab on the top/side of your screen, if that's preferable.

---

### Post by afrodeity on 2009-11-27
screenlets in Karmic are so archiac, I really want some of the plasma in my widget layer or a way of getting the plasmazoids ported over to Gnome. They really are cool. Aside from the plasma layer, I don't like the k-desktop much because of the "K" issue, which is really just a conceit to mathematical absurdity.

---

### Post by Zorael on 2009-11-27
"K" issue? Apps having the letter k in them? I don't follow.

---

### Post by seeker5528 on 2009-11-27
How is the 'K' issue any different than the 'G' issue?

Later, Seeker

---

### Post by josephellengar on 2009-11-27
> **seeker5528 said:**
> How is the 'K' issue any different than the 'G' issue?

Later, Seeker

I don't quite follow.  What is this 'K' issue of which you speak?

---

### Post by josephellengar on 2009-11-27
> **Zorael said:**
> ppa:samrog131/ppa[/url]), but if you'd prefer to compile it yourself, [it's on kde-look.org](http://kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009)```

```. [Here's another one](http://kde-look.org/content/show.php/Stealth+Cashew?content=108460) that will let you change its transparency. And in KDE 4.3, you can move it from the corner so that it's a tab on the top/side of your screen, if that's preferable.

Wow.  I didn't realize I could remove the panel so easily!  Thanks!  What's the cashew?

---

### Post by Zorael on 2009-11-27
> **rossholley said:**
> Wow.  I didn't realize I could remove the panel so easily!  Thanks!  What's the cashew?
The thingamajig in the top-right corner. :3

---

### Post by seeker5528 on 2009-11-28
> **rossholley said:**
> I don't quite follow.  What is this 'K' issue of which you speak?

You'll have to ask afrodeity that, maybe the insistence of devs to put a 'K' in the name, same as the 'G' folk with the Gs, or maybe the belief the 'K' is an ugly letter while 'G' is beautiful and shapely. :p

Later, Seeker

---

### Post by josephellengar on 2009-11-28
> **seeker5528 said:**
> You'll have to ask afrodeity that, maybe the insistence of devs to put a 'K' in the name, same as the 'G' folk with the Gs, or maybe the belief the 'K' is an ugly letter while 'G' is beautiful and shapely. :p

Later, Seeker

Oh yeah.  That annoys me too, although the gnome folks dont do it as much as the kde devs, but still a lot.

---

### Post by afrodeity on 2009-11-30
Reason I don't like Kubuntu is because everything is Kbootable on your Kdestkop. And I Know that Knowledge starts with a silent K, but it's annoying when everything has a K in it. Its a mathematical conceit, and has absolutely nothing to do with the user-interface.Imagine if every C was replaced by the letter K? Then I would Khill Out instead of Chill, or eat an EnKhillada instead of an Enchillada and so on... A switch to turn off the K's would be a start.

---

### Post by josephellengar on 2009-11-30
> **afrodeity said:**
> Reason I don't like Kubuntu is because everything is Kbootable on your Kdestkop. And I Know that Knowledge starts with a silent K, but it's annoying when everything has a K in it. Its a mathematical conceit, and has absolutely nothing to do with the user-interface.Imagine if every C was replaced by the letter K? Then I would Khill Out instead of Chill, or eat an EnKhillada instead of an Enchillada and so on... A switch to turn off the K's would be a start.

Definitely agree wholeheartedly

---

### Post by Zorael on 2009-11-30
> **afrodeity said:**
> Reason I don't like Kubuntu is because everything is Kbootable on your Kdestkop. And I Know that Knowledge starts with a silent K, but it's annoying when everything has a K in it. Its a mathematical conceit, and has absolutely nothing to do with the user-interface.Imagine if every C was replaced by the letter K? Then I would Khill Out instead of Chill, or eat an EnKhillada instead of an Enchillada and so on... A switch to turn off the K's would be a start.
While derailing from the thread subject; I'm sorry, GNOME apps don't do this?

gnote, gnotski, gnomine, gnomint, gnometris, gnotravex, glines, gnibbles, gnobots2, gtali, gnect, gcompris, gconf, gcrystal, gdesklets, gdeskcal, gelemental, ghemical, ghex, ghextris, gresolver, grhino, ginspector, gtetrinet, gtimelog, glipper, glife, glunarclock, glotski, ...

Pot, meet kettle; it's just another form of branding. The G ones just don't stand out as much as we already have a lot of GNU apps, and the letter K isn't as common in the *English* language. You're welcome to think that it should all go away, but please don't be selective and ignore "your" side of the field.

---

### Post by afrodeity on 2009-12-02
You got me, its probably just a weird heuristic thing - when I look in my gnome menu I see descriptions of applications, eg Calculator not GCalculator, and I see there is a move to do this in KDE, so I guess its just a gripe with the application information and how this is displayed in KDE of the past.:)

But to get back to the topic, I want some of those cool plasmazoids in my widget layer on my Gnome desktop!!!!

---

### Post by seeker5528 on 2009-12-02
> **afrodeity said:**
> You got me, its probably just a weird heuristic thing - when I look in my gnome menu I see descriptions of applications, eg Calculator not GCalculator,

[sarcasm]
It's so nice when you have 'Web Browser' listed on the menu 3 times with no indication as to which menu item links to what browser. Not showing the actual name of the program being run also makes it so much easier to get help.[/sarcasm] :P

Later, Seeker

---

### Post by afrodeity on 2009-12-03
Here's the solution - Kludgets [http://www.omgubuntu.co.uk/2009/09/os-x-widgets-linux.html](http://www.omgubuntu.co.uk/2009/09/os-x-widgets-linux.html)

---

### Post by afrodeity on 2009-12-03
Any idea where the application should be parked? Usr/bin or where else? It just downloads onto the desktop as an executable.

---

### Post by Zorael on 2009-12-03
> **afrodeity said:**
> Any idea where the application should be parked? Usr/bin or where else? It just downloads onto the desktop as an executable.
Binary downloads are the devil! ;3

I usually place out-of-package stuff (like scripts I wrote myself) into **/usr/local/bin** to keep content in **/usr/bin** all tracked by dpkg.

---

### Post by quinntar on 2009-12-05
Actually it's quite easy to run plasma desktop and gnome at the same time...
go under your gnome session then once done, open a terminal and simply launch 

```
plasma-desktop &

```
and it works

This being said, It's not really necessary to have the two desktops but it's quite fun :)

---

