---
title: "[SOLVED] how do i disable emerald?"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by chlorinekid on 2007-10-22
i would like to know how to disable emerald and go back to the default ubuntu 7.10 window manager? i cant see an option to disable it anywhere...

many thanks in advance..

---

### Post by joselin on 2007-10-22
Just uninstall it

sudo apt-get remove emerald

---

### Post by chlorinekid on 2007-10-22
that worked fine, thanks a lot.

just out of curiosity though, how would i have disabled it in order to switch to another window manager? i'd like to switch between window managers now and again without having to uninstall the onei dont want to use in order to activate the remaining one..

---

### Post by chlorinekid on 2007-11-06
anyone able to help?

---

### Post by discmaster on 2007-11-06
system>preferences>sessions. you can disable there without having to uninstall.

---

### Post by chlorinekid on 2007-11-06
that's excellent, thanks a lot pal :)

---

### Post by tak1150 on 2007-11-09
> **discmaster said:**
> system>preferences>sessions. you can disable there without having to uninstall.

I actually don't see an entry for emerald in my "sessions" list. I do see an entry that I made for emerald from way back when I was using Beryl under Feisty. I did a fresh install except for the home partition...

If the session manager doesn't start emerald, what does? Thanks!

---

### Post by jasonmeansfriend on 2007-11-10
> **tak1150 said:**
> I actually don't see an entry for emerald in my "sessions" list. I do see an entry that I made for emerald from way back when I was using Beryl under Feisty. I did a fresh install except for the home partition...

If the session manager doesn't start emerald, what does? Thanks!

you can create a launcher or run from command:

to switch to emerald: "emerald --replace"
to switch to gnome default metacity: "metacity --replace"

(note the space before the "--replace")

---

### Post by tak1150 on 2007-11-11
> **jasonmeansfriend said:**
> you can create a launcher or run from command:

to switch to emerald: "emerald --replace"
to switch to gnome default metacity: "metacity --replace"

(note the space before the "--replace")

Thanks for replying.
I knew of those commands. Sorry for being vague. What I was asking was what starts emerald if it's not the session manager. Also if you do "metacity --replace," you switch to metacity from Compiz Fusion. I would like to keep CF while having the window borders controlled by metacity. Thanks :)

Tak

---

### Post by Sims2789 on 2007-11-15
> **tak1150 said:**
> Thanks for replying.
I knew of those commands. Sorry for being vague. What I was asking was what starts emerald if it's not the session manager. Also if you do "metacity --replace," you switch to metacity from Compiz Fusion. I would like to keep CF while having the window borders controlled by metacity. Thanks :)

Tak

I have the same problem too. I haven't found out how to deactivate Emerald and keep Compiz/Compiz Fusion running so I can use my native window themes.

I shouldn't have to use the terminal to turn off the world's most advanced window manager. So nerdy... this is Ubuntu, not Slackware! It's made for 99% of the population, not for those that want to prevent desktop Linux from spreading or don't know how to spread it!

Thanks to everyone who's trying to help; just remember that most people don't want to uninstall a program just to turn it off, nor do we want to use the command line to do things that we could easily do in the GUI. This is like when I'm given a string of commands and then told to use vi to edit a config file. Since I like using a mouse, I made a launcher on my desktop that launches a root nautilus window, no terminal required.

Better yet, let's not have to edit config files and just use other GUI tools.

I'm very thankful for everything the Compiz/ex-Baryl/ex-ex-Compiz developers have done, and I understand that I'm part of a community, and not talking to some customer support person from M$, but please, for the love of God, couldn't Compiz have put an off button in the GUI? It's downright backward to turn something off by uninstalling it.

---

### Post by Sims2789 on 2007-11-15
Also, why is this labeled "Solved"? Uninstalling Emerald isn't a solution. Similarly, if OpenOffice wouldn't exit, would uninstalling it be a "solution"?

---

