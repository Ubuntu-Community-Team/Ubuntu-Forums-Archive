---
title: "Gnome toolbar, need ideas to reduce all the clutter."
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by Gen2ly on 2007-07-10
[FONT="Fixedsys"]I know this may not seem like a lot but it is for me.  Lately I've grown tired of having icons cluttering my desktop and just want a clean efficient look.  I've done pretty well but I need some thoughts and ideas.  Here is my current gnome toolbar:[/FONT]

[IMG]http://ia300208.us.archive.org/3/items/TooManyToolbarIcons/toomanyicons.png[/IMG]

[FONT="Fixedsys"]Not too bad but since I have a limited size video monitor it is definitely  too much.  Problem is that everything there is what I need.  NetworkManager I use for different areas, I use the terminal all the time, tomboy (A must!), I like to see my cpu and what it's doing.  I have to hold suspend at times so I don't get maylaid in game ;), the time, duh, and the show desktop applet I use periodically.  So here's what I'm looking for:[/FONT]
[LIST]
[*][FONT="Fixedsys"]Tilda's the drop-down console is busted since gnome 2.18 - it has screen drawing problems.  But wouldn't it be nice if you could minimize it to the notification area like say Rhythmbox does?  Is ther an app that can minimze another app to the notification area?[/FONT]
[*][FONT="Fixedsys"]Firefox isnt necessary a must but it is handy.  Is there a way to bind it to a launch-key?  Say pressing cntl-F10 for instance?[/FONT]
[*][FONT="Fixedsys"]Also, I'd like a tranparent clock that just hovers over the desktop.  I guess the best way to put it would be like those logo's you see on tv that tell a stations callsign, only as a timeclock!  Wouldn't that be neat![/FONT]
[/LIST]

[FONT="Fixedsys"]Any ideas on what I can do?[/FONT]

---

### Post by macogw on 2007-07-10
Beryl lets you set a dozen launch keys.  There's a way to do it in regular GNOME too, but I don't know it.

---

### Post by hyperair on 2007-07-11
You want a semi-transparent clock eh? screenlets or cairo clock might be the one for you, but you'll need to install a compositing manager like Beryl or Compiz Fusion or something of that sort.

---

### Post by timo1023 on 2007-07-11
> **Dirk.R.Gently said:**
> 
[LIST]
[*][FONT="Fixedsys"] Is ther an app that can minimze another app to the notification area?[/FONT]
[/LIST]


Alltray

---

### Post by xl_cheese on 2007-07-11
How about one menu icon on the panel.  the first selection in the menu would be the main menu.  Above it place all of your most used programs.

You're just adding one extra click to get to the programs you use most to have much more space on your panel.

---

### Post by psyopper on 2007-07-11
Why not try [Conky]("http://conky.sourceforge.net/")? It can put your clock and CPU info on the desktop rather than your bar. It can also run terminal commands with grep so that you can pull out specific "update" data. You would be surprised how up you could remove from the bar...

```

sudo apt-get install conky

```

To run Conky hit [ALT]+[F2] to open the run command, then type in conky

Curious how to make it work? Take a look that the [Post your conky.rc thread]("http://ubuntuforums.org/showthread.php?t=281865") on this very forum.

Searching the forum for Conky will get you a ton of useful information.

---

### Post by revertex on 2007-07-11
you can get a transparent clock in your desktop with gdesklets.

i've found stjerm (weird name) a good tilda replacement, you can grab a deb package here:

