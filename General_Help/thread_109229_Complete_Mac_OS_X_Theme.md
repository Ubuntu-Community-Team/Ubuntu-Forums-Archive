---
title: "Complete Mac OS X Theme?"
date: 2005-12-28
forum: General Help
---

### Post by jeffreyvergara.NET on 2005-12-28
is there any good Mac OS X theme, like:
[Ubuntu Mac OS Lookalike  ]("http://gnome-look.org/content/show.php?content=25165")
[MacOS-X Aqua Theme  ]("http://gnome-look.org/content/show.php?content=13548")

a step-by-step tutorial will be nice.

---

### Post by Nomearod on 2005-12-28
Ya... That would be nice...

But you could install GNOME Art ( Art Manager ) and searched there for a Mac Theme

---

### Post by Perfect Storm on 2005-12-28
Also you need gdesklets installed.

sudo apt-get install gdesklets

This may come in handy: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by Nomearod on 2005-12-28
[QUOTE=Artificial Intelligence]Also you need gdesklets installed.

sudo apt-get install gdesklets

This may come in handy: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)[/QUOTE]


But what desklet do we need do install to have a MacOS theme alike? ( the botton bar )

---

### Post by Perfect Storm on 2005-12-28
That one that match a Mac theme? It's called **Starterbar-desklet**

[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210)

---

### Post by jeffreyvergara.NET on 2005-12-28
[QUOTE=Artificial Intelligence]That one that match a Mac theme? It's called **Starterbar-desklet**

[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210)[/QUOTE]

Thanks A.I. i did not know that starterbar-desklet until now.

i found [gnoMac Theme Pack 1.0 ]("http://gnome-look.org/content/show.php?content=19714") but the package is to huge, there's too many choices, many themes to install. but the Icons included are nice

---

### Post by Perfect Storm on 2005-12-28
If I was you I'll find the diffrent stuff piece by piece (eg. the icons) find them on gnome-look.org and install them. Then go step by step 'till you're saticefied.

---

### Post by jeffreyvergara.NET on 2005-12-29
it seems im having problem with starterbar. i got errors and added Icons don't show.

---

### Post by jeffreyvergara.NET on 2005-12-29
i would also like to change the top panel without changing the whole theme. see screenshots.

im using ale-panther_gtk2 and gnoapple-icons and cursor. my Mac OS X theme is almost complete, the only problem is the top panel ang gdesklet

---

### Post by anil_robo on 2005-12-29
[quote=Nomearod]Ya... That would be nice...

But you could install GNOME Art ( Art Manager ) and searched there for a Mac Theme[/quote]

Art manage doesn't have a built-in search. One has to read the entire theme list manually! :(

---

### Post by Perfect Storm on 2005-12-29
[QUOTE=jeffreyvergara.NET]it seems im having problem with starterbar. i got errors and added Icons don't show.[/QUOTE]

Try with 

```
sudo apt-get install python-xdg
```

if that doesn't help 

```

sudo apt-get install gdesklets-data

```

---

### Post by Perfect Storm on 2005-12-29
[QUOTE=jeffreyvergara.NET]i would also like to change the top panel without changing the whole theme. see screenshots.

im using ale-panther_gtk2 and gnoapple-icons and cursor. my Mac OS X theme is almost complete, the only problem is the top panel ang gdesklet[/QUOTE]