### Post by Aquaman420 on 2007-11-16
To stop emerald you could go to the system monitor < processes tab and end Emerald.  And the other will just take over.  Then to start emerald again you could run apllication:  emerald --replace. As a previous poster said notice the space before --replace.  Best of luck

---

### Post by Aquaman420 on 2007-11-16
> Thanks for replying.
I knew of those commands. Sorry for being vague. What I was asking was what starts emerald if it's not the session manager. Also if you do "metacity --replace," you switch to metacity from Compiz Fusion. I would like to keep CF while having the window borders controlled by metacity. Thanks

Tak




In CCSM<Effects<Window Decoration.  In the command box if emerald --replace is in there then that is what starts emerald automatically if you remove it, the system default window manager will start instead.  I hope that is what you mean.  Best of luck.

---

### Post by Forlong on 2007-11-16
> **Sims2789 said:**
> Also, why is this labeled "Solved"? Uninstalling Emerald isn't a solution. Similarly, if OpenOffice wouldn't exit, would uninstalling it be a "solution"?
See [here](http://ubuntuforums.org/showthread.php?t=609082) if you're looking for a proper workaround.

---

### Post by Sims2789 on 2007-11-16
> **Aquaman420 said:**
> To stop emerald you could go to the system monitor < processes tab and end Emerald.  And the other will just take over.  Then to start emerald again you could run apllication:  emerald --replace. As a previous poster said notice the space before --replace.  Best of luck

Thank you, this doesn't work either. It removes my window borders altogether (so I can't close, minimize, etc. windows except from the bottom application bar), even though CompizConfig says they're on (Effects -> Window Decorations is checked). When I turn off Compiz and turn it back on again Emerald's borders re-appear.

I want to disable Emerald and still have my advanced desktop effects.

---

### Post by Sims2789 on 2007-11-16
> **Forlong said:**
> See [here](http://ubuntuforums.org/showthread.php?t=609082) if you're looking for a proper workaround.

This doesn't work either. I added *USE_EMERALD="no"* to *~/.config/compiz/compizmanager/config*. I then disabled and then re-enabled Compiz, but Emerald's still on. I even tried logging out and logging back in again, in case the settings are loaded on login, but that didn't work either. I also tried *USE_EMERALD = false* instead of *USE_EMERALD="no"*.

---

### Post by Forlong on 2007-11-17
> **Sims2789 said:**
> This doesn't work either. I added *USE_EMERALD="no"* to *~/.config/compiz/compizmanager/config*
The proper path is  **~/.config/compiz/compiz-manager** (with *compiz-manager* being the text-file where you have to put the command)

---

### Post by Aquaman420 on 2007-11-17
Apparently you can use the code : gtk-window-decorator --replace&.  I would imagine you could put it in the command box of CCSM<Effects<Window Decoration.  Best of luck.

Edit you can put the code in the command box, you just have to leave out the & at the end,

Courtesy of scottDkoDer on compiz forums

---

### Post by GoaSpy on 2007-11-19
> **Aquaman420 said:**
> Apparently you can use the code : gtk-window-decorator --replace.  I would imagine you could put it in the command box of CCSM<Effects<Window Decoration

     Hi, I've tried the method above and it's not working. The description of that command line sounds like this : "Decorator command line that is executed if no decorator is already running".

I've added two new menu items "Emerald ON" (command 'emerald --replace') and "Emerald OFF" (command 'gtk-window-decorator --replace'). This is working fine, however, the default decorator when I log in is Emerald.
I want gtk-wd default, I guess I could add this as a new session (startup program) but is there an alternative?

Thanks

PS: I'm using Gutsy

---

### Post by Sims2789 on 2007-11-20
Thanks. We need to lobby the Emerald developers to include an "Off" button so that it's easy for everyone to disable it.

---

### Post by tak1150 on 2007-11-21
> **Sims2789 said:**
> Thanks. We need to lobby the Emerald developers to include an "Off" button so that it's easy for everyone to disable it.

Amen.

Do they have a forum somewhere? Thanks.

---

### Post by Forlong on 2007-11-22
This has nothing to do with Emerald per se. It's configured in the compiz-wrapper in Ubuntu. That's why I posted the workaround with *USE_EMERALD="no*" in *~/.config/compiz/compizmanager/config*

---

### Post by shmengie on 2007-11-24
> **Forlong said:**
> This has nothing to do with Emerald per se. It's configured in the compiz-wrapper in Ubuntu. That's why I posted the workaround with *USE_EMERALD="no*" in *~/.config/compiz/compizmanager/config*
works for me. tytyty!!

(for us noobs who are just starting to poke around, stuff like this is a tad daunting. we go, "ooh, emerald...let's check that out. ooh, shiny!" then we go to turn it off and we're like, "oh, i'm such a noob, i can't even turn off visual effects." then, it turns out, it's not actually self-evident. then we go, "yeah, how come there's not a 'disable' button?" more importantly, who would win in a fight: emerald or metacity or comp-fusion? :) see? i have no idea what i'm talking about!)

---

### Post by Forlong on 2007-11-24
> **shmengie said:**
> more importantly, who would win in a fight: emerald or metacity or comp-fusion? :)
Easy one: Compiz would kick all of the above mentioned asses.