[http://forums.opencompositing.org/viewtopic.php?f=18&t=1158](http://forums.opencompositing.org/viewtopic.php?f=18&t=1158)

---

### Post by Gen2ly on 2007-07-11
[FONT="Fixedsys"]I'd like to thank all for the responses  This helped alot.  I tried all the ideas and here's what I came up with.  First of all I removed time, system monitor and desktop.  With the desktop applet, I learned that hide/show desktop can be key binded in the control panel "Keyboard Shortcuts." - I setup ctrl-alt-D and it works nice.  Then I decided Conky was a nice idea as it could handle alot of different processes:[/FONT]

[IMG]http://www.archive.org/download/Gnome-panelMakeRoom/Real-Estate-Save.png[/IMG]

[FONT="Fixedsys"]Unfortunately the vbe (oops dbe) driver which conky needs isn't stable on my computer not allowing a clean exit from X sometimes and has a couple drawing problems.  So am not using this method at this time.  Next I tried the clock options.  gdesklets was nice after a couple trys translucency worked:[/FONT]

[IMG]http://www.archive.org/download/Gnome-panelMakeRoom/screen.png[/IMG]

[FONT="Fixedsys"]I also added "alltray".  Nice app.  It only has support for a few apps but since it has it for gnome-terminal, I'm happy.  I use the terminal quite a bit.  Just enter into [COLOR="DarkRed"]System > Preferences > Sessions[/COLOR] and add the program:[/FONT]
```
alltray gnome-terminal
```
[FONT="Fixedsys"]... to see it at every startup.  With gdesklets, I'm not sure just yet if I'll be using it all the time.  Since Compiz isn't all that for playing games, et. al. I may decide to return to the time in the panel setup.  I haven't got to trying stjerm just yet.  I'll tray that tomorrow.  All is much better though, appreciate the help.[/FONT]

---

### Post by revertex on 2007-07-11
Cool, pretty nice conky.

conky use very few  resources, maybe this thread can help you with some ideas.

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

also you can use more than one conky instance at the same time.

---

### Post by weblordpepe on 2007-07-11
*que the wilson-fillips music*

[IMG]http://www.colby-sawyer.edu/images/image_10253.jpg[/IMG]
What we neeeed is a hide notifications icon applet! Good enouuuugh to hide all the icons we dont want on screen. 

Hiding a dozen icons or mooooore.
Just like windows XP has on the botoooommm!

*music goes away*

---

### Post by revertex on 2007-07-11
[@Dirk.R.Gently]("http://ubuntuforums.org/member.php?u=200557")

if you are looking for a minimalistic desktop why not give a try to fvwm, openbox or fluxbox?

fvwm is a bit complex to configure, but worth, you can replace metacity for openbox easily, and fluxbox is dead easy to configure.

---

### Post by revertex on 2007-07-11
> **weblordpepe said:**
> *que the wilson-fillips music*

[IMG]http://www.colby-sawyer.edu/images/image_10253.jpg[/IMG]
What we neeeed is a hide notifications icon applet! Good enouuuugh to hide all the icons we dont want on screen. 

Hiding a dozen icons or mooooore.
Just like windows XP has on the botoooommm!

*music goes away*

jusr right click and select "remove from panel", you are done.

---

### Post by urukrama on 2007-07-12
You can try out [apwal]("http://apwal.free.fr/"). If you bind it to a keyboard shortcut, whenever you press those keys a set of icons will appear around your mouse cursor in whatever shape and order you like. It works like a launcher panel, but doesn't have to be continually running (you just activate it whenever you need it, and once you've launched the program you desire, it closes). It is very light on resources, and very configurable. It is in the repos, so 

> sudo apt-get install apwal
will be all you need to do.

---

### Post by hyperair on 2007-07-12
Wow, sounds like a realy cool app. Wish I'd noticed it before.

Anyway while I don't really like Windows XP, the hide inactive icons on the notification tray is rather handy. Currently, my power button gets pushed offscreen pretty often, so I have to close some apps before it'll come back.

---

### Post by Gen2ly on 2007-07-12
[FONT="Fixedsys"]I just compiled and been using stjerm.  It's pretty neat:[/FONT]

[IMG]http://www.archive.org/download/StjermANewDropConsole/stjerm.png[/IMG]

[FONT="Fixedsys"]I've been considering trying fluxbox.  I have my gnome top almost exactly like I want it so I am not sure if I want to take the time to fix it if flux doesn't work.[/FONT]

---

### Post by hyperair on 2007-07-12
My tilda looks like that, just without the borders. ^^

I managed to get it to support true transparency by following these instructions:
[http://lj4newbies.blogspot.com/2007/06/true-transparency-tilda-terminal-on.html](http://lj4newbies.blogspot.com/2007/06/true-transparency-tilda-terminal-on.html)

---

### Post by Nythain on 2007-07-12
you could also consider getting used to alt+F2 and running commands that way.

another thing, have you considered having a psuedo transparent and tinted/shaded gnome terminal running borderless on your desktop so it looks very integrated, all the cool kids are doing it :)

sorry to hear conky didnt work out for you... didnt know it relied on vbe... i know that dbe (double buffer) is used to keep it from flickering

also if you dont mind the qt/kde libraries on your machine you could give conideration to yakuake and possibly superkaramba (not sure how well this actually runs in gnome)

and finally FLUXBOX is awesome... it takes a bit to figure out, but once you get it goin, its a pretty powerfull and light mojo

---

### Post by revertex on 2007-07-12
> **Dirk.R.Gently said:**
> [FONT=Fixedsys]I[/FONT]
[FONT=Fixedsys]I've been considering trying fluxbox.  I have my gnome top almost exactly like I want it so I am not sure if I want to take the time to fix it if flux doesn't work.[/FONT]

You can replace metacity by openbox in no time.

there is a pretty nice tutorial by stormy eyes here, he's a hardcore openbox user.

