---
title: "GNOME window customizing"
date: 2005-04-12
forum: Desktop Environments
---

### Post by benplaut on 2005-04-12
i have hit a wall ](*,) (good ol' smileys)

In SuSE (with KDE 3.3), i was able to completely customize how program's (namely GIMP) windows worked. I could make a minimal top bar for the main panel and layer panel, and could make it so that it would initially open in desktop 2. I could make it so that the panels would always be on top (initially) of the main drawing windows, and so that they would initially be in the correct place on the screen.

I am very happy with the simplicity of GNOME, and love the way the interface works, but i cannot use GIMP, my main program (other than firefox, of course :grin:), with such horribly placed windows. I am on a laptop, so i don't have much "screen real estate" to play with.

Any nice utilities that i am missing that can fix these behaviors?

I guess, for desktops, I am a Mozilla personality... i am willing to get over the huge file sizes, etc, to get the millions of (GUI) tweaks and settings.

Unless i am missing a transparent elufunt in the room, GNOME does not have this layer of custimization.

Any elufunts? [-o<

---

### Post by c_dog on 2005-04-12
Right-click the Panel and go to Properties and you're got the options to autohide, resize, show hide buttons and change the panel colors or make it transparent. Also you don't really have to have 2 panels. You can put all the necessary stuff on one.

---

### Post by joshmachine on 2005-04-12
This is definitely one of my biggest issues with Gnome as well.  They have made a concious decision to move away from customization in favor of "usability".  

The portion of the windowing system which does what you suggest is called the window manager.  Gnome comes with one that pretty lame, and doesn't have any of the features that you mentioned.  

If you want to risk it, you can try installing a different window manager.  Gnome used to ship with one called Sawfish, but this package is not in main so do so at your own risk. (you can still post your issues here.)  I think Sawfish does have the customization ability of which you speak.

There are others you can play around with. You will have to configure your gnome session to replace Metacity (this is the window manager (wm) that gnome is distributed with.  To do this go to System -> Session  

Select current session tab and change the style from restart to normal then issue the following from command prompt:

$ killall metacity && sawfish

the command prompt will be useful to have there because if you kill metacity and sawfish doesn't start you wont have any wm which means no tabbing around, no changing desktops etc. etc.   If this is the case simply issue 

$ metacity
 
I think you still have gnome panel regardless, but the themeing  will be different.  I have been beaten down by the system so I just suck it up and use metacity.

So far you haven't saved your session so I *think* that upon further log in metacity will be running again.  if you like sawfish, set it to restart in your session then save your session when you log out.

Nothing I've suggested will screw up your system too bad.  Worst case would be that you have no window manager when you log in.  I would save your session with a terminal running so that you can click on it (no tab remember)  and run metacity.

You will also lose much of you quick keys shortcuts.

Good luck.  

Me, i'm just using metacity cause I'm lazy.  I think if the gimp windowing didn't suck so bad maybe you woudn't care so much either ;)

Cheers

---

### Post by Spark* on 2005-04-13
[QUOTE=benplaut]In SuSE (with KDE 3.3), i was able to completely customize how program's (namely GIMP) windows worked. I could make a minimal top bar for the main panel and layer panel[/quote]
Configure Gimp to use Utility windows for the docks and toolbox and use a theme that renders small titlebars for utility windows (like Bluecurve or Clearlooks).

> , and could make it so that it would initially open in desktop 2
You can do that with Devil's Pie, which is an external utility:
[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

> I could make it so that the panels would always be on top (initially) of the main drawing windows
Again, configure Gimp to use Utility window hints and this will just work.

> and so that they would initially be in the correct place on the screen.
Configure Gimp to save windows positions on exit or use the "save window positions now" button.

You can find all those settings under "Window Management" in the Gimp preferences.

So why do the Gimp settings suck so much by default? Because they need/want to support broken window managers. :(

You are right to criticize the desktop environment if something doesn't work for you, however it's important to realize that in most cases the problem can be solved without costly customizability. It is the goal of all people involved in GNOME to make things like this "just work" (unfortunately the Gimp is not a GNOME project...).

---

### Post by benplaut on 2005-04-13
thank you all so much for your advice...

I don't think i will install a different window manager, as it sounds risky and a loss of features (i hardley touch my mouse- i do almost all of my work on the key-commands)...

i will try Spark*'s suggestion... when i get home. I tried it in SuSE with Gimp 2.0, but i still had to do excessive tweaking to get it to work correctly. 

i think i will end up just switching back to KDE... even though it has performance issues (and i kant stand the knaming schemes! ](*,) ).

If there is another desktop environment i should try, let me know... i am still a Newbie at this :-x

<<EDIT>>

I saw, in the apt repositories, "sawfish-gnome", and "icewm-gnome".

From what i have read, both are WMs. In terms of A) Integration into GNOME and B) Features mentioned above, while not looking like win95, which of these WMs would be best? 

Thanks for the help! :grin:

---