Neither Emerald nor Compiz Fusion can run without it.
And Metacity... well, come on, Metacity can't even handle transparency, how could it handle the mighty powers of Compiz?

Other than that: the Hulk.

---

### Post by ben2talk on 2008-02-14
I think there are many unsolved issues here. I, too, am confused. I have GUI access to 'GL Desktop' settings, but the settings here are over ridden by setting elsewhere. Thus if I select to 'maximise' when I double click the titlebar it will still roll up as set elsewhere - but the title is for 'Gnome compiz Preferences', so I would like to know what these settings do, and why some settings don't have any effect while others do! I set the Viewport Windows for the top left corner here, that's fine. Where did I set the Right corner? not here for sure, but I have Viewport Windows for ALL desktops up there, and bottom right corner is expose of desktops... Can't set that here.

The Thread 'How do I disable Emerald is marked as SOLVED. How is it solved? The only way I can disable Emerald is to disable Compiz! Yet compiz is a big reason that ubuntu GUI iis popular,it makes the screen a nice place to live rather than simply a place to go to launch programs, it enables some extremely good user functions (for me, the ability to make my windows fly around by flicking to corners to switch and find open applications is a really big bonus. It's one reason people Love macintosh). These are selling points. This makes the difference between the many cool people who use macintosh, the many Geeky people using linux, and the sheep stuck with Windows. Personally, I'd like to approach the Macintosh camp, but learn how to use my system more effectively - without getting too much of a headache.

Emerald needs it's own settings interface which enables a user to enable it or disable it without the need to install or uninstall it each time.

For me, it will be uninstalled. The 'diable' problem was not solved. Couldn't you label this [ANSWERED], or would this destroy the illusion of a high clearup rate?

Please excuse me, I'm English and love to complain. The fact that I'm here means that I made a choice, and I am extremely happy about what's happening here - and rather excited about the future.

:popcorn:

I'm confident that these issues are being dealt with and I'm prepared to hang in here for the ride. Maybe I can contribute something sometime - however I do hear that KDE (of which I am not fond)  seeks to deal with this kind of issue before it happens. I'd prefer gnome to address it too. Or perhaps I should just try to learn a liittle more a little faster - my first cuup of ubuntu is rather sweet, and not yet half consumed!

---

### Post by emakarov on 2008-03-07
In my case, the file /usr/bin/compiz has the following code:

```

# Use emerald by default if it exist
USE_EMERALD="yes"

...

if [ -x ${COMPIZ_BIN_PATH}emerald ] && [ "$USE_EMERALD" = "yes" ]; then
	verbose "Starting emerald\n"
	${COMPIZ_BIN_PATH}emerald --replace &

```

There is no evidence that it uses any setting from ~/.config/compiz. When I changed the second line to 'USE_EMERALD="no"', emerald was indeed disabled.

Hope this helps.

Evgeny

---