[http://ubuntuforums.org/showthread.php?t=75471&highlight=replace+metacity+openbox](http://ubuntuforums.org/showthread.php?t=75471&highlight=replace+metacity+openbox)

more here

[http://icculus.org/openbox/index.php/Help:GNOME/Openbox](http://icculus.org/openbox/index.php/Help:GNOME/Openbox)

if you miss desktop icons install rox and use rox-pinboard.

or replace by xfwm

[http://ubuntuforums.org/showthread.php?t=88393&highlight=replace+metacity+openbox](http://ubuntuforums.org/showthread.php?t=88393&highlight=replace+metacity+openbox)

being a former long time fluxbox user i don't recomend it, its dead easy to configure, tabs are really nice and i miss it, but it's kinda sloooow.

---

### Post by urukrama on 2007-07-12
> **revertex said:**
> You can replace metacity by openbox in no time.

there is a pretty nice tutorial by stormy eyes here, he's a hardcore openbox user.

[http://ubuntuforums.org/showthread.php?t=75471&highlight=replace+metacity+openbox](http://ubuntuforums.org/showthread.php?t=75471&highlight=replace+metacity+openbox)


This howto is largely unnecessary if you install the latest version of Openbox (3.4), which I really recommend. A lot of options were added to 3.4 that weren't there in 3.3, and a lot of bugs were fixed as well. (Some of the configuration tips in the above mentioned howto are still useful in 3.4)

If you install Openbox 3.4, available [here]("http://icculus.org/openbox/index.php/Openbox:Download"), you'll have a session "Gnome + Openbox" you can select in GDM.

---

### Post by j2fraser on 2007-07-12
Well, for starters, you can always use [[COLOR="Red"]drawers[/COLOR]]("http://www.gnome.org/learn/users-guide/2.14/gospanel-18.html") to declutter your panels. Also, if you don't want open apps to clutter the appearance of your panels, you can always remove the panel object that displays them (can't remember what it is called now, from work). Can you configure a [[COLOR="Red"]window selector applet[/COLOR]]("http://www.gnome.org/learn/users-guide/2.14/panel-default.html")?

---

### Post by weblordpepe on 2007-07-12
> **revertex said:**
> jusr right click and select "remove from panel", you are done. Thats not a solution. Wilson Phillips wont approve either.
XP's hide notification icons is a simple & effective way of reducing clutter. Its something that Gnome & KDE could benefit from.

---

### Post by revertex on 2007-07-12
> **weblordpepe said:**
> Thats not a solution. Wilson Phillips wont approve either.
XP's hide notification icons is a simple & effective way of reducing clutter. Its something that Gnome & KDE could benefit from.

sorry i didn't understand, can you explain why that's not a solution an why  XP's hide notification icons is in any way better?

in both methods you can get rid of notifications icons, i really can see the difference.

bear in mind that linux is not windows, it's a completely different way to do the same tasks.

---

### Post by revertex on 2007-07-12
> **hyperair said:**
> My tilda looks like that, just without the borders. ^^

I managed to get it to support true transparency by following these instructions:
[http://lj4newbies.blogspot.com/2007/06/true-transparency-tilda-terminal-on.html](http://lj4newbies.blogspot.com/2007/06/true-transparency-tilda-terminal-on.html)

pretty neat, only thing that make me drop tilda is the lack of transparency under composite.

does tilda animation effect work with composite?

---

### Post by weblordpepe on 2007-07-12
> **revertex said:**
> sorry i didn't understand, can you explain why that's not a solution an why  XP's hide notification icons is in any way better?

in both methods you can get rid of notifications icons, i really can see the difference.

bear in mind that linux is not windows, it's a completely different way to do the same tasks. Because removing them from the panel means you have to fumble about with going into the application to add them again. The only choice is to have the tool on screen 100% of the time, or to not have that tool.
With the hide notification icons thing its a very quick & easy way to have lots of notification icons running and quickly get them out of the road. And then to get them back again with a single click. Like the drawer thing. Except not for launchers.

---

### Post by Nekiruhs on 2007-07-12
> **weblordpepe said:**
> Thats not a solution. Wilson Phillips wont approve either.
XP's hide notification icons is a simple & effective way of reducing clutter. Its something that Gnome & KDE could benefit from.
KDE has it, only GNOME could benefit.

---

### Post by weblordpepe on 2007-07-12
Real!!!??
Cool I couldnt figure it out in KDE. Where is it in KDE? Did I miss something obvious?

---

### Post by revertex on 2007-07-13
thank's weblordpepe, i didn't realise that gnome wasn't this feature.

maybe because i run very few apps in the tray, but it's really a shame that gnome devs don't care to implement this feature.

last time i did a kde a spin i noticed that autohide feature.

also in xp you can select to always show or always hide a trayicon.

---

### Post by weblordpepe on 2007-07-13
Yea I find it a vital feature. Something lacking from Gnome, eh.

---

### Post by weblordpepe on 2007-07-13
I figured out a compromise. You can add a draw, and then add the notification area to the draw.

---

### Post by urukrama on 2007-07-13
Here is a screenshot of my apwal configuration. The middle icon (Thunar) is located where my mouse cursor is when I launch apwal.

---

### Post by Gen2ly on 2007-07-13
> **Nythain said:**
> sorry to hear conky didnt work out for you... didnt know it relied [FONT="Fixedsys"]on vbe... i know that dbe (double buffer) is used to keep it from flickeringoops my bad there, meant dbe.[/FONT]
> and finally FLUXBOX is awesome... it takes a bit to figure out, but once you get it...
[FONT="Fixedsys"]I think I will try fluxbox or openbox first, oh and thanks for the links revertex.  I'm goona begin looking over these things and and try do something this weekend and be one of the cool ones ;)[/FONT]
> **urukrama said:**
> [FONT="Fixedsys"]Here is a screenshot of my apwal configuration. The middle icon (Thunar) is located where my mouse cursor is when I launch apwal.cool reminds me of playing Neverwinter :)[/FONT]

---

