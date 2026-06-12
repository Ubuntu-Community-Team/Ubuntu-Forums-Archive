---
title: "HOWTO: True transparent Gnome Panels with Compiz Fusion"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by Mr Greencastle on 2007-10-23
Not sure if anyone knows this, but I just found it out, and am excited (since I've wanted this forever) so I'm saying it anyway.

If you are running Compiz Fusion (If you can, I think you should), you can make the panel TRUE transparent. To do this, simply open up the Compiz settings manager:

```
ccsm
```

Or if you don't have it:

```
sudo apt-get install compizconfig-settings-manager
```

Then go to: General Options > Opacity Settings
and add a new one there: dock   (make opacity 80 or something)
Know that this makes the whole panel transparent, icons included, so don't make it TOO transparent.

There are a lot more that you can set aswell, such as:
dock = Dock/Menu Bar
dropdownmenu = Menus
popupmenu = Right Click Menus/Single Start Menu
tooltip = Tool Tip Popups

Also if you don't feel like using emerald to make you window borders/title bars transparent, you can do it by changing a property in gconf-editor.

```
gconf-editor
```
Its under Apps > gwd
Theres a setting for metacity_theme_active_opacity that should default at 1, change it to a value between 0 and 1, such as 0.75, and there you go!

By the way:

Here is an example of what it looks like (notice how you can actually see the window THROUGH the panel):
[[IMG]http://img100.imageshack.us/img100/4079/truetransparenttf2.th.png[/IMG]](http://img100.imageshack.us/my.php?image=truetransparenttf2.png)

And these are some interesting panels, 
[[IMG]http://img237.imageshack.us/img237/1332/65966version2er5.jpg[/IMG]](http://imageshack.us)

Just save the image to your Pictures folder, then drag and drop it onto a blank part of your panel and it should change.
(Originally for KDE, but I Gimped it for Gnome)...
[[IMG]http://img522.imageshack.us/img522/6360/stripededitdf1.png[/IMG]](http://imageshack.us)

Thanks to the authors of these, of course.

Hope that helped!

Mr Green

---

### Post by kelbizzle on 2007-10-24
where's the screen shot :-)

---

### Post by sekazi on 2007-10-24
It would be nice if it did the menus. I already have a transparent dock using a PNG.

---

### Post by Mr Greencastle on 2007-10-24
To make the menus transparent, add another one in the same place, but instead of dock, its called: dropdownmenu.

Hope it helped.

Also, I'll post a screenshot in a few minutes.

---

### Post by sekazi on 2007-10-24
Thanks. It looks much better now. Where do you find the entries at? I want to know what else can be made transparent.

---

### Post by Baby Boy on 2007-10-24
@Mr Greencastle

That setting looks awful on my desktop. How exactly can I make my panels look like yours?

---

### Post by Mr Greencastle on 2007-10-24
If you want the background for the panel I'll upload it here in a sec...
[[IMG]http://img237.imageshack.us/img237/1332/65966version2er5.jpg[/IMG]](http://imageshack.us)

When I do, just save the image to your Pictures folder, then drag and drop it onto a blank part of your panel and it should change.

I have this one now though (Originally for KDE, but I Gimped it for Gnome)...
[[IMG]http://img522.imageshack.us/img522/6360/stripededitdf1.png[/IMG]](http://imageshack.us)

By the way, I would like to thank whoever made this panel background, its excellent!

---

### Post by entropism on 2007-10-24
What would be the panel name to use for the "start menu" panels (trying to think of a non-windows term but failing miserably)

---

### Post by Mr Greencastle on 2007-10-25
I'm assuming you're talking about the menus that drop down (Apps, System, Prefs)?

If so, I posted up a bit on how to change that to transparent aswell.

Mr Green, an ex-Windows user... who doesn't quite get what you are saying ;P

---

### Post by sekazi on 2007-10-25
> **entropism said:**
> What would be the panel name to use for the "start menu" panels (trying to think of a non-windows term but failing miserably)
dropdownmenu
Thats what Mr Greencastle posted ealier. I think thats what you are looking for.

Mr Greencastle do you happen to know how to do the window boarders. I was to stay as far from emerald as possible. I already have the boarder I like but I want it transparent like the menus and dock.

Heres my dock image.

Not Transparent
[IMG]http://img171.imageshack.us/img171/7334/glossywhitesolidmenubarfo4.png[/IMG]

Transparent PNG
[IMG]http://img150.imageshack.us/img150/59/glossywhitetransparentmft4.png[/IMG]

---

### Post by Baby Boy on 2007-10-25
> **Mr Greencastle said:**
> If you want the background for the panel I'll upload it here in a sec...
[[IMG]http://img237.imageshack.us/img237/1332/65966version2er5.jpg[/IMG]](http://imageshack.us)

When I do, just save the image to your Pictures folder, then drag and drop it onto a blank part of your panel and it should change.

I have this one now though (Originally for KDE, but I Gimped it for Gnome)...
[[IMG]http://img522.imageshack.us/img522/6360/stripededitdf1.png[/IMG]](http://imageshack.us)

By the way, I would like to thank whoever made this panel background, its excellent!

Thanks a lot, I am using the first one. :)

---

### Post by Mr Greencastle on 2007-10-25
No problem!

And about the window borders, I'll see what I can do... I'll post again if I figure it out.

Mr Green

---

### Post by Mr Greencastle on 2007-10-25
Ok, so, there is no Value you can enter there as I know of BUT!
If using GTK, (Gnome) than this is what you CAN do: 
Open a terminal type
```
gconf-editor
```

Its under Apps > gwd
Theres a setting for metacity_theme_active_opacity that should default at 1, change it to a value between 0 and 1, such as 0.75, and there you go!

Thanks to the guys on IRC for the help.

Mr Green

---

### Post by Baby Boy on 2007-10-25
Thanks, that looks great! :)

---

### Post by mshaaban on 2007-10-25
Thanks for the tip ...
Panels look very cool this way
I tried it for the menus but it's a kind of confusing especially if u have a terminal or window open ..

---

### Post by praxis22 on 2007-10-25
I actually had a perfect desktop, with full transparent bars, but readable minimised window titles, and menus, etc. using beryl, and that remained when I upgraded to gutsy and got compiz-fusion working. However, I was mucking about a few night ago, and the desktop theme switched from a beryl themed emerald, to a default emerald, which now looks ****, It's got drop shadows which really spoils the effect, and the window decoration is horrible. Of course if I edit it, I'll lose all my other customisations. I'm going to have to rebuild and reinstall the Beryl manager, etc. just so I can get the themes back. V annoying. 

I may also have worked out how to get the screensaver working with a GL desktop, but that needs a bit more tweaking.

---

### Post by entropism on 2007-10-25
> **Mr Greencastle said:**
> I'm assuming you're talking about the menus that drop down (Apps, System, Prefs)?

If so, I posted up a bit on how to change that to transparent aswell.

Mr Green, an ex-Windows user... who doesn't quite get what you are saying ;P

Well, that WAS what I was talking about, but I changed my panels around so the dock is on the bottom and the menus are condensed into a start button.  Changing "dropdownmenu" no longer works for them, but it DID change the opacity of every other drop down menu.

---

### Post by Mr Greencastle on 2007-10-25
I'm guessing you changed from the "Menu Bar" to the "Main Menu"
I tried it myself, and it looks like it indeed does not make that transparent... very odd.

I'll investigate further, and see what I can do.

Mr Green

---

### Post by Mr Greencastle on 2007-10-25
Alrighty, so to make that Main "start button" Menu transparent. The name for it is: ```
popupmenu
```

Note that it will also make the context "right-click" menus transparent (which may be a good thing aesthetically)

Its weird that the Main Menu is treated as a different type of menu than the Menu Bar...
Mr Green

---

### Post by entropism on 2007-10-25
Thanks Green!  I have to say, after MANY failed attempts at trying to get into Linux, I'm ready to drop Windows completely after a week.  I was ready to write Gutsy off completely after installing Kubuntu and configuring BTNX (something messed up and my OS wouldn't boot), but Gnome is stable and working wonderfully for me.  This new version is almost perfect...  I just need X-fi support so I don't have to go into my BIOS and turn on on-board every time I swap OSes...

---

### Post by Mr Greencastle on 2007-10-25
I'm glad to hear that!
Its always good to see that more and more people are realizing that Linux is just better. And my OS of choice, Ubuntu, has such an excellent community.

All the best in your newest venture,

Mr Green

---

### Post by sekazi on 2007-10-25
Thanks Mr Greencastle. I have alot of transparency going on now. My video card is probably freaking by now.

Turning off metacity_theme_active_shade_opacity and metacity_theme_shade_opacity off makes the entire window border transparent.

```
tooltip
```

That is one I found. It makes the tooltips transparent.

---

### Post by praxis22 on 2007-10-25
I manged to work out what had happened, it had trashed the theme itself for some reason, so it defaulted to the first one in the list. I had a backup, so I lost nothing once I was able to find the themes again, but I had to manually install as they're not in the repos for gutsy.

Screenshot attached, (she's all digital before you ask)

This is using emerald as the window decorator, I'm running compiz, but it looked just the same running beryl:

name=Crystal-ICE
theme_version=0.3
creator=Jesper
description=Crystal like
suggested=Lipstik
version=0.61

Legacy engine

Theme comes from the emerald themes package.

I simply right clicked the panel, went into the "background" tab, checked "solid colour" and dragged the slider to "transparent" that way it doesn't effect the readability of the text. active menus are still white, but I think I have them at 95% opacity, for a little bit of translucency, but beyond that it makes it real difficult to read IMO. The active window shows up as white-ish  on the bottom bar too but it's also at 95%

---

### Post by Mr Greencastle on 2007-10-25
Crazy background!

I try not to use emerald myself, but I'm stuck in a position between having a cool GTK theme, but crappy window border, or use emerald with it.

---

### Post by praxis22 on 2007-10-26
[http://market.renderosity.com/mod/bcs/index.php?ViewProduct=44150](http://market.renderosity.com/mod/bcs/index.php?ViewProduct=44150)

There's a link on that page to a "full body render"  resize it to 1600x1200 and you'll get the same aspect as mine. It's for a program called Poser. May even work under wine, as it's a purely software renderer, make no use of accelerated 3D at all.

---

### Post by markp1989 on 2007-10-27
any one know how to add transparency to the menu when you right click on the desktop in gnome?

---

### Post by sekazi on 2007-10-27
> **markp1989 said:**
> any one know how to add transparency to the menu when you right click on the desktop in gnome?

All of the ones we have went though so far is

dock = Dock/Menu Bar
dropdownmenu = Menus
popupmenu = Right Click Menus/Single Start Menu
tooltip = Tool Tip Popups

The one you are looking for is popupmenu.

---

### Post by markp1989 on 2007-10-27
> **sekazi said:**
> All of the ones we have went though so far is

dock = Dock/Menu Bar
dropdownmenu = Menus
popupmenu = Right Click Menus/Single Start Menu
tooltip = Tool Tip Popups

The one you are looking for is popupmenu.

thankyou worked extreamly well:D

---

### Post by itsbradman on 2007-10-28
Great!!  I was wondering how to do that!!  Now my desktop is complete after almost losing everything after the Gutsy upgrade.

---

### Post by Baby Boy on 2007-10-28
> **itsbradman said:**
> Great!!  I was wondering how to do that!!  Now my desktop is complete after almost losing everything after the Gutsy upgrade.
Wow, nice job.

---

### Post by Mr Greencastle on 2007-10-28
Nice desktop!

> dock = Dock/Menu Bar
dropdownmenu = Menus
popupmenu = Right Click Menus/Single Start Menu
tooltip = Tool Tip Popups

I added that to the beginning of the guide.

Mr Green

---

### Post by itsbradman on 2007-10-28
Good deal and thanks for the compliment.  It's amazing what you can do with open source these days.  I couldn't even get that pitiful excuse of eye candy called aero to run on this machine. lol.  If anyone has any other suggestions or tips or questions, post um here.

---

### Post by itsbradman on 2007-10-28
ok, another one.  The only window that pops up now, that isn't translucent, is the rythmbox display that show what song is playing.  Any ideas?

---

### Post by ecschiel on 2007-11-01
> **itsbradman said:**
> ok, another one.  The only window that pops up now, that isn't translucent, is the rythmbox display that show what song is playing.  Any ideas?

Just use [COLOR="Blue"]notification[/COLOR] as the window type... that should do the trick:lolflag:

---

### Post by Baby Boy on 2007-11-02
> **ecschiel said:**
> Just use [COLOR="Blue"]notification[/COLOR] as the window type... that should do the trick:lolflag:
Any way to make that work for Amarok? I am referring to the popup which shows what song is playing when I place my mouse arrow over the Amarok icon in the upper panel.

(I've already added notification as the window type)

---

### Post by ecschiel on 2007-11-03
> **Baby Boy said:**
> Any way to make that work for Amarok? I am referring to the popup which shows what song is playing when I place my mouse arrow over the Amarok icon in the upper panel.

(I've already added notification as the window type)

I really don't know what window type to use there, but I was googlin and find something nice.

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

Look there for window matching instructions, it's really complete and with that info you can apply any filter that you can imagine. I tried to find out how to make transparent that, but when you try to get the properties of the window (the popup u say) it vanishes and doesn't come back till you finish the command. Read that link and you'll see what I mean. I don't use amarok (rhytmbox instead) but i supose that it's the same type of window, so if u find out how to made it transparet (or anybody else) just post it here so everybody could do the same (me included :lolflag:)

---

### Post by Mr Greencastle on 2007-12-02
> I really don't know what window type to use there, but I was googlin and find something nice.

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

Wow, I've been looking for something like that for awhile. This is going to make me mess with my settings for another  few days. I love it, thanks.

---

### Post by 1nc0gnit0 on 2007-12-19
Is it possible to make only the top panel transparent, without the AWN dock? Because "dock" affects AWN dock as well...

---

### Post by hhhhhx on 2007-12-20
it would be nice if it dident effect awn:(

---

### Post by ecschiel on 2007-12-21
> **1nc0gnit0 said:**
> Is it possible to make only the top panel transparent, without the AWN dock? Because "dock" affects AWN dock as well...

I'm not sure what u mean with AWN, try to explain me some more and i will try to find a way out =D

---

### Post by 1nc0gnit0 on 2007-12-22
> **ecschiel said:**
> I'm not sure what u mean with AWN, try to explain me some more and i will try to find a way out =D

AWN is Avant Window Navigator, a dock-like window navigator for GNOME. You can find more info about it on [http://code.google.com/p/avant-window-navigator/](http://code.google.com/p/avant-window-navigator/)

---

### Post by darkskye on 2008-01-17
anyone know the window code to turn swiftweasel transparent, and also file folders (aka home, music)?

---

### Post by dunomous on 2008-02-21
Does anyone know a way to Change this opacity of the panel through the gconf-editor. My CCSM always crashes whenever I try to select anything.

---