If yo uhave the other theme (as shown in the screenshot). Go to that theme (/home/<usename>/.themes/<name of the theme> and see if you can find the specific .png file. When found drag it up to the panel and the panel change.

---

### Post by jeffreyvergara.NET on 2005-12-29
I manage to have a Mac OS X look using Rpanther2 theme and Gnome-Apple Icons. I also change the ubuntu logo beside application to apple logo. the only problem with the Icon theme is that there are some icons that are missing like  volume control and show desktop, so I edited index.theme and insert "Inheritance=gnome" of Gnome-Apple icon so the volume control on the top panel will show. but there's a problem again with that, the diskdrives icons changes to gnome default.

Im also trying to figure out gdesklet and the error when i used Starterbar

---

### Post by veehell on 2005-12-29
[QUOTE=jeffreyvergara.NET]is there any good Mac OS X theme, like:
[Ubuntu Mac OS Lookalike  ]("http://gnome-look.org/content/show.php?content=25165")
[MacOS-X Aqua Theme  ]("http://gnome-look.org/content/show.php?content=13548")

a step-by-step tutorial will be nice.[/QUOTE]

on that link there is step.by.step howto install MacosX theme. (i am using Aqua aswell) I did not found any other, only this one. 

To have panel with similar behavior as from Tiger, there are several gDesklets (as some user already mention) From my experience, gDesklets are quite consumers of RAM and CPU (if you start using them instead of gnome parts) I test it, it looks nice, but i rather return to default panel from gnome (much much faster, no refresh problems)

---

### Post by jeffreyvergara.NET on 2005-12-29
ok, I manage to run starterbar, the problem is it does not support the language I am using... (i think) so i change to english and it worked fine.

about gdesklet, how can you make it always on-top? and it seems that the icons is a bit small and when highlighted it becomes to large. I used 48x48 icons.

---

### Post by tigrez on 2005-12-29
I've installed the gDesklet and the StarterBar, and I've the same problem.
This is a semi-solution:
right-click on the starter-bar and "View Source"
After some line you found this:
[COLOR="Red"]<display anchor="center" window-flags="**below**,sticky"[/COLOR]
if you change **below** with **above**, your desklet stay on top, but it show the background wallpaper over all windows! 
It may be only a my vesa driver problem...

So I've restored **below** and added another line.
This is a piece of the source:
<display anchor="center" window-flags="below,sticky"
[COLOR="Red"]	desktop-borders=",-50"
[/COLOR]         on-enter="iconbar:enter"
         on-leave="iconbar:leave"
         on-menu="iconbar:menu"
	 on-file-drop="iconbar:add">

And changed the zoom in "Configuration" at 70%

Remember to save the changed and **Restart Desklet** to view the effects.

I suggest to change the -50 from -30 to -100 and look if is more nice.

This work only if u have the bar at bottom.

Sorry for my english!

;-)

---

### Post by ekravche on 2005-12-29
all these lookalike themes do not even come close to the actual mac osX UI.

---

### Post by sciurus on 2005-12-29
[QUOTE=ekravche]all these lookalike themes do not even come close to the actual mac osX UI.[/QUOTE]

But they look nice. Personally, I'm not a huge fan of the brushed metal look. For several months I've stuck with variations on

---

### Post by zammi on 2005-12-29
Hi,

Following are the latest in the town (If you are Tiger fan):
[http://www.gnome-look.org/content/show.php?content=30859](http://www.gnome-look.org/content/show.php?content=30859)
[http://www.gnome-look.org/content/show.php?content=30972](http://www.gnome-look.org/content/show.php?content=30972)
(You will get link to a good icon theme as well).

BTW:
Don't forget to visit my KDE cutormization as well.
[http://www.kde-look.org/content/show.php?content=30919](http://www.kde-look.org/content/show.php?content=30919)
[http://www.kde-look.org/content/show.php?content=23535](http://www.kde-look.org/content/show.php?content=23535)

---

### Post by jeffreyvergara.NET on 2005-12-30
Thanks tigerz it worked!
Here's my latest Mac OS X Tiger? Theme.. ^^

what is the command to use Trash? The 2 icons of the far right side of my Starterbar is just to make it somehow look like OS X.

---

### Post by tigrez on 2005-12-30
Your icon stay above or below all windows? 
Do you have activated the trasparency of deklets?
I'd like to see if desklets use trasparency over the windows or not...
If you put a thumbnail showing this effet, i'm very happy! :-)

---

### Post by jeffreyvergara.NET on 2006-01-01
hmm.. im really new with gdesklet. 
only the panel stays on top, when the icons are zoomed in, it stays below the window.
i really want to add workspace switcher and trash in starterbat but I dont know how,

---

### Post by jeffreyvergara.NET on 2006-01-01
just a update for my MacOSx theme.

---

### Post by jeffreyvergara.NET on 2006-01-02
this mac os x theme for kde really looks great.
[http://www.kde-look.org/content/show.php?content=30789]("http://www.kde-look.org/content/show.php?content=30789")

this one for gnome.
[http://gnome-look.org/content/show.php?content=19075]("http://gnome-look.org/content/show.php?content=19075")

---

### Post by jeffreyvergara.NET on 2006-01-02
hello, can someone send me 48x48 apple logo Icon, i lost my icon set and that the only Icon im missing, i dont want to download whole set again. thanks

---

### Post by Perfect Storm on 2006-01-02
This one?

---

### Post by jeffreyvergara.NET on 2006-01-03
thanks A.I.
btw, do you know where to get "Engage"? I got this somewhere:
> deb [http://j.portalier.free.fr/debian/](http://j.portalier.free.fr/debian/) testing main
but I think it is broken.

---

### Post by mgchan on 2006-01-08
Does anyone know if there is a custom icon for the wireless status?

How exactly did you get the volume icon to show up under your theme?  Mine keeps disappearing with certain themes.

Also, what font is it that you are using?

---

### Post by MJRehrig on 2006-03-04
Can anyone tell me where to get the Gnome-Apple icon set?

Thank you.

---

### Post by drguitarum2005 on 2006-03-10
[QUOTE=tigrez]I've installed the gDesklet and the StarterBar, and I've the same problem.
This is a semi-solution:
right-click on the starter-bar and "View Source"
After some line you found this:
[COLOR="Red"]<display anchor="center" window-flags="**below**,sticky"[/COLOR]
if you change **below** with **above**, your desklet stay on top, but it show the background wallpaper over all windows! 
It may be only a my vesa driver problem...

So I've restored **below** and added another line.
This is a piece of the source:
<display anchor="center" window-flags="below,sticky"
[COLOR="Red"]	desktop-borders=",-50"
[/COLOR]         on-enter="iconbar:enter"
         on-leave="iconbar:leave"
         on-menu="iconbar:menu"
	 on-file-drop="iconbar:add">

And changed the zoom in "Configuration" at 70%

Remember to save the changed and **Restart Desklet** to view the effects.

I suggest to change the -50 from -30 to -100 and look if is more nice.

This work only if u have the bar at bottom.

Sorry for my english!

;-)[/QUOTE]


This didn't seem to do anything for me at all. Am I missing a step? Also, I added firefox to it but it won't allow me to use the .png icons, is this right? thanks!

---

### Post by Laterix on 2006-03-10
Here is my current osx-look-a-like gnome desktop. I'm still working on it to make it better. As you can see from the screenshot, I'm also writing a mac-look guide for ubuntu newbies.

[img]http://users.utu.fi/ljtaim/pics/macthumb.png[/img]
[Full version](http://users.utu.fi/ljtaim/pics/maclook.png)

---

### Post by Perfect Storm on 2006-03-10
That's a real beauty, I must say.

---

### Post by drguitarum2005 on 2006-03-10
What are yall using for the dock? I tried the gdesklet, uh, StarterBar, but I can't get transparency and/or always on top and I can't even add icons, everything is just a question mark. i tried adding them but all the icons in .png format are greyed out.

---

### Post by Perfect Storm on 2006-03-10
You properly are missing some libs I guess.

I know Starterbar needs pyxdg, so you might try with that first.

```
sudo apt-get install python-xdg
```

To make it stay on top you may have to change starterbar config file.
By the way they won't be true transperant. You can't see your windows behind it. Only the wallpaper.

---

### Post by drguitarum2005 on 2006-03-10
I already had that python library. I copmletely removed gdesklets, starterbar, and the library and reinstalled them in synaptic/downling starterbar and still the same. icons are just questionmarks and all icon options are greyed out.

Edit: i fixed the icon part, the transparency thing is very annoying however

---

### Post by steveneddy on 2006-03-12
Here's what I did to get close to the Mac theme on my personal PC.

To get close to MAC-OSX look, I used the theme's from art.gnome.org and gnomelook.org for the mouse and other widget stuff. I installed gdesklets for the starter bar (very cool, btw), added the clock, calender and weather gdesklet just because I like them. 

GlossyP from art.gnome.org
Border is CrispBlue
Icons are OSX
I also used the glass mouse from gnomelook.org

This is my version only and is my interpretation of the Mac OS. I didn't try to emulate it perfectly, just tried to get in the neighborhood.

I would put an image up, but.............

EDIT: nevermind

---

### Post by terranz on 2006-03-12
so Laterix, how far have you come with that how-to?

---

### Post by drguitarum2005 on 2006-03-12
[QUOTE=steveneddy]Here's what I did to get close to the Mac theme on my personal PC.

To get close to MAC-OSX look, I used the theme's from art.gnome.org and gnomelook.org for the mouse and other widget stuff. I installed gdesklets for the starter bar (very cool, btw), added the clock, calender and weather gdesklet just because I like them. 

GlossyP from art.gnome.org
Border is CrispBlue
Icons are OSX
I also used the glass mouse from gnomelook.org

This is my version only and is my interpretation of the Mac OS. I didn't try to emulate it perfectly, just tried to get in the neighborhood.

I would put an image up, but.............

EDIT: nevermind[/QUOTE]


is that true transparency on your terminal and starter bar?

---

### Post by drguitarum2005 on 2006-03-12
here is mine by the way
a couple things i don't like:

the giant fake transparent area behind desklets, mainly the starterbar if you put it "always on top", so i have it behind for now and use shift+f12
the weird gray boxes in my panel around standard icons-need to figure out how to change that

other than that I think its gettin close

EDIT: the other two gdesklets in the lower left corner are not os x related, im just tinkering

---

### Post by byen on 2006-03-12
looks pretty neat...can you tell us which GTK theme you are using for the taskbar? 
thanks!

---

### Post by routerstu on 2006-03-12
yes, please write a how-to.  i think there would be a lot of people who appreciate it.

Thanks!

---

### Post by drguitarum2005 on 2006-03-13
i'm going to try my best to remember where I got these things...

I am using certain elements from a package called mac-osx-bundle...possibly from gnomefiles or something of the like

i am also using "RPanther2" for "controls" and "window border" (in gnome theme manager) and icons are "OSX"

mouse is also OSX

if you need any more information i'll be glad to find it

---

### Post by byen on 2006-03-13
[QUOTE=drguitarum2005]i am also using "RPanther2" for "controls"[/QUOTE]
Thanks buddy... gonna try it out now and digg in a little.....

---

### Post by Laterix on 2006-03-13
[QUOTE=terranz]so Laterix, how far have you come with that how-to?[/QUOTE]
I'm sorry to tell you that I haven't advanced with it much lately, because I've had some hard exams. So all my time goes with my studies, but I try to get it done at the end of the week.

---

### Post by terranz on 2006-03-13
I have found a nice looking osx theme but the widgets for minimise maximise and close are on the right wher as osx has them on the left.  Can I change that?

Also can I change those ugly tabs on the ends of the panels?

---

### Post by mgchan on 2006-03-13
[QUOTE=terranz]I have found a nice looking osx theme but the widgets for minimise maximise and close are on the right wher as osx has them on the left.  Can I change that?

Also can I change those ugly tabs on the ends of the panels?[/QUOTE]
You can change which side the minimize and maximize buttons are in the Configuration Editor (Ubuntu Menu -> System Tools -> Configuration Editor).

Go to "apps -> metacity -> general" and edit "button_layout" to your liking.  It's pretty obvious how to format it.

After you're done, restart metacity (run 'metacity-message restart').

The arrows at the ends of the panels are affected by the theme you use.  You can change them somewhat in the Panel Properties (Show hide buttons, Arrows on hide buttons) but I don't know how to get rid of them.

---

### Post by aysiu on 2006-03-13
[QUOTE=mgchan]
Go to "apps -> metacity -> general" and edit "button_layout" to your liking.  It's pretty obvious how to format it.[/QUOTE] I don't know if it's *obvious*, but there are instructions: > Arrangement of buttons on the titlebar. The value should be a string, such as "menu:minimize,maximize,close"; the colon separates the left corner of the window from the right corner, and the button names are comma-separated. Duplicate buttons are not allowed. Unknown button names are silently ignored so that buttons can be added in future metacity versions without breaking older versions. 

---

### Post by terranz on 2006-03-14
Thanks.  I'm now a step closer.

---

### Post by jakeee on 2006-03-18
I'd like to know how to get rid of that ugly ubunto logo on the top panel and replace it with an apple logo.

---

### Post by Perfect Storm on 2006-03-18
rename your apple icon to distributor-logo and make it a .png if it aren't already.

then

```
sudo cp distributor-logo.png /usr/share/icons/hicolor/48x48/apps

```

---

### Post by mr.p on 2006-03-18
[QUOTE=Laterix]Here is my current osx-look-a-like gnome desktop. I'm still working on it to make it better. As you can see from the screenshot, I'm also writing a mac-look guide for ubuntu newbies.

[img]http://users.utu.fi/ljtaim/pics/macthumb.png[/img]
[Full version](http://users.utu.fi/ljtaim/pics/maclook.png)[/QUOTE]

Can't wait for this guide.

---

### Post by mr.p on 2006-03-26
[QUOTE=mr.p]Can't wait for this guide.[/QUOTE]
Any updates?

---

### Post by el_rata on 2006-03-27
anyone knows how to create an icon set ?? ... plzz let me know ...

---

### Post by Absolute on 2006-03-31
[QUOTE=Laterix]Here is my current osx-look-a-like gnome desktop. I'm still working on it to make it better. As you can see from the screenshot, I'm also writing a mac-look guide for ubuntu newbies.

[img]http://users.utu.fi/ljtaim/pics/macthumb.png[/img]
[Full version](http://users.utu.fi/ljtaim/pics/maclook.png)[/QUOTE]
Wow!  I can't wait! :)

---

### Post by Laterix on 2006-04-01
[QUOTE=Absolute]Wow!  I can't wait! :)[/QUOTE]
Argh, you guys are giving me pressures. I've been very busy with my studies and I'm very sorry, but It's still not ready. :( Perhaps I could put it available and finish it when I have time...

---

### Post by Hangetsu on 2006-04-01
That would be great!  Id be happy getting even halfway to what you've created.  Just list the guide as "DRAFT", and work on it when you can.

Thanks again, and kudos for such an amazing looking theme!

---

### Post by wangdang on 2006-04-01
just post a shortie for starters and you can write more later on?

like

xx-theme +gdesklets + this and that desklet + this and that application 

i'm completely dying to get a desktop that looks like yours

---

### Post by Laterix on 2006-04-02
OK, you won. The link is in my Signature.

If you see errors or misleading stuff in the guide, please tell me.

---

### Post by terranz on 2006-04-02
Thanks for the starter :-D

---

### Post by wangdang on 2006-04-02
how did you do the top gnome panel?

brilliant work btw

---

### Post by terranz on 2006-04-03
You know what would be really good?
Something like this
[http://www.osx-e.com/downloads/misc/flyakite_osx.html](http://www.osx-e.com/downloads/misc/flyakite_osx.html)

like automatix except without changing sources and stuffing things up.

---

### Post by Laterix on 2006-04-03
[QUOTE=terranz]You know what would be really good?
Something like this
[http://www.osx-e.com/downloads/misc/flyakite_osx.html](http://www.osx-e.com/downloads/misc/flyakite_osx.html)

like automatix except without changing sources and stuffing things up.[/QUOTE]
Yeah, I'm familiar with FlyakiteOSX. I used it when I had Windows on my computer. It would be possible to write a script which makes all the changes and downloads needed stuff from the internet, BUT... yes there is always a but. I don't have any experience on writing bash-scripts. I'm sure I would learn basics fast, but there's really no way to automate firefox "tweaks" for example. At least I can't think of any way to do this. And of course... time is an issue.

And after all... it's not that hard to do it with the guide, is it?

---

### Post by terranz on 2006-04-03
I would like to make that a project but I don't really know bash scripting either so I really would be a project.  Keeping me from linux at the moment is the fact that I can do everything but print at the moment (I could before I got a new printer)

---

### Post by s_h_a_d_o_w_s on 2006-04-03
This is my setup:

OS X icons  [http://www.gnome-look.org/content/show.php?content=31618](http://www.gnome-look.org/content/show.php?content=31618)

T Ish GTk 2.x [http://www.gnome-look.org/content/show.php?content=30859](http://www.gnome-look.org/content/show.php?content=30859)

OS X Background [http://users.utu.fi/ljtaim/images/tiger.jpg](http://users.utu.fi/ljtaim/images/tiger.jpg)

I know it isn't really OS X, but I like it.

Screenshot:

[http://pic.piczo.com/img/i120391145_93392_2.gif](http://pic.piczo.com/img/i120391145_93392_2.gif)

P.S. Laterix's guide (two posts above this one) helped me find the background and t-ish, Thanks Laterix!

---

### Post by Tipo on 2006-04-03
[QUOTE=s_h_a_d_o_w_s]This is my setup:

OS X icons  ([link]("http://http://www.gnome-look.org/content/show.php?content=31618"))

T Ish GTk 2.x ([link]("http://http://www.gnome-look.org/content/show.php?content=30859"))

OS X Background ([link]("http://http://users.utu.fi/ljtaim/images/tiger.jpg"))

I know it isn't really OS X, but I like it.[/QUOTE]

Is it just me, or do all those links that you posted redirect to [www.microsoft.com?](www.microsoft.com?)

---

### Post by s_h_a_d_o_w_s on 2006-04-03
I was just checking them out and you're right, but I just fixed them, they should work now. That was weird. 0_o

---

### Post by henriquemaia on 2006-04-03
What I would really like was to have an option to make the close button on metacity to work as in OSX. I mean, I want to close the window, but not the app. I can do something like that with alltray, but sometimes this does not work as expected. It would be so nice to have it as a gnome option...

---

### Post by curlydave200 on 2006-04-05
"I also change the ubuntu logo beside application to apple logo."

What did you do to change the icon?

---

### Post by Laterix on 2006-04-05
[QUOTE=curlydave200]"I also change the ubuntu logo beside application to apple logo."

What did you do to change the icon?[/QUOTE]
Overwrite this file with the icon you want to use.
```

/usr/share/icons/hicolor/48x48/apps/distributor-logo.png 

```

---

### Post by terranz on 2006-04-05
I went through that extensions how-to to get shadows and other effects and it crashed very quickly every time I used it so I think I'll wait to see what dapper offers in the way or visual effects.

---

### Post by el_rata on 2006-04-07
i can't change mi menu bar icon ... i don't know why ... any ideas? please post quickly ... !!!! see you soon

---

### Post by maccabbi on 2006-04-07
Some of these are pretty cool. I am new to ubuntu but I am a die hard mac fan, so I must say that if you really want an OSX look you need to change the button locations. Alot of people skipped this but it is easy. 
Launch gconf-editor
Go to /apps/metacity/general/
Change button_layout value to close,minimize,maximize:menu

Doing this with a good icon pack and a brushed metal theme looks pretty close. 

If I can figure out how to get online I will be quite pleased with ubuntu.

---

### Post by asusrules on 2006-04-17
[QUOTE=Laterix]Here is my current osx-look-a-like gnome desktop. I'm still working on it to make it better. As you can see from the screenshot, I'm also writing a mac-look guide for ubuntu newbies.

[img]http://users.utu.fi/ljtaim/pics/macthumb.png[/img]
[Full version](http://users.utu.fi/ljtaim/pics/maclook.png)[/QUOTE]


when do you think you will be done with the complete instructions for making ubuntu look like mac os?

---

### Post by asusrules on 2006-04-20
i heard that a new verison of ubuntu (6.06) will be released in june, if i already have the mac os theme on my current system, would i have to redo the theme on the new release or will the theme go to the new verison?

---

### Post by el_rata on 2006-04-20
if you upgrade from breezy 5.10 to dapper 6.06 (like i did) you keep all your themes .... it depends on the installation type .... if you make a new install from a CD you should backup your home folder.
dapper is already out, the official launch is in june ... and if you want to install dapper now, just change the repositories from breezy to dapper and do:

                  sudo apt-get update && apt-get dist-upgrade

and you'll have to sit because this method to get dapper takes a little while ....

---

### Post by steveneddy on 2006-04-30
[QUOTE=drguitarum2005]is that true transparency on your terminal and starter bar?[/QUOTE]

Yes it is. I used Eterm and set the starter in the little starter bar from Gdesklets to start it with no borders and no tool bar. Also told it to be transparant and how much....also have to tell it where on the desktop you want it because you can't move it without a border. To exit, just type exit.

Here are the commands for the launcher for eterm:

/usr/bin/Eterm -O -g 65x30+20+135 --shade 35

Let's see, where is the file, -O is for transparancy, -g is geometry (how big and where on the desktop) and finally the degree of transparancy

Hope this helps.

---

### Post by Laterix on 2006-05-31
Sorry about this long delay. I'm not sure will I complete my Mac look guide... perhaps I should, but I don't have motivation since I changed my desktop to orange dapper look + compiz.

I don't promise anything, but I try to complete it in the near future.

---

### Post by Grog140 on 2006-06-07
Laterix I just need to thank you for the great guid. I completed the mac thing and the reailzed I diddn't like the mac theme but I used that orange thing you have posted on your site and I love it in conjunktion with some of the mac stuff you had :)

---

### Post by JGKC9AYC on 2006-06-10
[QUOTE=Laterix]Overwrite this file with the icon you want to use.
```

/usr/share/icons/hicolor/48x48/apps/distributor-logo.png 

```[/QUOTE]

I tried that, then typed in killall gnome-panel & the Ubuntu logo's still there.

---

### Post by Perfect Storm on 2006-06-10
Put it in ~./theme/<themename>/128x128 or scalable/apps instead.

---

### Post by JGKC9AYC on 2006-06-10
> Put it in ~./theme/<themename>/128x128 or scalable/apps instead.

I didn't see a "128x128" or  "scalable/apps" in that theme folder...do I create it?

Another thing...instead of using gdesklet, I created another bar down at the bottom for my quick launch icons but it's visible all the time & takes away about 3/4" of viewable area when browsing.  Is there a way around that?

---

### Post by JGKC9AYC on 2006-06-11
OK...it seems that the icon needed to be in a totally different folder, so I got that took care of.
Now, the only problem i'm having is the Opera starter on my gDesklet starter bar.  For some reason, when I choose it, as soon as Opera loads, it disappears.  It did this after I updated my kernel from 686 to K7.  I posted about this in another thread, but I figured since I was updating this, i'd throw it in anyhow.  :)

---

### Post by rysh on 2006-06-15
[QUOTE=JGKC9AYC]OK...it seems that the icon needed to be in a totally different folder, so I got that took care of.[/QUOTE]

Can you share your knowledge with us, please. Because i am still looking for this change

---

### Post by rysh on 2006-06-15
[QUOTE=rysh]Can you share your knowledge with us, please. Because i am still looking for this change[/QUOTE]

OK i found out myself also already. In my case i had in the directory /usr/share/pixmaps a file called gnome-logo-icon-transparent.png which i renamed and then  i copied another icon in this directory and called it also gnome-logo-icon-transparent.png. 

I started with Ubuntu by a Kubuntu CD but changed it so it now runs with GDM, gnome, XGL and compiz. So the (k)ubuntu logo was in mycase a normal gnome foot. Which i wanted to change into an apple.

:D

---

### Post by TVMA on 2007-02-14
I don't know if anyone posted the link, but I've used this how to for MAC OS X theme on ubuntu


[http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php)

---

### Post by el_rata on 2007-02-28
laterix did a great job on that guide ....

---

### Post by Meatcart on 2007-04-12
> **TVMA said:**
> I don't know if anyone posted the link, but I've used this how to for MAC OS X theme on ubuntu


[http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php)
The results from that guide don't look like the screenshot he/she firstly posted..

[http://users.utu.fi/ljtaim/pics/ubuntu_osx.png](http://users.utu.fi/ljtaim/pics/ubuntu_osx.png)

Or is there another guide for that one? I must that this screenshot has the best osx look a like as far as I've seen, so I'd rather have that instead of the other ones.. I could mess around with it myself to get that result, but I'm just wondering if I'm missing something here?

---

### Post by keforex on 2007-10-24
> **jeffreyvergara.NET said:**
> is there any good Mac OS X theme, like:
[Ubuntu Mac OS Lookalike  ]("http://gnome-look.org/content/show.php?content=25165")
[MacOS-X Aqua Theme  ]("http://gnome-look.org/content/show.php?content=13548")

a step-by-step tutorial will be nice.

I am a complete n00b and although I do have some computer skills, I am new to linux.

I installed Ubuntu 7.10 on my x64 system and now I am trying to install this Mac OS theme but geez I can't find the folder "themes", and the whole install procedure isn't as clear for me as I would like. Since I am from a DOS/Windows environment, all these file extensions here are new for me and I have no clue on how to start doing a simple thing like changing the theme... 

Can anyone put here a step-by-step on how to install this Mac OS theme?... I've read almost all pages here but I am still puzzled. Where in the hell is the "themes" folder?.... If I don't have one, where should I create it, etc?... I feel like an idiot but this Linux thing is new (and frustrating).... thanks for any help!!

EDIT - NEVER MIND... I followed the link a few posts above... lets see what happens. If anyone has a better choice please post.... thanks anyways!!!

EDIT #2 - Well... isn't there anything like download and install for this?... I started reading the article but man, there are 3 million steps to achieve this Mac OS look., BTW, when I download stuff it usually shows up in a folder. This folder has a bunch of subfolders and files, but which one is the installer? This is so confusing... Also, my screen resolution is 2560x1600 native (30in monitor) and it seems like there's no Mac OS theme for this resolution huh... help!!!

---

### Post by virtualmaster on 2007-12-07
Guys, just so you know, installing xserver-xgl will allow you to use true transparency. it also lets compiz desktop effects work on unsupported hardware

---

### Post by shoaibi on 2008-07-15
i am unable to get the icons and wallpapers zip file at:
[http://gnome-look.org/content/show.php?content=13548](http://gnome-look.org/content/show.php?content=13548)

can anyone please upload these files as attachments or at somewhere else?

---

