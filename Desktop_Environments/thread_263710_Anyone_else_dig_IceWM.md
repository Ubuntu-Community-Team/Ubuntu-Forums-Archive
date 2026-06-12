---
title: "Anyone else dig IceWM?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by aysiu on 2006-09-23
I think I may have found a home.

For months, I'd switched back and forth between KDE and Gnome. I dabbled in XFCE, too, but none of them could really satisfy me.

In Gnome, I hated how my choices were:
A) Fading lines whenever I minimized or unminimized applications
B) Wire frames whenever resizing windows
C) "Empty" entries in my Firefox bookmarks

In KDE, I hated how the removable drives and media settings were so complicated.

In XFCE, I hated how it was difficult to edit the applications menu and how the "maximized" windows were never really maximized.

Of course, each of the above had its own strengths, too. But IceWM seems to be where I'll find a home. I've tried Fluxbox and Enlightenment. Those just made no sense to me.

IceWM gives you just enough point-and-click functionality but also some easy-to-understand text configuration files.

For anyone who's interested in exploring IceWM, here are some tips from my last day's exploration:

1. If you launch Nautilus, be sure to launch it without it controlling the desktop (*nautilus --no-desktop*). Otherwise, you won't be able to log out of IceWM without explicitly killing nautilus from the terminal (*killall nautilus*) first.

2. If you use Gnome applications, you may notice they appear *extremely* ugly. IceWM won't automatically inherit the preferred theme you specified in Gnome before. So launch *gnome-theme-manager* and define it again.

3. Themes--there's a package in the repositories called *icewm-themes*. It has tons of themes, about 80 of them. Most are crap, though. If you want good themes, go to [http://themes.freshmeat.net/browse/925/](http://themes.freshmeat.net/browse/925/)

I would highly recommend IceBuntu and IceHybrid.

4. Don't bother with the GUI frontends for configuring IceWM (those are also in the repositories--*iceme*, *icepref*, *iceconf*, etc.). Believe it or not, they're actually more confusing than hand-editing the actual configuration files.

Before you do anything, copy all the files from /etc/X11/icewm to /home/*username*/.icewm
You can modify those config files later, and I think they're pretty self-explanatory (in the Preferences file, 1 means true; 0 means false).

5. Any time you change a configuration file, you can go to the arrow next to Log Out and restart IceWM or you can change a theme, and the settings will take effect.

6. If you want to define keyboard shortcuts for volume controls up and down (and mute--which doesn't *toggle* mute/unmute; it just turns the volume to 0), you should install *aumix* through the repositories. The *keys* config file from /etc/X11/icewm you copied over has the up and down controls defined already.

In the end, it's a lot of fun, and I think I'll stick with it. Of course, I don't have any native IceWM programs (are there any?). I use Rhythmbox for music, Thunderbird for email, Firefox for web, and Thunar for file management.

Anyone know how to shut down from IceWM without logging out first? (And I don't mean *sudo shutdown -h now* from the terminal)

---

### Post by ComplexNumber on 2006-09-23
**aysiu**
i'm sorry, but i'm not in any position to judge. the last time i installed IceWM was when kde 1.0 was current. in those days, i was going through my exploring linux phase. everything was a new concept to me. i was absolutely fascinated because there was nothing like this in windows, and i was only used to windows and other lesser known OS's such as TOS, amiga OS, bbc micro OS, etc. i tried enlightenment, blackbox, windowmaker, gnome(with sawfish/sawmill and enlightment), iceWM, iceWMlite(i can't remember, but there was a lite version of it or something),  a WM that sounded like fwvwm(or something that). things have quite probably changed since then, but i don't think it caught my eye. i liked blackbox most after gnome because of its supreme minimilism that it did extremely well. window maker i found very difficult to get to grips with. enlightment was too overbearing in the amount of eye candy (i felt that it was all eye candy, but not much else). i remember iceWM as being fairly easy to use, but thats all. it seemed to have most things in the right place.
i'm using gnome at the moment, and the way i see things, "if its not broken, it doesn't need fixing". meaning: i'm quite happy with gnome + metacity, so i have no need to try out others.

---

### Post by Rhapsody on 2006-09-23
I've been using KDE as long as I've been using Linux mainly due to a snap decision I made shortly before switching over, but I've found I have very little attachment to it. The only app I'm really attached to that can be fairly closely associated with KDE is Amarok, and the developers of that are starting to de-emphasize that attachment.

Every time the issue comes up, I state my desire to wait until KDE 4 comes along, at which point I'll re-evaluate my options. I'm usually pretty lazy, so I'll probably not make any changes, but I do sometimes get bursts of energy that I put into big things like changing desktop environments...

---

### Post by henriquemaia on 2006-09-23
Other:
I really like IceWM, specially for outdated computers. One of my first choices when I build one.

---

### Post by christhemonkey on 2006-09-23
I used fvwm a while back on my laptop.
And i must say, it worked good and fulfilled all my needs then, unforunately my needs have changed since then, but i still like to use lightweight WM (currently using fluxbox on the laptop)

---

### Post by fuscia on 2006-09-23
yuk! i've never seen so many themes i didn't like, in one place. enjoy it anyway, aysiu.

---

### Post by aysiu on 2006-09-24
> **fuscia said:**
> yuk! i've never seen so many themes i didn't like, in one place. enjoy it anyway, aysiu.
I've got my IceWM looking just fine, thanks.

---

### Post by jason.b.c on 2006-09-24
> **aysiu said:**
> I've got my IceWM looking just fine, thanks.

I dunno , That really dosen't look much differant than regular gnome , I hate to say..

---

### Post by m83 on 2006-09-24
I used IceWM for about 2 years. I think it's the best Window Manager ever. I just love how you can control everything using keyboard shortcuts. When I used IceWM I rarely used the mouse and I was so fast and productive. I also loved that I had a CPU and Network monitor in the taskbar.

Today I use GNOME as I found that I can do in GNOME what I did in IceWM. Of course, IceWM is much better than Metacity, but I found out that GNOME meets my needs.

I still think that IceWM kicks *** and I'll choose it over anything anytime.

---

### Post by fuscia on 2006-09-24
> **aysiu said:**
> I've got my IceWM looking just fine, thanks.

that *does* look good. *goes off to install icewm*

---

### Post by Jason-X on 2006-09-24
> **aysiu said:**
> I've got my IceWM looking just fine, thanks.

Wow! I have never seen ICEWM look that nice. Might have to give it a go.:D

---

### Post by m83 on 2006-09-24
I'm pretty prowd of how my IceWM used to look.

Here:
[http://www.linux360.ro/forum/image-asp1417.html]("http://www.linux360.ro/forum/image-asp1417.html")
[http://www.linux360.ro/forum/image-asp1416.html]("http://www.linux360.ro/forum/image-asp1416.html")

The theme is [IceCrack]("http://themes.freshmeat.net/projects/icecrack/") with some small modifications of my own (mainly I changed the fonts, the colors used for the CPU and network monitors and the clock). If you want my IceWM setup just tell me.

---

### Post by fuscia on 2006-09-24
of course, lipkid can make anything look good...

[[IMG]http://img174.imageshack.us/img174/4568/icewmcd6.th.jpg[/IMG]](http://img174.imageshack.us/my.php?image=icewmcd6.jpg)

---

### Post by %hMa@?b&lt;C on 2006-09-24
how do i install, and remove if necessary?
sudo aptitude install icewm?
then do i just get a choice to use icewm/?

---

### Post by fuscia on 2006-09-24
> **jeffc313 said:**
> how do i install, and remove if necessary?
sudo aptitude install icewm?

sudo apt-get install icewm iceconf iceme icewm-themes(if you want themes)

---

### Post by %hMa@?b&lt;C on 2006-09-24
> **fuscia said:**
> sudo apt-get install icewm iceconf iceme icewm-themes(if you want themes)

got it, but is *really* ugly, how od i do a wallpapaer?

---

### Post by fuscia on 2006-09-24
> **jeffc313 said:**
> got it, but is *really* ugly, how od i do a wallpapaer?

i use feh for wallpapers in wms.

---

### Post by xhaan on 2006-09-24
I used IceWM, I just figured it was another WM :P
Though for a WM I prefer *Step type WMs... I for some reason don't get into WMs that try to look like DEs I guess.

BTW, how did you get it to look so nice? I don't really care about looks when using a WM, just curious.

---

### Post by aysiu on 2006-09-24
> **jeffc313 said:**
> got it, but is *really* ugly, how od i do a wallpapaer? Well, if you use *iceconf* or *icepref*, they have GUI ways of changing preferences, but it's honestly easier to just edit /home/jeff/.icewm/preferences and make sure this line is in there: ```
DesktopBackgroundImage="/home/jeff/pictures/nameofwallpaperyouwant.jpg"

```

> **xhaan said:**
> 
BTW, how did you get it to look so nice? I don't really care about looks when using a WM, just curious. Are you talking to me? Several people have posted screenshots, so I'm not sure. Basically, I used the IceBuntu theme, changed the GTK and icon themes using *gnome-theme-manager*, and got rid of the workspace switcher and a few other things from the toolbar.

---

### Post by liquidtenmillion on 2006-09-24
I used to use icewm on and off, but I don't like it.  There is NO way to get two separate panels in it, which is the way I prefer it.  Also, it is FAR too heavy for what it is.   it's absurd that it takes up 64mb of ram on my PC.

Also, the menu system is far too weak, far too ugly, and it takes way too long to actually execute a program through the menu.

I use either Gnome or Windowmaker as my primary windowmanager.  Windowmaker on very lightweight installations, or gnome on fast PCs.  Windowmaker is just faster, smaller, prettier, and more customizeable than icewm.  Plus the menu system is significantly more customizeable and has more features.

---

### Post by TravisNewman on 2006-09-24
fuscia, that's some messed up wallpaper :)

Wow, IceWM looks so much better than the last time I used it (Solaris 8 at college)

---

### Post by IYY on 2006-09-24
I too love IceWM. It's simple, and yet powerful and fast.

> 1. If you launch Nautilus, be sure to launch it without it controlling the desktop (*nautilus --no-desktop*). Otherwise, you won't be able to log out of IceWM without explicitly killing nautilus from the terminal (*killall nautilus*) first.


Or better yet, use ROX or Thunar. ROX has the advantage of having a desktop, while Thunar has a more traditional look and feel.


> 2. If you use Gnome applications, you may notice they appear *extremely* ugly. IceWM won't automatically inherit the preferred theme you specified in Gnome before. So launch *gnome-theme-manager* and define it again.

You can also add the gnome-settings-daemon to your startup file (an executable script located at ~/.icewm/startup which you can create if it doesn't already exist)

> 3. Themes--there's a package in the repositories called *icewm-themes*. It has tons of themes, about 80 of them. Most are crap, though. If you want good themes, go to [http://themes.freshmeat.net/browse/925/](http://themes.freshmeat.net/browse/925/)

I would highly recommend IceBuntu and IceHybrid.

Thanks, I made these themes. :D 

In addition to your list of cool things about IceWM, there's another very important one: IceWM is very comfortable to use without a mouse. I'm not sure whether these are the defaults of IceWM or just the defaults of icepref, but on my machine the following shortcuts are very helpful:

Windows+Space = turn the task bar into an input box for commands
Windows+1,2,3..= switch to desktop 1,2,3
Windows+left/right = switch to previous/next desktop
Windows = open menu

Alt+F9-F12 = window options, like maximize,minimize,full screen, roll up
Alt+esc = scroll through visible windows

And I also defined Windows+T for a terminal.

Also, I think the tray may not be included in the default Dapper installation, so you need to add **icewmtray &** to the startup file.

I really think there should be an article for all these things in the Wiki, to link newbies with low-resource machines. There should also be better defaults (default theme and options) in the next Ubuntu release so that IceWM is less scary to newcomers.

---

### Post by aysiu on 2006-09-24
> **IYY said:**
> I too love IceWM. It's simple, and yet powerful and fast. I know someone said Window Manager earlier, but I've never been able to make head or tails of Window Manager, Enlightenment, Sawfish, or Fluxbox.

> 
Or better yet, use ROX or Thunar. ROX has the advantage of having a desktop, while Thunar has a more traditional look and feel. Yes, I eventually settled on Thunar. Rox I find hard to adapt to.

> 
You can also add the gnome-settings-daemon to your startup file (an executable script located at ~/.icewm/startup which you can create if it doesn't already exist) Yes, I soon found this out through a Google search. Handy trick.

> 
Thanks, I made these themes. :D  Wow! You did? Thanks for making those. I probably wouldn't be using IceWM without them. There are 80 themes that come with IceWM, but I think they're all ugly.

> 
Windows+Space = turn the task bar into an input box for commands Very handy. I might start using that instead of *grun*.

> Windows = open menu Found that out by accident.

> And I also defined Windows+T for a terminal. *Windows* didn't work for me. The word *Super* did, however. Just a note for others, it's *Ctrl*, not *Control*.

> Also, I think the tray may not be included in the default Dapper installation, so you need to add **icewmtray &** to the startup file. Actually a system tray was included by default when I installed it.

> I really think there should be an article for all these things in the Wiki, to link newbies with low-resource machines. There should also be better defaults (default theme and options) in the next Ubuntu release so that IceWM is less scary to newcomers. When I get more comfortable with IceWM, I'll try to create an easy-to-understand guide.

---

### Post by fuscia on 2006-09-24
> **panickedthumb said:**
> fuscia, that's some messed up wallpaper :)


you're on crack, dude. she's *tres* hot!

---

### Post by Albi on 2006-09-24
Looks really ugly for the most part...
Yeah I know you made it look like the default ubuntu, but I don't see any reason to pick that over Gnome/KDE if your computer can handle it.

---

### Post by aysiu on 2006-09-24
> **Albi said:**
> 
Yeah I know you made it look like the default ubuntu, but I don't see any reason to pick that over Gnome/KDE if your computer can handle it.
Geez, I thought I'd already explained it in my first post: [quote=me earlier]In Gnome, I hated how my choices were:
A) Fading lines whenever I minimized or unminimized applications
B) Wire frames whenever resizing windows
C) "Empty" entries in my Firefox bookmarks

In KDE, I hated how the removable drives and media settings were so complicated.

In XFCE, I hated how it was difficult to edit the applications menu and how the "maximized" windows were never really maximized.[/quote] To top it all off, IceWM *is* faster than all three even though my "computer can handle it."

The load-up time for KDE, XFCE, and Gnome is not that long, but there is load-up time nonetheless. IceWM loads up instantaneously.

And applications load up much more quickly. In KDE and XFCE, an application like Thunderbird loads up in about 5-7 seconds. In Gnome, it takes 10-12 seconds on my computer. IceWM loads it up in 2 seconds.

Well, in any case, it works for me.

I think the real question is--if IceWM does everything I want it to, why do I need to load up a more resource-intensive environment?

---

### Post by fuscia on 2006-09-24
aysiu, have you ever used openbox?

---

### Post by aysiu on 2006-09-24
> **fuscia said:**
> aysiu, have you ever used openbox?
Nope. Is it as easy to configure as IceWM... or is more like Fluxbox, Enlightenment, Sawfish, WindowMaker, etc....?

---

### Post by fuscia on 2006-09-24
> **aysiu said:**
> Nope. Is it as easy to configure as IceWM... or is more like Fluxbox, Enlightenment, Sawfish, WindowMaker, etc....?

it's pretty simple, though there may be some configurations i've never messed with that may, or may not be a pain in the assterisks. openbox, openbox-themes, obconf...i use pypanel with it, and obmenu is drunken child easy to use (once it's installed, that is). there're a couple of howto threads laying around, by raublekick and stormy eyes, that are pretty helpful. openbox is minimal. i also found making my own themes for it to be fairly easy. the first time i logged into it, i was puzzled by the blank screen. i thought it was broken until i tried the right-click by accident. scrollable workspaces too.

---

### Post by aysiu on 2006-09-25
I think I'll stick with IceWM for a while. If I get restless or "master" IceWM, I might try out OpenBox.

---

### Post by roderikk on 2006-09-25
> **aysiu said:**
>  When I get more comfortable with IceWM, I'll try to create an easy-to-understand guide.

Looking forward to that one! Could you post here if you do? I've just installed ubuntu on an old laptop and used XFCE and already think that is quite 'snappy' compared to Gnome on the same laptop. Would love to try IceWM if I've got some more time on my hands!

---

### Post by DJiNN on 2006-09-25
> **aysiu said:**
> I've got my IceWM looking just fine, thanks.

Hey, that looks VERY good!! I've played around with Ice a bit, and have to agree that most of the default themes are OK, but not that great. But after seeing that i think i'll give it a try.

You said that you tried Fluxbox & it was difficult? Howso? I have only been using Fluxbox for a few weeks now, but i find it really easy (Although it was hard when i first tried, but mainly due to my unfamiliarity more than anything else)..... maybe once you have played with Ice a while you might find Flux a bit easier? 

Anyway, i think i shall also be trying Ice in the next week or so..... just to see how it compares to Flux. Going to try OpenBox as well. 

But one thing i know is that i won't be going back to Gnome or KDE or XFCE in a hurry. Why waste ANY CPU on all that when the Lightweight DM's have all the functionality (Once you have them set up correctly) and none of the bloat! :)

I've just done a server install of Ubuntu & installed Flux..... It's fantastic, so i know how you must feel with Ice. Nice one! :)

---

### Post by Onyros on 2006-09-25
aysiu, in terms of file management, I find PCManFM superior to Thunar, especially due to one key feature: tabs! And you can even drag'n'drop files by placing them over the tabs.

There's a new beta out with desktop icons and all (even though its implementation of a desktop is really flawed right now), but as a file manager it's pretty good.

I must admit I like IceWM, but my favourite (other than GNOME) is Fluxbox, the configuration is really easy once one gets the hang of it.

---

### Post by PatrickMay16 on 2006-09-25
I find IceWM very useful for slower machines with low memory. It looks pretty good and is very usable, while being resource effective. But on fast machines with large amounts of memory, I just use GNOME.

---

### Post by aysiu on 2006-09-25
> **roderikk said:**
> Looking forward to that one! Could you post here if you do? I'll post a link.

> **DJiNN said:**
> You said that you tried Fluxbox & it was difficult? Howso? I seem to remember just not being able to find options for configuring things. There was a right-click menu and that was about it. > maybe once you have played with Ice a while you might find Flux a bit easier?  That's very possible. I don't want to rush things, though.

> But one thing i know is that i won't be going back to Gnome or KDE or XFCE in a hurry. Why waste ANY CPU on all that when the Lightweight DM's have all the functionality (Once you have them set up correctly) and none of the bloat! :) Yes, the good thing is that I can run all the programs I usually run and *gnome-settings-daemon* and still have it be lots faster.

> **Onyros said:**
> aysiu, in terms of file management, I find PCManFM superior to Thunar, especially due to one key feature: tabs! And you can even drag'n'drop files by placing them over the tabs.

There's a new beta out with desktop icons and all (even though its implementation of a desktop is really flawed right now), but as a file manager it's pretty good. I'll keep that in mind. When it gets in the repositories, I'll be sure to give it a try.

---

### Post by lapsey on 2006-09-25
iceWm is great but i think it really has room for improvement in the panel + menu. Especailly as regards multiple panels.
and  I'm sure it wouldn't be too hard to allow for theming the panel item borders (or menu a bit more extensively)

---

### Post by aysiu on 2006-09-25
I agree with lapsey on IceWM's shortcomings, but those are, fortunately, non-issues for me. 

The borders are fine for me (not ideal, but not bothersome either) and a welcome tradeoff for other window behavior I like. And I have no use for multiple panels. I do almost everything through keyboard shortcuts, anyway.

By the way, I tried OpenBox and Fluxbox. I'm going to have to say that while I've seen people do some beautiful things with both window managers, they just didn't seem intuitive or appealing to me--not worth the effort to understand. I probably could have done an hour or so of research and eventually felt comfortable with either one, but if IceWM does what I want, I don't see the point.

OpenBox gave me a completely black screen with a context menu. Switching themes was easy, but one of the configuration options referred to a non-existent dock. When I installed one (the py... something), it was also totally black with only the focused application appearing. I couldn't see the configuration files in any obvious place (~/.openbox, for example). So I gave up.

Fluxbox *appeared* to give me a bit more at first. It had a visible toolbar with a lot more context menu items, but most of those items didn't make any sense to me, and I couldn't find a way to launch a terminal or any other application, for that matter. Eventually, I did Control-Alt-F1 and found the config files in ~/.fluxbox, but they didn't make any sense to me.

Bottom line: I could probably make the effort to understand Fluxbox or Openbox, but I don't see the benefit. IceWM came rather naturally to me, and it works just fine for me. I do appreciate the recommendations, though.

---

### Post by croak77 on 2006-09-25
> **aysiu said:**
> I

OpenBox gave me a completely black screen with a context menu. Switching themes was easy, but one of the configuration options referred to a non-existent dock. When I installed one (the py... something), it was also totally black with only the focused application appearing. I couldn't see the configuration files in any obvious place (~/.openbox, for example). So I gave up.

Fluxbox *appeared* to give me a bit more at first. It had a visible toolbar with a lot more context menu items, but most of those items didn't make any sense to me, and I couldn't find a way to launch a terminal or any other application, for that matter. Eventually, I did Control-Alt-F1 and found the config files in ~/.fluxbox, but they didn't make any sense to me.


Openbox uses freedesktop standards so the config files are in ~/.config/openbox/menu.xml and ~/.config/openbox/rc.xml. The default configs are in /etc/xdg/openbox/. You can just copy them over. The 'dock' it's referring to is for dock apps like used in WindowMaker. Pypanel is a seperate app. I believe to config file is ~/.pypanelrc, The defalut one is /etc/pypanelrc. 

For fluxbox, it usually come with a menu that doesn't match your setup. If you open a terminal you can run fluxbox-generate-menu to automagically scan and add items to your menu. You can install fluxconf which contains a few GUI's, fluxmenu, fluxconf, fluxkeys, to easily edit your menu, fluxbox config and key bindings.

---

### Post by skymt on 2006-09-25
> **aysiu said:**
> OpenBox gave me a completely black screen with a context menu. Switching themes was easy, but one of the configuration options referred to a non-existent dock.

The Openbox "dock" is the same as the Fluxbox "slit". They're both a place to put Window Maker-style [dockapps](http://dockapps.org/). For example, at one point, I was running Fluxbox with Gkrellm, fbpager, and several dockapps, all in one autohiding thing-a-ma-bob. It's pretty convenient to have everything in one place.

---

### Post by DJiNN on 2006-09-25
> **aysiu said:**
> 
Bottom line: I could probably make the effort to understand Fluxbox or Openbox, but I don't see the benefit. IceWM came rather naturally to me, and it works just fine for me. I do appreciate the recommendations, though.

That makes sense..... it's what you want from a particular environment that counts after all.  I like Fluxbox because it gives me a lot of flexibility & i've only just started to learn about it.  But it does take a little bit of setting up..... not long, but long enough. Whereas Ice just works from the getgo, which is really kool.

I've also just been trying Window Maker, and that looks REALLY GOOD! Very configurable but without all the "Config Files" etc......  So my faves at the moment are WM & Flux...... but i've yet to spend any real time in IceWM..... Got that to come. :)

Aren't we lucky to have so much choice? :)

---

### Post by aysiu on 2006-09-25
> **DJiNN said:**
> 
Aren't we lucky to have so much choice? :) Yes!

---

### Post by kerry_s on 2006-09-25
I prefer fluxbox or openbox(currently using ob). I just don't like icewm, it's just not the feel i want.

---

### Post by lapsey on 2006-09-25
i don't know why people say IceWM is memory intensive (did someone say 64MB?): it's not even taking up 2MB here. And that's with the IceBuntu theme and other bells n whistles.

---

### Post by fuscia on 2006-09-25
i never did figure out the dock in openbox or fluxbox, but i'm not much of a dock person to begin with.

---

### Post by nalmeth on 2006-09-25
I remember toying with IceWM once, with a few beers... Played with some  themes, but I don't think I got mcuh further. Beer doesn't help much when you're trying to concentrate. :???:
All in all, it was neat, customizable, and fast. Not terribly slick looking though. 

BTW, whats with the avatar fucsia? It's all fuzzy

---

### Post by fuscia on 2006-09-25
> **nalmeth said:**
> BTW, whats with the avatar fucsia? It's all fuzzy

i'm wearing a veil.

---

### Post by aysiu on 2006-09-26
Okay.

I created a script that sets up IceWM in a nice Ubuntu-Gnome-friendly way, using IceBuntu and a few other minor customizations to preferences.

Only trouble is I don't have a default Ubuntu to test it on.

Anyone willing to test it for me? It's a simple shell script, really. I would say if you know simple terminal commands (*aptitude*, *cd*, *mv*), you can examine the script yourself and see there's nothing to be afraid of (and very little to fix, should something go "wrong").

Please let me know if the results turn out okay or not, and at what point things went wrong if they do.

Do not give me abstract suggestions for improvement to the script ("You might want to include a question asking the user if she wants to proceed with ________"). I am not a programmer. Unless you have actual lines of code to give me ("Insert this line between the second and third lines"), I can't really take suggestions.

**Edit**: This script has moved to [post #58.](http://ubuntuforums.org/showthread.php?p=1549508#post1549508)

---

### Post by IYY on 2006-09-26
I will test it on a LiveCD when I get some time, but I would suggest adding icons for menus (like accessories, games, office). There are some sample Tango icons in the IceBuntu theme, but the next version will have nicer icons based on the new Gnome theme.

---

### Post by aysiu on 2006-09-26
I tried testing it on the live CD, and it wouldn't work. IceWM would install just fine, but when I logged out and logged back in again, I think the files I added to the ~/.icewm got reset somehow.

I will definitely consider adding icons.

---

### Post by Peter76 on 2006-09-26
Hey Aysiu, did you check my Icewm+Rox howto here : 

[http://www.ubuntuforums.org/showthread.php?t=171203](http://www.ubuntuforums.org/showthread.php?t=171203)

If you got some additions to it, post them please... I was wondering why no more people were using Icewm... It's so neat!!!

---

### Post by aysiu on 2006-09-26
Thanks for that HowTo, Peter76. It looks ideal for older systems, and I'll definitely keep it handy for reference.

I think, since I have a more modern system, I basically favor Thunar over Rox and still use all my typical Gnome applications (Thunderbird, Firefox, Gnome Terminal, etc.)... so my installation script is targeted at a different audience.

---

### Post by user1397 on 2006-09-26
i dont know if this has been answered already in this thread, but how exactly do you install a theme in icewm?  (i mean one from the link aysiu has on the first page of this thread, and yes i have looked in the wiki)

---

### Post by IYY on 2006-09-26
Extract it to ~/.icewm/themes

---

### Post by aysiu on 2006-09-26
I believe you extract the .tar.gz to /usr/share/icewm/themes

---

### Post by IYY on 2006-09-26
That works too, but requires sudo.

---

### Post by Albi on 2006-09-26
How much lighter is this than XFCE?

---

### Post by aysiu on 2006-09-26
Lighter, but since XFCE is pretty light to begin with, you probably won't see vast improvements.

---

### Post by aysiu on 2006-09-27
Okay. It took me a while (because my old machine is slow and can't handle the Desktop CD, and the Alternate CD took over an hour to fully install), but I did test out the script.

I had to make a few revisions to actually have it work, but it did work eventually, and this is the working script.

It uses IceBuntu--the IceWM theme that looks like the default Gnome setup in Ubuntu. It uses Thunar as a file manager. And it shows Evolution and Firefox on the panel and most of the default Gnome applications in the menus.

On my 766 MHz, 128 MB RAM machine, it's quite responsive, even running Gnome Terminal and Firefox.

Anyone's welcome to modify the startup script if you have any programming chops (I don't have any, as you may have noticed).

**Warning**: The script assumes you have Ubuntu installed already (not Kubuntu or Xubuntu) and that you have a working internet connection.

More specifically, this is what the script does:
1. Backs up your sources.list
2. Puts in a temporary sources.list
3. Installs IceWM, Thunar, and a few other programs related to getting IceWM working.
4. Restores your original sources.list
5. Installs the IceBuntu theme
6. Sets you up with some sensible defaults for configuration files and makes them the default configuration files while also backing up the original defaults

---

### Post by IYY on 2006-10-02
Question for all IceBuntu users: a user has recently made a modification to this theme that makes the borders thinner (screenshot attached). I personally like the new look better and will add this to the archive, but do you think the old "fat border" look is even needed anymore?

---

### Post by oss_monkey on 2006-10-07
> **IYY said:**
> Question for all IceBuntu users: a user has recently made a modification to this theme that makes the borders thinner (screenshot attached). I personally like the new look better and will add this to the archive, but do you think the old "fat border" look is even needed anymore?

Hmm... I think I like it. Where can I get it? Also, is it possible to make the title bar of applications smaller? I'm only on 1024x768, so I'd want as much working real estate as I can have. :)

Oh yeah, and the font sizes too. Where can I change that? (like in Firefox's Bookmarks Toolbar)

---

### Post by Chimes on 2006-10-07
The only reason I even have a window manager is to have multiple consoles viewable in the same window at once...

so IceWM works just fine.

By the way, mocp rocks. Do you know how fun it is to just Alt+ctrl+F1, logon, and use mocp to turn my computer into a jukebox? it's fun -- and it impresses the hell out of people... they're like "wow, how can you do that?" and I'm like "it's a little thing called linux." and then they're like "oh man, that's so cool! And you are, by association, cool!" and I'm like "you got it, dawg!" and then we perform the dap handshake.

The dap handshake part would make a lot more sense if I was african, but it was not until last tuesday that I realized that I use it because my use of ubuntu has enabled me to get in touch with my non-existant african roots. Simply because of Ubunutu's cool slogan, (which, for the non-super-enlightened among us, means "humanity"), I have come in touch with my african brothers in the Congo who don't own a computer and live under constant violence.

 This human-link has enabled me to perform the dap with utmost accuracy, and now I thank god that I am part of ubuntu, otherwise I would not be part of the 'cool' crowd which clearly has a connection with all of humanity, unlike those darn debian people, who aren't part of humanity at all. Those debian people are probably more like gophers or like... cranky chipmunks or something than real humans.

Anyway, after I am done with my neat-o handshake, I start selling my book "How to install Ubuntu in 100 days" and usually I make money from it because they pay me to stop yelling at them to buy my book. I'm like "BUY IT! BUY IT! YOU ARE NOT MORE LIKE A GOPHER OR CHIPMUNK, ARE YOU? ARE YOU???" and then I tell them, calmly and rationally while dousing my arms with gravy that if they pay me money I'll leave them alone.

So wait... where was I going with this? :-k 

Oh yeah, yeah. IceWM is cool. I can dig it. Oh yeah. I'm cool.

---

### Post by IYY on 2006-10-07
> By the way, mocp rocks. Do you know how fun it is to just Alt+ctrl+F1, logon, and use mocp to turn my computer into a jukebox? it's fun -- and it impresses the hell out of people... they're like "wow, how can you do that?" and I'm like "it's a little thing called linux." and then they're like "oh man, that's so cool! And you are, by association, cool!" and I'm like "you got it, dawg!" and then we perform the dap handshake.

I installed it and it's a very cool program indeed. Can't believe I never heard about it before.

> Hmm... I think I like it. Where can I get it? Also, is it possible to make the title bar of applications smaller? I'm only on 1024x768, so I'd want as much working real estate as I can have.

The official Freshmeat page (first hit on google for 'IceBuntu') already includes this theme in the archive. Changing the size of the titlebar might be a bit tricky, unless I can think of some clever ImageMagick script to do it.

> 
Oh yeah, and the font sizes too. Where can I change that? (like in Firefox's Bookmarks Toolbar)

If you are running gnome-settings-daemon in your startup like suggested in this thread, you can just run gnome-font-properties and select your font.

---

### Post by picpak on 2006-10-07
The fact that IceWM can do so much with so little is amazing.

Ctrl-Alt-Space is awesome!

---

### Post by liquidtenmillion on 2006-10-07
It's equal in size tofvwm and Windowmaker but does much less than either of those.

---

### Post by ghostshadow189 on 2006-10-07
hi all ,
i installed icewm with "sudo apt-get install icewm iceconf iceme" . after that , i loged out and choosed icewm session . but unfornately , it didnt display anything , like toolbar , start menu , etc . it just displayed a blue desktop . i also tried ctrl+alt+esc and i saw window list , so that mean maybe i installed icewm successfully , but still there're some mistake ? i tried right click , left click everywhere on screen but there nothing happned .
thanx for ur helps !

---

### Post by aysiu on 2006-10-11
ghostshadow189, have you tried creating a test user to see if it might be a problem specific to your login?

---

### Post by oss_monkey on 2006-10-11
Does anyone know how to order the items on the taskbar? When I alternated between hand-editing the configuration files and using iceme/icepref, the pager switched from right to left, and the little handle moved from 3rd from the right, to the rightmost. :s Mind-boggling.

Btw, thanks for recommending this, aysiu. You rock.

---

### Post by aysiu on 2006-10-11
You can order the *applications* on the taskbar, but I don't think you can order the other items.

Has anyone else been able to do this?

---

### Post by pastored on 2006-10-14
> **oss_monkey said:**
> Also, is it possible to make the title bar of applications smaller? I'm only on 1024x768, so I'd want as much working real estate as I can have. :)

Oh yeah, and the font sizes too. Where can I change that? (like in Firefox's Bookmarks Toolbar)

Hi there - Where you REALLY want to look to change title bar sizes is in the default.theme file of whatever theme you're using.

For example, I'm using Smoothy-Feelings theme, and in the /usr/share/icewm/themes/Smoothy-Feelings directory, you'll see a "default.theme" file. That contains all the specific instructions on how that particular theme changes the appearance of Icewm.

You're looking for the line:
```
TitleBarHeight=19
```

Change it to whatever value you prefer. The number you use is the number of pixels high you want your title bar. Want a t itle bar that is 1 pixel high which forces you to use Alt+F4 to close the app? THAT's where you change it. 

NOTE: this value will also work in your ~/.icewm/preferences file.

Hope that helps,

---

### Post by aysiu on 2006-10-14
pastored can correct me if I'm wrong, but I think the themes' preferences (/usr/share/icewm/themes/themename/default.theme) will override your personal preferences (/home/username/.icewm/preferences).

---

### Post by pastored on 2006-10-14
> **aysiu said:**
> Anyone know how to shut down from IceWM without logging out first? (And I don't mean *sudo shutdown -h now* from the terminal)

The answer is very close to you! 

There are a couple of ways of doing this, one is in your ~/.icewm/preferences file, and one would be in your ~/.icewm/menu or ~/.icewm/toolbar files.

There is a setting in the preferences file for the Shutdown command:
```
#  Command to shutdown the system
ShutdownCommand=""
```

Just type in your "sudo shutdown -h now" command in between the quotes, and restart icewm. You'll see that you now have a Shutdown option in your Logout submenu. This is the "safe" way of shutting down, because the submenu forces you to think a moment before you shut your computer down.

The OTHER way is to create a menu entry / button in your menu (or toolbar). Same code, just different file in which to put it.

```
prog "I'm OUTTA here" /usr/share/pixmaps/quit.png "sudo shutdown -h now"
```

If you want it in your menu, put it in the ~/.icewm/menu file. If you want it on your toolbar, use the ~/.icewm/toolbar file.

Hope that helps!

---

### Post by picpak on 2006-10-14
Odd thing is, if the submenu has a line before the arrow, you have to click the submenu to the right of the line, or it won't work.

I wish there were a way to change this.

---

### Post by aysiu on 2006-10-14
pastored, thanks for the tip.

---

### Post by oss_monkey on 2006-10-22
> **picpak said:**
> Odd thing is, if the submenu has a line before the arrow, you have to click the submenu to the right of the line, or it won't work.

I wish there were a way to change this.

Well, what I do is just let the cursor stay on the menu item, then in about a second, the submenu appears. :)

---

### Post by oss_monkey on 2006-10-22
Wallpaper help!

I've been using IceWM a couple of weeks now, but I still couldn't make heads nor tails of wallpaper. I know that some others use feh to set the wallpaper, but I can't figure out why my laptop's acting this way.

When I log into Ubuntu, I see the wallpaper but it is replaced by a plain gray background. If I reload the theme (IceBuntuThinBorder), then the wallpaper returns.

I took a look into the relevant config files and found these.

[COLOR="DarkOrange"]preferences[/COLOR] file:
DesktopBackgroundImage=/correct/path/to/image.jpg

[COLOR="DarkOrange"]startup[/COLOR] file:
gnome-settings-daemon

Any idea what's wrong?

---

### Post by IYY on 2006-10-22
I just use ROX to set the wallpaper, because it also gives me desktop icons.

---

### Post by Campitor on 2006-10-29
I have been using IceWM for about six months now, and I love it.  It runs smoothly on my 233Mhz 80MB ram machine.  All is really nice, I added adesklets and it looks great.  I only have one problem...when I run Opera, or xdvi, or xpdf; everytime the mouse pointer changes to a hand or magnifying glass, it will remain on the screen. That is, I have two mouse-pointers, one which is active and changes back to the arrow, and another that just sits there on the desktop, in the last position it was used within any of the before mentioned applications.  Even if I restart Icewm, the pointer will remain there.  It only goes away if I logout and login again. I figured this is a low-memory hang up, or an xorg thing.  Does anybody know how I can mannually restart the mouse-pointer, or refresh the screen in a very hard way?

  other than that, I love Ice...in my old laptop it takes 4 seconds to boot up.  And LyX takes 10 seconds to boot.

Camp.

---

### Post by picpak on 2006-10-29
> **oss_monkey said:**
> Well, what I do is just let the cursor stay on the menu item, then in about a second, the submenu appears. :)

Thanks, but I found an even better solution:

```
MenuMouseTracking=1
MenuActivateDelay=225
SubmenuMenuActivateDelay=225
```

The menus open automatically. That's a lot less clicking!

As for your background image problem...after changing your background, run

```
icewmbg
```

for the changes to take effect.

---

### Post by shining on 2006-10-29
> **aysiu said:**
> I think I may have found a home.

For months, I'd switched back and forth between KDE and Gnome. I dabbled in XFCE, too, but none of them could really satisfy me.
...


Did you have a look at fvwm?
A few links:
[http://www.fvwm.org/](http://www.fvwm.org/)
[http://www.zensites.net/fvwm/guide/](http://www.zensites.net/fvwm/guide/)
[http://fvwm.lair.be/](http://fvwm.lair.be/)

---

### Post by aysiu on 2006-10-29
> **shining said:**
> Did you have a look at fvwm?
A few links:
[http://www.fvwm.org/](http://www.fvwm.org/)
[http://www.zensites.net/fvwm/guide/](http://www.zensites.net/fvwm/guide/)
[http://fvwm.lair.be/](http://fvwm.lair.be/)
I've dabbled in every window manager in the repositories, so, yes.

IceWM is the only one that suits my sensibilities right now. Thanks for the suggestion, though.

---

### Post by BLTicklemonster on 2006-11-21
> **IYY said:**
> I just use ROX to set the wallpaper, because it also gives me desktop icons.

I have to admit that one of the most frustrating things about linux so far is how everyone has a different way of doing things. I just spent God knows how long trying to get rox to be there when I want it to be there. First of all, ./rox does not open anything. Secondly, when I tried to set ... hell, I forget what it was now, anyway, something asked me for my password, and by God, it said I had it wrong. So I opened a terminal, and typed sudo apt-get update, and typed in the same password rox said was wrong, and voila, update.

I just want some normalcy in icewm, is all. I'd like to add some launch thingies to my whatever it is sitting at the bottom of the desktop. (taskbar, I guess) yes, there's a place for that in /etc/X11/icewm/iforgetwhichone, but it was there. but to test whether that would make a difference, I #ed out Vlm, restarted icewm, and Vlm was still there. So I decided that was not the place to make such changes. I'd also like the ability to put icons on my desktop if I so desire. I don't like icons there (actually, the ability to drag something there for future consideration is a desire, too) but it's a nice place to park things. 

yeah, I'm real frustrated. Seems like each new adventure has some whacky differences that just don't make things easier. Get this, on the ROX site, it says to run ROX-Session, and it worked. Short time later, I try, and no such thing. WTF? OMG I just deleted rox! No, it's still there. Hmmm. 

So if anyone would like to ease me along into some usability with icewm, I'd be more than appreciative. In the meantime, I'll be back here cutting paper dolls in my padded cell with the Ubuntu stickers (huh, Firefox says ubuntu isn't spelled right.) on the walls.

Thanks for turning me on to rox, it looks like it will be what I was looking for, I just have an unreal expectation that stuff is going to work intuitively for some insane reason, and sure as heck, EVERYTHING you try in Linux works differently than everything else.

Rant over. sorry.

---

### Post by IYY on 2006-11-21
Rox is nice and simple to install, but it has some disadvantages:

[LIST]
[*]The desktop is not really a desktop but a 'pinboard'. So, it's for shortcuts, not files.
[*]The file manager is good, but not as good as Nautilus or (the lighter) Thunar.
[/LIST]

But to answer your question...

To get Rox, 

```
sudo apt-get install rox-filer
```

To launch a file manager,

```
rox

```
To make Rox draw a desktop in IceWM,

```
echo "rox -p=main &" >> ~/.icewm/startup
chmod +x ~/.icewm/startup
```

At this point you can drag icons to the desktop.

---

### Post by BLTicklemonster on 2006-11-21
I already had a wallpaper showing up, and added some stuff to the program list thing at the bottom left. I got rox running okay before I posted, and finally got it where I could see the items showing what all it does, but it was so foreign to me. Really frustrating. That command you list there at the end, what does it do? I ran it and nothing really happened different than I already had.

---

### Post by IYY on 2006-11-21
The last command just adds the rox desktop to the IceWM startup, so that you don't have to launch it every time. If it was already there, you should remove the duplicate.

---

### Post by burek on 2006-11-25
iceconf dont work

[http://ubuntuforums.org/showthread.php?t=306604&highlight=iceconf](http://ubuntuforums.org/showthread.php?t=306604&highlight=iceconf)


Please aysiu could you look at this ? 

how to fix it ?

i am runing edgy 

thank yolu

---

### Post by IYY on 2006-11-25
Try icepref instead.

---

### Post by burek on 2006-11-25
> **IYY said:**
> Try icepref instead.

I tried and it didnt work too: fonts gone.
  
I installed icewmcc sthg from freshmeat and it worked with fonts
but it kept repeating that .icewm/keys ... are necessary

I dont know how to configure it.
I just want workspace wrap and alt right mouse for resize 

thnak wou

---

### Post by IYY on 2006-11-27
On an unrelated topic, here is a short article I wrote on IceWM (includes instructions on installing IceWM, Rox and themes):

[http://digg.com/linux_unix/Why_use_IceWM_and_how_to_use_it](http://digg.com/linux_unix/Why_use_IceWM_and_how_to_use_it)

---

### Post by BLTicklemonster on 2006-11-27
Two things I have found out.

[Rox-filer rocks](http://ubuntuforums.org/showthread.php?t=171203), and [IcwWM Theme Designer](http://linux.softpedia.com/get/Desktop-Environment/Themes/IceWM-Theme-Designer-080.shtml) is excellent to have around, too.

:)

the attachment, though not anything to write home to Linus about, is light years ahead of where I was a day or two ago.

---

### Post by BLTicklemonster on 2006-11-29
I've got a little problem all of a sudden now. My clock at wants to blink, which for some reason makes it move left and right inside a space smaller than it is alloted, therefore I see either h/m/s, or /m/s because it keeps moving around.

Any idea how to correct this anomoly?

---

### Post by burek on 2006-11-29
> **BLTicklemonster said:**
> Two things I have found out.

[Rox-filer rocks](http://ubuntuforums.org/showthread.php?t=171203), and [IcwWM Theme Designer](http://linux.softpedia.com/get/Desktop-Environment/Themes/IceWM-Theme-Designer-080.shtml) is excellent to have around, too.

:)

the attachment, though not anything to write home to Linus about, is light years ahead of where I was a day or two ago.

When the Edgy doenst bug with it yeah ... Icewn can be excellent... :( :(

---

### Post by BLTicklemonster on 2006-11-29
Indeed, my dapper runs icewm better than edgy does.

---

### Post by BLTicklemonster on 2006-11-30
Aysiu, have you tried fluxbox yet?

---

### Post by aysiu on 2006-11-30
> **BLTicklemonster said:**
> Aysiu, have you tried fluxbox yet?
Yeah, but I just find it too much work to set up.

---

### Post by BLTicklemonster on 2006-11-30
Just add kfce4-panel & to the startup file (/home/you/.icewm/startup) at the end, and then in the init file, change

session.screen0.toolbar.visible:	true 
to
session.screen0.toolbar.visible:	false

and reboot.

It's pretty danged quick, let me tell you. Though iceWM can do more with the themes.

---

### Post by d3v1ant_0n3 on 2006-11-30
I've been having a play with IceWm recently. I like the speed! Just need to get to grips with theming it.

---

### Post by hanzomon4 on 2006-12-01
This is great, I always wanted to have a DE that uses rox and this is the smoothes. Much better then trying to use rox-filer in gnome. But yeah beryl and this my new favorites... who knew

---

### Post by BLTicklemonster on 2006-12-01
!!! seems to work quite well in feisty, too. I haven't seen any problems yet at all.

---

### Post by fuscia on 2006-12-12
> **fuscia said:**
> yuk! i've never seen so many themes i didn't like, in one place. enjoy it anyway, aysiu.

wrong again (at least, in my view)...

---

### Post by Peter76 on 2006-12-12
Fuscia, what mediaplayer is that in your screenshot; or what theme?

Thanks, Peter

---

### Post by BLTicklemonster on 2006-12-12
I like icewm, it's real quick and all, but it got me looking around, and I actually like fluxbox better now. Sure, the themes/styles aren't as pretty, but if you set it to run with rox or xfce4-panel, it really is a lot nicer. I've played around with others, too, like enlightenment, blackbox, and a few more, but I keep coming back to either icewm or fluxbox. There's a fluxbuntu coming out (there's a cd iso download already, alpha test) soon, so I was naturally wondering... will there be an icebuntu?

*edit:

duh, googled it. sorry.


*nudder edit:

duh, that's a theme. lmao.

---

### Post by dbbolton on 2006-12-12
dig it i do

---

### Post by rrwo on 2006-12-12
It ran really fast on a five-year-old machine I was using, and I would have switched to it, had it worked.  It didn't, and I didn't have the time to figure out how to fix it.  So I went back to using Xfce.

---

### Post by mcduck on 2006-12-12
Well, it's very lightweight. Kind of ugly, altough I've seen some ok looking screenshots. That's all. If I needed a lightweight desktop I'd probably use fluxbox or ion instead..

---

### Post by drokmed on 2006-12-13
Excellent thread.  Glad to see icewm still has a strong following.  I can't believe only one distribution uses icewm by default (DeliLinux).

Every time I build a server, I always put icewm on it.  I force the server to boot to text mode, but if the operator needs a gui, icewm is there.  I try to keep server memory utilizations to a minimum, and icewm is perfect for this.

As for desktops, I have gnome on my laptop and kde on my desktop.  I also have a test server that runs icewm.

I feel funny running firefox on icewm, since firefox takes like 10 times the RAM vs icewm, but dillo just doesn't render sites well enough.

I wish ubuntu would build an icewm package containing the latest code, and be nicely configured by default.  Until then, we'll continue to tweak it w/ tips from threads like this one!

---

### Post by aysiu on 2006-12-13
Puppy Linux also uses IceWM.

---

### Post by K.Mandla on 2006-12-13
Perhaps this has been mentioned, but if anyone watches the xubuntu-devel mailing list, there has been an invitation by the admin of [lookxp]("http://lxp.sourceforge.net/") to have that project bundled along with a modified icewm as part of the Xubuntu default.

Jani seems interested, if it's properly managed ...

[quote=Jani Monoses]So I am open to such an addition to the xubuntu CD, but somebody with at least universe upload rights needs to be in charge of it and have a step by step plan written up first, just like the other feature specs in launchpad. Then it can be discussed on this list and development can proceed after the parties involved reach an agreement on the feisty goal and everyone's role in the process.[/quote]
Personally, I'd love to see an IceWM variant installable by default. One that defaulted to an XP look would be ... okay, so long as that's adjustable. Which I am certain it would be.

Anyway, if you're an IceWM fan, it might be worth looking in to, to see if you can help out. :-k

---

### Post by roachk71 on 2006-12-13
Honestly, there are still situations in which XFCE isn't light or fast enough, such as very old hardware a friend or associate would like resurrected.

I still like IceWM; I simply don't use it now.

---

### Post by SunnyRabbiera on 2006-12-13
IceWM is alright, I am more of a windowmaker fan though (but it is a bit of a pain)

---

### Post by mikerduffy on 2006-12-13
> **K.Mandla said:**
> Perhaps this has been mentioned, but if anyone watches the xubuntu-devel mailing list, there has been an invitation by the admin of [lookxp]("http://lxp.sourceforge.net/") to have that project bundled along with a modified icewm as part of the Xubuntu default.

[***This screenshot***]("http://lxp.sourceforge.net/TBar_details_1024.jpg") caught my eye.  Is a language-switching feature available on other desktops?

---

### Post by troymcdavis on 2006-12-13
I didn't consider it until I saw this thread (and voted it in).

Consider my vote changed, I've been converted. The speed rocks, and I'm excited about the theme customization.

---

### Post by AgenT on 2006-12-14
> **mikerduffy said:**
> Is a language-switching feature available on other desktops?Yes. That is not a language switcher but a keymap switcher. GNOME and KDE offer this. In GNOME, right-click panel -> Add to Panel -> Keyboard Indicator. To switch languages (on your applications) you must logout.

---

### Post by scrooge_74 on 2006-12-15
i try ICEWM for a few hours, it is a lot faster than Gnome, but I am just too lazy to set up things to just work when I click on them, maybe during the weekend I will toy more with it. Specially if I manage to change my keyboard layout to spanish.

Probably will install it on a machine been use as SMB server just to have a GUI for doing a few things.

---

### Post by aysiu on 2006-12-19
I have to tell you--I was stuck on IceBuntu for a **long** time--it was a professional-looking theme that made IceWM usable.

As of today, there's a new IceWM theme on my desktop--Thin Black.

I found it in [this thread](http://ubuntuforums.org/showthread.php?p=1908876), and it's slick--very slick.

---

### Post by K.Mandla on 2006-12-19
> **mikerduffy said:**
> [***This screenshot***]("http://lxp.sourceforge.net/TBar_details_1024.jpg") caught my eye.  Is a language-switching feature available on other desktops?
I think KDE does something like that, doesn't it? I don't use KDE, but the last time I used a SLAX live CD I could've sworn there was some sort of language switcher button on the taskbar. It looked like a little flag, I think. Any KDE fans available to corroborate?

---

### Post by IYY on 2006-12-20
> **aysiu said:**
> I have to tell you--I was stuck on IceBuntu for a **long** time--it was a professional-looking theme that made IceWM usable.

As of today, there's a new IceWM theme on my desktop--Thin Black.

I found it in [this thread](http://ubuntuforums.org/showthread.php?p=1908876), and it's slick--very slick.

Cool :D

---

### Post by bionnaki on 2006-12-20
so, I have a question. I will be doing an install on my brother's old computer that currently runs windows 98 (I am unsure of the exact specs, but basically it's a win98 computer). I would like to do a server install of either dapper or edgy and then use aysiu's script to install icewm + themes. is this recommended? or do I need to have the default ubuntu gnome install first?

how exactly would I use this script? I suppose I could burn it disc or host it on my website and just wget it, but then what do I do?

also, is it possible to modify the script to use the black theme? or is installing the theme easy once I have everything set up?

I have never done an install on an old system before, so I want to make I have everything in order before I do it. 

thanks!

---

### Post by aysiu on 2006-12-20
If you don't have experience with IceWM, I'd **highly** recommend installing regular Ubuntu *first*.

The script kind of assumes you already have Ubuntu installed, anyway, and it draws on a lot of Gnome services (and even with that, IceWM is still a *lot* faster than Gnome).

So what you do is a regular installation of Ubuntu (using the Alternate CD, of course). Then you download the script. Give me a few minutes, and I'll attach a modified version that will use the black theme instead.

Once the script is on your desktop, you just open up a terminal and paste in these commands: ```
cd ~/Desktop
tar -xvzf icewm.tar.gz
chmod +x setupicewm.sh
./setupicewm.sh
```

**Edit**: Okay. I've uploaded the revised script. I haven't actually tested the revision yet, so let me know if it doesn't work.

---

### Post by BLTicklemonster on 2006-12-20
> **aysiu said:**
> If you don't have experience with IceWM, I'd **highly** recommend installing regular Ubuntu *first*.

The script kind of assumes you already have Ubuntu installed, anyway, and it draws on a lot of Gnome services (and even with that, IceWM is still a *lot* faster than Gnome).

So what you do is a regular installation of Ubuntu (using the Alternate CD, of course). Then you download the script. Give me a few minutes, and I'll attach a modified version that will use the black theme instead.

Once the script is on your desktop, you just open up a terminal and paste in these commands: ```
cd ~/Desktop
tar -xvzf icewm.tar.gz
chmod +x setupicewm.sh
./setupicewm.sh
```


He is using this script, btw, in case anyone wants to find it. (this was for my own selfish use, btw ;) I don't want to be looking all over for it tonight when I home.)

[http://ubuntuforums.org/showpost.php?p=1549508&postcount=58](http://ubuntuforums.org/showpost.php?p=1549508&postcount=58)

---

### Post by scrooge_74 on 2006-12-20
I have a question for those that like and use Icewm a lot.  How can I change the keyboard layout so I can write in another language such as spanish? (My keyboard is in english)

I can configure it very easy in Gnome, but I don't have a clue how to do it in Ice

thanks

---

### Post by Albi on 2006-12-20
> **scrooge_74 said:**
> I have a question for those that like and use Icewm a lot.  How can I change the keyboard layout so I can write in another language such as spanish? (My keyboard is in english)

I can configure it very easy in Gnome, but I don't have a clue how to do it in Ice

thanks

Change it in gnome, then make sure to autostart gnome-settings-daemon.  Then, when the dialog asks, choose "use gnome settings".

I'm glad people liked my theme.  It still needs more polish, especially in the taskbar, and it won't maximize all the way, I don't know how I should edit my frameAT.xpm file to fix this, but I'll do it tommorow when school's over.

Anyways, as I said in that thread, IceWM has as much power as metacity when it comes to theming, just not enough interest I guess.  If someone posts a really nice metacity theme here I'll try to port it to IceWM, it's actually incredibly easy.

By the way, anyone know how the LookXP people got an actual box to draw over the windows in the toolbar?

---

### Post by aysiu on 2006-12-20
> **Albi said:**
> 
I'm glad people liked my theme.  It still needs more polish, especially in the taskbar, and it won't maximize all the way, I don't know how I should edit my frameAT.xpm file to fix this, but I'll do it tommorow when school's over. I think you did a smashing job. I really, really like this theme.

> If someone posts a really nice metacity theme here I'll try to port it to IceWM, it's actually incredibly easy. I wasn't going to demand anything, but since you offered, any chance you could port [Humanoid-OSX](http://gnome-look.org/content/show.php?content=35753)? I know a lot of people frown on OS X look-a-like themes, but the ones currently available for IceWM are piss-poor.

If you have the time, cool. If not, that's also cool.

---

### Post by IYY on 2006-12-21
> I'm glad people liked my theme. It still needs more polish, especially in the taskbar, and it won't maximize all the way, I don't know how I should edit my frameAT.xpm file to fix this, but I'll do it tommorow when school's over.

It maximizes all the way on my machine. With the taskbar, it's mostly just a matter of shifting the images so that it aligns nicely.

---

### Post by Albi on 2006-12-21
> **aysiu said:**
> 
 I wasn't going to demand anything, but since you offered, any chance you could port [Humanoid-OSX](http://gnome-look.org/content/show.php?content=35753)? I know a lot of people frown on OS X look-a-like themes, but the ones currently available for IceWM are piss-poor.

If you have the time, cool. If not, that's also cool.

I was looking more for a professional looking Gnome-looking theme (not too over-the top) for now, although I'll definitely do an OSX clone eventually.

---

### Post by aysiu on 2006-12-21
> **Albi said:**
> I was looking more for a professional looking Gnome-looking theme (not too over-the top) for now, although I'll definitely do an OSX clone eventually.
Cool. Please post a link to whatever you port. Thanks for all your good work.

---

### Post by IYY on 2006-12-21
Theme's I'd like to see ported...

Some version of the Gilouche theme (maybe in green or blue): [http://art.gnome.org/themes/metacity/1286](http://art.gnome.org/themes/metacity/1286)

And something like the old Clearlooks theme, possibly sans colour:
[http://art.gnome.org/themes/metacity/1009](http://art.gnome.org/themes/metacity/1009)

---

### Post by halw on 2006-12-21
aysiu,

Have loaded icewm after installing Kubuntu. Problem is can't find programs in icewm that are in Kubuntu, e.g., Ooo, Kontac, etc.

How do you get these things to show up?

---

### Post by aysiu on 2006-12-21
If you edit the /home/halw/.icewm/preferences file, you should see something about showing (1, as opposed to hiding, which is 0) the Programs menu, and I think that Programs menu is autogenerated, but I could be wrong about that.

If you don't have a preferences file there, you can copy one from /etc/X11/icewm to your home directory and then modify it: ```
sudo cp /etc/X11/icewm/preferences ~/.icewm/preferences
nano ~/.icewm/preferences
```

---

### Post by halw on 2006-12-21
> **aysiu said:**
> If you edit the /home/halw/.icewm/preferences file, you should see something about showing (1, as opposed to hiding, which is 0) the Programs menu, and I think that Programs menu is autogenerated, but I could be wrong about that.

If you don't have a preferences file there, you can copy one from /etc/X11/icewm to your home directory and then modify it: ```
sudo cp /etc/X11/icewm/preferences ~/.icewm/preferences
nano ~/.icewm/preferences
```

Followed your instructions. I have Program menu item but no programs.

Any ideas?

---

### Post by scrooge_74 on 2006-12-21
Read the begining of the post and you will find how to add programs to your menu or you could install iceme to do it from the GUI

---

### Post by Albi on 2006-12-21
It's not exactly Gilouche, but it's close enough (better IMO)
[http://ubuntuforums.org/showthread.php?p=1917147#post1917147](http://ubuntuforums.org/showthread.php?p=1917147#post1917147)

Just did it today.  No bugs or anything, but might add more animations for the buttons+ a different colour for inactive windows in the future.  Background is included in theme, just change the path accordingly (i'll try to find out how to fix it so you don't have to do this shortly)

---

### Post by hanzomon4 on 2006-12-22
What's the easiest  way to get the menus setup, also can I add an applet to control my sound?... like in gnome

---

### Post by halw on 2006-12-22
What repository is ROX in? Tried installing but got message that it could not be found.

---

### Post by Albi on 2006-12-22
> **hanzomon4 said:**
> What's the easiest  way to get the menus setup, also can I add an applet to control my sound?... like in gnome

Not sure how to do this, although if you have multimedia buttons on your keyboard and they work under gnome, you can run gnome-settings-daemon at startup and it will work

As for menus, install iceme.  It's a very simple graphical tool.

> What repository is ROX in? Tried installing but got message that it could not be found.
It's called rox-filer

---

### Post by hanzomon4 on 2006-12-22
I was able to set up volume hotkeys by editing the icewm/key file to use amixer(alsa) instead of aumix(oss)```
 key "Alt+Ctrl+d"	amixer set PCM 5-		# lower volume
key "Alt+Ctrl+u"	amixer set PCM 5+		# raise volume

```

I want to use the + and - but I don't no what to call them: plus, Plus,+.... get where I'm going

---

### Post by halw on 2006-12-22
Well it looks like I'm really close to having things setup to use IceWM on a dapper Server install.

One of the final things I need to resolve is to get the system to recognize my usb flash drive. I have an xorg.conf file on there, from a mepis install, that allows the correct 1024x768 resolution on the Toshiba 2545xcdt.

What files do I need to modify to get my usb port recognized?

---

### Post by hanzomon4 on 2006-12-22
Does it have a mount point? Oh, and what file-manager are you using(rox-filer?)

---

### Post by halw on 2006-12-22
Doesn't seem to have a mount point.

Am using rox-filer.

---

### Post by halw on 2006-12-22
OK, got it. I used thunar fm and found the usb stick. Was able to open with kate to verify access. I then used konsole to copy xorg.conf from usb drive to /etc/X11 and voila, 1024x768 screen resolution. Nice crisp fonts, et al.

IceWM found all the packages I have loaded thus far and automatically placed them in the menus. Cool=D> !

Thank everyone for your help and discussion on this subject. Setting up this old laptop this way gives it new life.

---

### Post by hanzomon4 on 2006-12-22
Glad you got it  working and do check out [Thin Black theme]("http://www.ubuntuforums.org/showthread.php?p=1909879")... It's so neat!!

---

### Post by roderikk on 2006-12-22
Hi all!

I have found this site which explains a lot: [IceWM tips]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/IceWM_Tips") . Hope it helps some!

BTW, I tried setting my background image on several ways but I can't seem to get it to work? Anyone else having this problem?

---

### Post by aysiu on 2006-12-22
> **roderikk said:**
> Hi all!

I have found this site which explains a lot: [IceWM tips]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/IceWM_Tips") . Hope it helps some!

BTW, I tried setting my background image on several ways but I can't seem to get it to work? Anyone else having this problem?
Nope.

You have to run *icewmbg*.

You also have to edit your /home/roderikk/.icewm/preferences file to specify where the background image is that you want to use.

---

### Post by hanzomon4 on 2006-12-22
Or you can enable the pinboard(in rox-filer) and just right click the desktop and set background

---

### Post by dmizer on 2006-12-22
i absolutely love icewm.  once you learn the little tricks, it's easily managable.  and i LOVE how it revives my older machines.

here's my current desktop using the green icebuntu theme (thanks IYY)
[[img]http://ubuntuforums.org/picture.php?pictureid=1485&albumid=165&dl=1218476141&thumb=1[/img]](http://ubuntuforums.org/picture.php?albumid=165&pictureid=1485)

i found everything i needed to know about icewm in this thread:
[http://www.ubuntuforums.com/showthread.php?t=98233&highlight=howto+ubuntu+lite](http://www.ubuntuforums.com/showthread.php?t=98233&highlight=howto+ubuntu+lite)
i've been meaning to take some time and compile it into a more concise guide.

here's the guide i followed to get scim working for multi language input:
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) ... the guide indicates that it's for dapper, but it also works for edgy.

the only drawback that i've found is that icewm doesn't support multiple locales well.

ps, once you've modified the preferences file to give your shutdown menu option, you can also access your shutdown option with ctrl+alt+del

edit:
pps, my machine is a 600mhz p3 with 128mhz of ram.  with my current setup, she boots in under 4 minutes, and loads the desktop in about 5 seconds.  but i still get handy features like auto-mounting cdrom and usb, and i can watch dvd's in full screen with no problem.

---

### Post by oyvindaa on 2006-12-25
I've got a second computer (500mhz computer with 512mb ram), and as I've grown tired of Xfce I thought I'd try something else. So I landed on IceWM. The base system is Dapper (I'll have to remove the ubuntu-desktop and install the icewm-packages). We'll see how it goes! Exciting :)

---

### Post by BLTicklemonster on 2006-12-26
Been clowning around some more, and the easiest way I have found to have a real desktop without wierd stuff going on (rox) is to put 

nautilus &

in startup.


Also, if you want a quick screenshot, install scrot (sudo aptitude install scrot) and put it in the toolbar

prog "Scrot" scrot scrot

and restart icwm. Just click on it, you hear a beep, and you have a screenshot in your /home directory.

---

### Post by finferflu on 2006-12-27
Ok, I've had my try with IceWM, and I'm quite satisfied, even the adesklets work fine...
The only thing I would like to know if it's possible to limit the size of maximized windows, or avoid them to cover the upper part of the screen, since I've got a desklet there, and I wouldn't like to cover it...

Anyone?

---

### Post by BLTicklemonster on 2006-12-27
how the heck did you get adesklets to work? I installed it and nothing ever happens when i run it

---

### Post by oyvindaa on 2006-12-27
> **BLTicklemonster said:**
> Been clowning around some more, and the easiest way I have found to have a real desktop without wierd stuff going on (rox) is to put 

nautilus &

in startup.


Also, if you want a quick screenshot, install scrot (sudo aptitude install scrot) and put it in the toolbar

prog "Scrot" scrot scrot

and restart icwm. Just click on it, you hear a beep, and you have a screenshot in your /home directory.

I put ```
nautilus &
``` in startup, because I wanted my external harddrive (it's shared through Samba) to automount at bootup. Now I'd like to prevent nautilus from starting up at boot and still make my hd automount and staying shareable through Samba, and revert back to Rox-filer running the desktop. I've tried removing 'nautilus &' file and putting 'rox --pinboard=yourusername &' back there but it didn't change anything. I guess nautilus has to be blocked off elsewhere?

How do I accomplish this? :)

---

### Post by finferflu on 2006-12-27
> **BLTicklemonster said:**
> how the heck did you get adesklets to work? I installed it and nothing ever happens when i run it

Just reading the instructions :D

Go on the [adesklets website]("http://adesklets.sourceforge.net/desklets.html"), and download the desklet you want, every desklet should have a Readme file that explains how to use it. In my case I only downloaded yab, and all I needed to do was to run yab.py from its directory, and choose whether I wanted to test it or register it. If you test it, it only shows until you terminate it from command line, if you register it, it will start up every time you launch adesklets. Quite simple. Cofiguration was manual, through a config.txt file. The very good thing is that it's very lightweight :)

Anyone with a hint for placing windows in a way that they don't cover the desklet? It's just a shame that it gets covered...

EDIT: If you want even more eyecandy, you can install/use Katapult as your quick launcher, it's very nice, and it works with ALT+SPACEBAR ;)

---

### Post by finferflu on 2006-12-27
> **oyvindaa said:**
>  I've tried removing 'nautilus &' file and putting 'rox --pinboard=yourusername &' back there but it didn't change anything. I guess nautilus has to be blocked off elsewhere?

How do I accomplish this? :)

Not to be stupid, but did you actually put ```
'rox --pinboard=**yourusername** &'
``` without changing *yourusername* to your actual username??

---

### Post by oyvindaa on 2006-12-27
> **finferflu said:**
> Not to be stupid, but did you actually put ```
'rox --pinboard=**yourusername** &'
``` without changing *yourusername* to your actual username??

No, I used my actual username :) 

It just seems like Nautilus is running the show at the moment and I can't stop it from doing just that.

---

### Post by BLTicklemonster on 2006-12-27
> **oyvindaa said:**
> I put ```
nautilus &
``` in startup, because I wanted my external harddrive (it's shared through Samba) to automount at bootup. Now I'd like to prevent nautilus from starting up at boot and still make my hd automount and staying shareable through Samba, and revert back to Rox-filer running the desktop. I've tried removing 'nautilus &' file and putting 'rox --pinboard=yourusername &' back there but it didn't change anything. I guess nautilus has to be blocked off elsewhere?

How do I accomplish this? :)

There's a command, something like 

nautilus -nodesktop &


or

nautilus --no-desktop &

I can't remember...

or something, I think it's mentioned here. Use that command along with the rox pinboard, maybe?


one of these days, I'm going to set up ubuntu with my username as 

yourusername

so I can just copy and paste all these instructions....

---

### Post by oyvindaa on 2006-12-28
I'm afraid that didn't work mate :\

---

### Post by finferflu on 2006-12-28
Are you sure it's nautilus? have you tried killing it? If you have deleted it from the startip script it shouldn't load at all. Maybe its startup does not depend on that script. Maybe you're using Metacity?

---

### Post by Albi on 2006-12-28
> **aysiu said:**
> 
 I wasn't going to demand anything, but since you offered, any chance you could port [Humanoid-OSX](http://gnome-look.org/content/show.php?content=35753)? I know a lot of people frown on OS X look-a-like themes, but the ones currently available for IceWM are piss-poor.

If you have the time, cool. If not, that's also cool.

Done :D
[http://ubuntuforums.org/showthread.php?t=326516](http://ubuntuforums.org/showthread.php?t=326516)


> **hanzomon4 said:**
> Glad you got it  working and do check out [Thin Black theme]("http://www.ubuntuforums.org/showthread.php?p=1909879")... It's so neat!!

Glad to see my theme in use.  You might wanna get the latest version though, I improved it a lot, especially the panel and "Start" button

---

### Post by oyvindaa on 2006-12-28
> **finferflu said:**
> Are you sure it's nautilus? have you tried killing it? If you have deleted it from the startip script it shouldn't load at all. Maybe its startup does not depend on that script. Maybe you're using Metacity?

Yeah I'm pretty sure it's Nautilus, tried killing it but with no result.

I think its startup depends on something else, yes. Just don't know where it is.. :)

---

### Post by finferflu on 2006-12-28
> **oyvindaa said:**
> Yeah I'm pretty sure it's Nautilus, tried killing it but with no result.

I think its startup depends on something else, yes. Just don't know where it is.. :)

Have you tried running the following command?
```
ps -A
```

If not, check whether nautilus is there, after you have killed it. If it's still there go for

```
ps -A s
```

And check wheter there is a Z under the heading STAT, which means it's a zombie process...

---

### Post by oyvindaa on 2006-12-29
Thank you for the help, although I've now decided it's ok the way it is, so I'll just let it be :)

---

### Post by BLTicklemonster on 2006-12-29
> **finferflu said:**
> Just reading the instructions :D

Go on the [adesklets website]("http://adesklets.sourceforge.net/desklets.html"), and download the desklet you want, every desklet should have a Readme file that explains how to use it. In my case I only downloaded yab, and all I needed to do was to run yab.py from its directory, and choose whether I wanted to test it or register it. If you test it, it only shows until you terminate it from command line, if you register it, it will start up every time you launch adesklets. Quite simple. Cofiguration was manual, through a config.txt file. The very good thing is that it's very lightweight :)

Anyone with a hint for placing windows in a way that they don't cover the desklet? It's just a shame that it gets covered...

EDIT: If you want even more eyecandy, you can install/use Katapult as your quick launcher, it's very nice, and it works with ALT+SPACEBAR ;)


Katapult launches, but it just sits there.

Adesklets... I have to register, and it talks to the mothership... not going to do that, thanks.


*edit:
it never fails... I just found the answer. 

START TYPING. LMAO.

WOOHOOO nice program.


Now, what are the chances of getting icons on my desktop without killing my icewm logout function? Nautilus messed that up real nice.

---

### Post by finferflu on 2006-12-29
> **BLTicklemonster said:**
> 
Adesklets... I have to register, and it talks to the mothership... not going to do that, thanks.


What are you talking about?? you have to register the desklet with the program adesklet, so that when you start up adesklets, all the desklets you have registered with it will start together. It's not a registration like you have to fill in a form, or send data. You only register the desklet with adesklets...

---

### Post by BLTicklemonster on 2006-12-29
The page said that he applets constantly contact the site for updates. I just don't care for anything other than ubuntu itself doing that. And even then, it's no something that brings smiles to my face.

---

### Post by finferflu on 2006-12-29
Most of the apps always check for updates, Firefox does that as well. Checking for updates does not send your data anywhere, it's just a common thing for apps.
But it's your choice anyway ;)

---

### Post by BLTicklemonster on 2006-12-29
I'm not paranoid, they're out to get me, honestly!!!

---

### Post by LaneLester on 2006-12-30
> **IYY said:**
> but do you think the old "fat border" look is even needed anymore?

Yes, I vote for fat. I'm running the green one now.

Lane

---

### Post by LaneLester on 2006-12-30
> **scrooge_74 said:**
> Read the begining of the post and you will find how to add programs to your menu or you could install iceme to do it from the GUI

I must have missed it somehow. I searched the preferences file for all instances of "menu" and "show," and I never saw anything related to the Programs menu.

Lane

---

### Post by finferflu on 2006-12-31
Has anyone noticed that if you press CTRL+ALT+SPACEBAR you get a command line in the toolbar? It would be have been a very nice idea if it only worked... I don't know why, but when I type in a command and press enter, nothing happens... too bad...

---

### Post by IYY on 2006-12-31
> **finferflu said:**
> Has anyone noticed that if you press CTRL+ALT+SPACEBAR you get a command line in the toolbar? It would be have been a very nice idea if it only worked... I don't know why, but when I type in a command and press enter, nothing happens... too bad...

First time I hear of this feature not working. I've been using it frequently for years.

---

### Post by finferflu on 2006-12-31
> **IYY said:**
> First time I hear of this feature not working. I've been using it frequently for years.

Do you think there's anything I can do about it? Tinkering something somewhere? Could have I broken such a feature with all the flippin' GUI configuration apps I've installed and run?

---

### Post by BLTicklemonster on 2006-12-31
That's odd finerflu, mine works.

---

### Post by finferflu on 2007-01-01
Do you guys use a double height toolbar to make it work?

EDIT: I've copied somebody else's preferences file, and now it works, even though the terminal that appears when I press CTRL+ENTER after I enter the command, crashes instantly...

EDIT2: I've just reconfigured the whole thing using the preferences file in /etc/X11/icewm and copying it into ~/.icewm/. I have found out that the main problem is in TerminalCommand. If I put 

```
TerminalCommand="aterm -tr +sb -sh 60"
```

When I press CTRL+ENTER in the Command Line Interface, nothing happens, but if I leave it as it is, namely

```
TerminalCommand="x-terminal-emulator"

```
It works, but it shows me an ugly grey tterm. I really would like to change it, but I don't know how...

---

### Post by finferflu on 2007-01-01
Who said that IceWM is not user-friendly and ugly?
I just want to show off how I have configured my mother's desktop, so that it's easy for her to use (browse the web, check mail, use messenger, listen to music, and so on) eyecandy to see, and light for her old machine.

I must say I really like it! :D

---

### Post by oyvindaa on 2007-01-01
That looks great finferflu! :)

---

### Post by Mateo on 2007-01-01
very nice finferflu.  mind sharing any of your secrets?

---

### Post by finferflu on 2007-01-01
> **oyvindaa said:**
> That looks great finferflu! :)

Thanks! :D

> **Mateo said:**
> very nice finferflu.  mind sharing any of your secrets?

Secrets? What secrets? I've used adesklets (available in the repositories), with the [yab desklet]("http://adesklets.sourceforge.net/desklets.html"). 
The background is from [kde-look.org]("http://www.kde-look.org/content/show.php?content=39512") and the theme is [IceOSX from Albi]("http://ubuntuforums.org/showthread.php?t=326516").
The toolbar is configured with the preferences file. 
If you need any tips on anything just ask me ;)

Suggestions are welcome as well :)

---

### Post by BLTicklemonster on 2007-01-01
> **oyvindaa said:**
> I'm afraid that didn't work mate :\

nautilus --no-desktop --browser

???

---

### Post by finferflu on 2007-01-02
ah, by the way, if you guys want icons on the desktop without messing with nautilus (or rox), you could give a look to [idesk]("http://idesk.sourceforge.net/wiki/index.php/Main_Page") (in the repositories). I use it mainly to set my desktop background, since it doesn't seem to work for me with the normal parameters in the preferences files. The nice thing about idesk is that even if you kill it, the desktop background stays.

---

### Post by BLTicklemonster on 2007-01-02
You know, I messed with idesk in fluxbox, and I'd rather use either dgesklets $ or rox -p=main &.

But I do wonder, in flux, when I use gdesklets, if I restart flux (not logging out, but just click restart), the gdesklets on my desktop are removed, yet the gdesklets icon stays on the taskbar. Odd.

---

### Post by finferflu on 2007-01-02
> **BLTicklemonster said:**
> You know, I messed with idesk in fluxbox, and I'd rather use either dgesklets $ or rox -p=main &.

But I do wonder, in flux, when I use gdesklets, if I restart flux (not logging out, but just click restart), the gdesklets on my desktop are removed, yet the gdesklets icon stays on the taskbar. Odd.

Maybe you need to register your desklets with gdesklets?

---

### Post by BLTicklemonster on 2007-01-02
:-k :???:  and I wonder how one would do that?

As far as idesk is concerned, I'm trying to work that out at present. If I can ever get it all set right (whoever wrote the readme did the typical "I know what this means, so it makes sense to me", trick and doesn't just come out and say exactly what needs to go where. Yeah, it does say what goes where, but there's two ways to do that), then I'll probably just stick with it. (you have to grid where the icons go... sheesh! ) 

Logically (apply your own logic and let 'er rip)
```
inset tab a42e33b into slot a42ee3b
```

or

Sensibly (make some freaking sense so people know wtf you're talking about)
```
this goes here; that goes there
```

Notice that Linux and Logical both begin with the same letter? 

;)

anyway, I didn't have time this morning to do much, so I printed out the 7 pages of the readme for futher perusal.

---

### Post by finferflu on 2007-01-02
Did you give a look at the wiki as well?

---

### Post by forcesofhabit on 2007-01-04
How can I get yab to work this? I've installed adesklets and then ran adesklets -i
now that Ive downloaded yab from there how do I use it in IceWM?

---

### Post by finferflu on 2007-01-05
> **forcesofhabit said:**
> How can I get yab to work this? I've installed adesklets and then ran adesklets -i
now that Ive downloaded yab from there how do I use it in IceWM?

If you've downloaded yab, you should be able to locate its folder (or the zipped file, in this case just unzip it), otherwise just download it from the adesklets website. cd in the yab folder and run:

```
./yab.py
```

It will ask you whether you want to test it or register it. If you test it, yab will close as soon as you terminate the process. If you register it, yab will appear everytime you run adesklets. 

Have fun!

---

### Post by MkfIbK7a on 2007-01-08
i love icwm better than all tothe WM put toghether!

---

### Post by Mateo on 2007-01-08
I don't like the fact that you have to click to expand the applications in the menu bar.

---

### Post by forcesofhabit on 2007-01-10
Why does nothing show up when I run adesklets???
I see something flash in the upper corner...

---

### Post by forcesofhabit on 2007-01-10
Okay I figured out I must have to run 'adesklets' in terminal with a specified window manager preference (ex. --rox)

I used --rox, and it appears, but it won't let me configure the panel.

It's also not transparent...?

---

### Post by Peter76 on 2007-01-28
:guitar: Yihoo!!!!

Just installed Ubuntu with Icewm on a Toshiba 300CDT laptop, 200 Mhz Pentium1, 32 MB ram.....
Configuration as follows:

- no display manager, just do startx after login
- Icewm with bluecrux theme
- Xfe file manager, comes included with an image viewer
- Gtkpad, lightweight editor
- Dillo as webbrowser
- standard xterm
- XMMS for mp3 playing.

Very lightweight and works fast ( for such an old machine, but really, I'm impressed )

---

### Post by K.Mandla on 2007-01-28
> **Peter76 said:**
> :guitar: Yihoo!!!!

Just installed Ubuntu with Icewm on a Toshiba 300CDT laptop, 200 Mhz Pentium1, 32 MB ram.....
Configuration as follows:

- no display manager, just do startx after login
- Icewm with bluecrux theme
- Xfe file manager, comes included with an image viewer
- Gtkpad, lightweight editor
- Dillo as webbrowser
- standard xterm
- XMMS for mp3 playing.

Very lightweight and works fast ( for such an old machine, but really, I'm impressed )
Sweeet! \\:D/

Check out [urxvt ]("http://packages.ubuntu.com/edgy/x11/rxvt-unicode")if you want a transparent terminal -- I run that on a 300Mhz machine and supposedly it uses less memory than xterm.

[Leafpad]("http://packages.ubuntu.com/edgy/editors/leafpad") looks and behaves a lot like Notepad, and doesn't seem too cumbersome.

Just some ideas. ;)

---

### Post by fuscia on 2007-01-28
i've been using it for the past couple of days. it reminds me of route1. (i actually kind of like some of the fugly themes.)

---

### Post by berserker on 2007-01-28
> **Mateo said:**
> I don't like the fact that you have to click to expand the applications in the menu bar.

Change the following from 0 to 1 in your ~/.icewm/preferences file:

```
MenuMouseTracking=1
```

---

### Post by berserker on 2007-01-28
> **wert613 said:**
> i love icwm better than all tothe WM put toghether!

I agree!  I've tried KDE, Gnome, Fluxbox and XFCE and prefer IceWM because of its  ease of configurability and speed.

---

### Post by BLTicklemonster on 2007-01-29
> **berserker said:**
> I agree!  I've tried KDE, Gnome, Fluxbox and XFCE and prefer IceWM because of its  ease of configurability and speed.

What he said.

---

### Post by finferflu on 2007-01-29
I don't want to spoil this thread, I also believe IceWM is great, I've customized it to my heart's desire, and I think its best feature is usability. Nevertheless I've found my home with E17, even though it's not as usable as IceWM sometimes. I'm just comparing the two, because they're both very lightweight, and I like them both.

---

### Post by vronp on 2007-02-07
> **roderikk said:**
> Hi all!

I have found this site which explains a lot: [IceWM tips]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/IceWM_Tips") . Hope it helps some!

BTW, I tried setting my background image on several ways but I can't seem to get it to work? Anyone else having this problem?
Yes, I had the same problem but finally figured out that the default.theme file has a path line that overrides all other "methods" for setting the background image.

Go to your themes directory and edit the default.theme file.  Look for the path to the background image.  Are you also using the "Thin Black" theme?  If so, the path in the default.theme file is wrong.  It's the last line in the file.

---

### Post by SunnyRabbiera on 2007-02-07
I have a love/ hate relationship with IceWM
actually i perfer windowmaker :D

---

### Post by ago on 2007-02-07
IceWM is one of the best window managers around. By far.  It is really a shame that almost any default setting that ships with it completely and utterly sucks, from the theme, to the menu, to almost anything else in the configuration. 

If this came bundled with a nice theme by default, like ThinBlack (why not be different for once and go with a black theme as opposed to grey stuff like anybody else?), other 5 good themes as opposed to 80 junk ones, a decent configuration tool, matching but light theme for gtk 1/2 controls, a nice light terminal (my favorite is mrxvt**) a "normal" menu and some sane settings, there would be serious competition for anybody else.

It sounds like a good project for a metapackage,  BlackIce or something...

---

### Post by ago on 2007-02-07
PS here is .mrxvtrc configurationn if anyone is interested (you obviously need to install mrxvt):

> 
## see /usr/share/doc/mrxvt-common/examples

## TRANSPARENCY
#Mrxvt.transparent:		True
#Mrxvt.transparentScrollbar:	True
#Mrxvt.transparentTabbar:	True
#Mrxvt.tintColor:		#000000
#Mrxvt.shading:			85

## SCROLLBAR
Mrxvt.scrollBar:		True
Mrxvt.scrollbarRight:		True
Mrxvt.scrollbarStyle:           rxvt
Mrxvt.saveLines:                5000
#Mrxvt.scrollTtyOutputInhibit:   true
#Mrxvt.scrollTtyKeypress:        true

## COLORS
Mrxvt.background:		black
Mrxvt.borderColor:		green
Mrxvt.foreground:		white
Mrxvt.cursorColor:		yellow
Mrxvt.itabBackground:           #101010
Mrxvt.tabBackground:            #000000
Mrxvt.itabForeground:           #909090
Mrxvt.tabForeground:            #9a9a9a
Mrxvt.scrollColor:              #808080
Mrxvt.troughColor:              #202020

## TABS
Mrxvt.bottomTabbar:		True
Mrxvt.hideButtons:		False
Mrxvt.syncTabIcon:		True
Mrxvt.syncTabTitle:		True
Mrxvt.highlightTabOnBell:       True

## SHORTCUTS
Mrxvt.macro.Ctrl+Shift+n:	NewTab "Nano" !nano -w

## MENU
Mrxvt.showMenu:			False

## MISC
Mrxvt.smoothResize:		False
Mrxvt.smartResize:		False


---

### Post by Sunflower1970 on 2007-02-07
I think I'll have to try this out. I've been using Enlightenment on an old PII 400 Mhz 384 MB RAM. And although I like some of the flash, it's just not very intuitive (although I seem to be getting more comfortable with it...and I like how I can go from one desktop to the next by just sliding the mouse to the right and keep going 8) )

---

### Post by Sunflower1970 on 2007-02-08
I'm glad I came upon this thread. I installed it tonight and have been playing around with it for most of the evening. I think I really like it. It'll take some getting used to, and I'm still figuring out rox-filer, but on the whole, I think this will be my new desktop enviornment for this old computer of mine. It's much zippier than Enlightenment, as well.  :)

---

### Post by BLTicklemonster on 2007-04-07
I know it's just stupid to be this way, but I want to use nautilus in icewm so I can have icons on my desktop while using something I am familiar with. As opposed to the other solutions here.

So I edited my startup to this:
```
#!/bin/sh
icewmbg & # I can do without this now, probably
nautilus -n & # -n so no browser opens
numlockx &
gnome-volume-manager &
gnome-settings-daemon &
lomoco &
```


then edited my menu to include this:
```
prog "Kill Nautilus" "killall nautilus" killall nautilus
```


Now I just click start on my toolbar, then click kill nautilus, then log out.

Now there ought to be a way to incorporate (probably already posted on here somwhere) ***killall nautilus *** in with the logout command, but I wonder just how that's done?

Best thing about it is, I have my partitions on my desktop now :)

---

### Post by Mateo on 2007-04-07
shouldn't it just be:

 whatever-the-logout-command-is & killall nautilus

?

---

### Post by BLTicklemonster on 2007-04-07
Yep, but I can't find the logout part, lol.

---

### Post by aysiu on 2007-04-07
> **BLTicklemonster said:**
> Yep, but I can't find the logout part, lol.
```
cd ~/.icewm
nano preferences
``` It's in there somewhere.

---

### Post by BLTicklemonster on 2007-04-07
okay, the preferences I have in my home directory are truncated. I'll have a looksee in X11/icewm and see if I find it, and copy and past it to the other one. Thanks!

Bah there's nothing in /etc/X11/icewm

but in my home icewm, in preferences, I have this:

LogoutCommand=""

---

### Post by OU812 on 2007-04-20
Taking a suggestion from aysiu, I installed ubuntu server + icewm on my old laptop. I liked it so much that I installed it on my desktop. I also installed rox and xfe. I like xfe better, but I installed rox for the desktop icons and handling of wallpaper (though I have been too lazy to find out how to use the features of rox). Again using aysiu's suggestion, I installed the icebuntu theme. For wallpaper, I just go to [www.gnome-look.org;](www.gnome-look.org;) a lot of ubuntu wallpapers can be found there. And you can guess that I chose gdm to complete the theme! Did I forget to mention that the title bar is at the top of the screen?

I am trying to stick with "x" applications: snackamp, xdvdshrink, ripperx, xcdroast, etc. I really don't want gnome or kde apps. They can be wonderful, but I want to try and maintain a light system. I like to call these my ice apps.

I like icewm a lot, but getting it look the way I want is tough. I will have to read about using rox, and I don't like the default design of the menus. I will definitely need to spend a lot of time customizing the menus so that I don't need so many clicks to access my program. Another annoyance is that I was using icepref and hit the defaults button. Now I don't get a start menu when I right-click on the desktop. I have tried changing the mouse settings, but no luck. 

Thanks for this thread. I am only half-way through it, but already I have found some great links and some great reading.

john

---

### Post by OU812 on 2007-04-21
Are iceconf and icepref buggy?

1. Sometimes I change the background, but it doesn't stick - not after restarting or logging out. Sometimes rebooting will do the trick, but that's just too extreme.

2. Sometimes clicking on restart (in icepref) messes things up. It's like there's two versions of icewm: in one version I can right-click on the desktop and get a menu, see the network traffic, and have only one workspace (0). On the other version I have 4 workspaces, no right-click menu on the desktop, and no network traffic icon. Clicking on restart (in icepref) seems to switch between these two versions of icewm.

I want to use the tools because I installed them (as suggested in the ubuntu server wiki) and don't want them taking up valuable space. But if they don't work, no need to install next time. What is your experience? Thanks.

john

---

### Post by Outrunner on 2007-04-21
In my search for the perfect window manager(for me, of course), I tried IceWM a few times and I liked it, but unfortunately for IceWm I found Fluxbox. ;) I still like IceWM though, and now that I've installed Feisty on my laptop, I think I'm going to go with it(or not? I dunno, it's not my fault that I'm so indecisive is it?)

---

### Post by aysiu on 2007-04-25
By the way, earlier in the thread, I think I advised using *gnome-settings-daemon* to get GTK working properly (basically, using Gnome's theme manager), but I've been trying to get rid of all the Gnome crap to get my old laptop running faster.

I found you could still get all the GTK goodness by doing this: ```
nano ~/.gtkrc-2.0
``` This creates and edits a new file in your home directory. In the blank document, type ```
gtk-icon-theme-name = "*iconset*"
gtk-theme-name = "*theme*"
``` Then save (Control-X, Y, Enter).

For example, mine looks like this: ```
gtk-icon-theme-name = "OrangeFun"
gtk-theme-name = "Human"
``` *OrangeFun* is just what I renamed the Human icon theme... for fun. It'll look for icon theme folder names in the /usr/share/icon folder and GTK theme names in the /usr/share/themes folder.

I also used to prefer *gnome-terminal* to *xterm* because of copy and paste. Even though you can't use Shift-Insert in *xterm*, you can paste by pressing middle-click (or, on my laptop, pressing the left- and right-click buttons simultaneously) and copy by highlighting text in *xterm* and then pressing left- and right-click buttons together in another application.

I also avoid using *gnome-volume-manager* by using *thunar-volman-plugin*, which you can activate in the Thunar preferences. I tried *rox-filer* for a while, but the inability to use trash (instead of a total deletion) annoyed me, as did the lack of a location bar. Thunar is light enough for me, though.

---

### Post by dspari1 on 2007-04-26
Correct me if I'm wrong, but wouldn't Ubuntu Lite have less clutter than installing IceWM ontop of Ubuntu? It looks to me that if you do it this way, you'll have more disk space, have less loaded library files, and have an all round more efficient system in the end.

[https://help.ubuntu.com/community/InstallingUbuntuLite](https://help.ubuntu.com/community/InstallingUbuntuLite)

The Ubuntu doc is off and requires the "Alternate Install CD" to install a Command Line System and not the "Ubuntu Server CD".

[http://groups.google.com/group/ubuntu_lite/browse_thread/thread/2606df4148302af5](http://groups.google.com/group/ubuntu_lite/browse_thread/thread/2606df4148302af5)

---

### Post by aysiu on 2007-04-26
Ubuntu Lite is a year and a half old and appears to be for Dapper Drake.

Yes, there are two approaches--installing everything and removing what you don't need, and installing virtually nothing and adding only what you want.

I have a guide to doing the latter:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by dspari1 on 2007-04-26
> **aysiu said:**
> Ubuntu Lite is a year and a half old and appears to be for Dapper Drake.

Yes, there are two approaches--installing everything and removing what you don't need, and installing virtually nothing and adding only what you want.

I have a guide to doing the latter:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

Very nice! Seems like you have your own distro of Ubuntu in the works IMO.

---

### Post by aysiu on 2007-04-26
> **dspari1 said:**
> Very nice! Seems like you have your own distro of Ubuntu in the works IMO.
If I could figure out the ins and outs of Reconstructor, I would probably create something like IceBuntu.

I know there's already a Fluxbuntu, but I haven't been able to warm up to Fluxbox, for some reason.

---

### Post by dspari1 on 2007-04-26
> **aysiu said:**
> If I could figure out the ins and outs of Reconstructor, I would probably create something like IceBuntu.

I know there's already a Fluxbuntu, but I haven't been able to warm up to Fluxbox, for some reason.

I'm still a newbie, so I wouldn't be able to help you there; however, I'm sure that there are a lot of like minded individuals that could help you create IceBuntu with a livecd and everything.

With that said, I hope I'm not tricking you into doing something you really don't want to do :lolflag:

---

### Post by beefcurry on 2007-04-26
more variaty :) nice! I'll try IceWM sometime soon, fluxbox didnt seem very nice to me when I first used it as well :P

---

### Post by aysiu on 2007-04-28
An update: **sound on my old laptop,** I started playing around with Xubuntu to see if it's speedier in Feisty than in previous releases--it *is*, but IceWM is still snappier.

The only problem is that in Ubuntu and Xubuntu, I could use the multimedia keys to raise, lower, and mute the volume. In IceWM, I couldn't.

So I followed [this tutorial on using multimedia keys in Linux](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Multi_Media_Keys_in_Linux.html) and modified it slightly.

First, I installed *xev*: ```
sudo apt-get update && sudo apt-get install xev
``` Then I used it by typing ```
xev
``` and then pressing the keys I wanted. Once I found the *key codes* (176, 174, and 160), I created a shell script in /usr/local/bin: ```
sudo nano /usr/local/bin/multikeys
``` and entered in this text: ```
#!/bin/bash
xmodmap -e 'keycode 176=F13'
xmodmap -e 'keycode 174=F14'
xmodmap -e 'keycode 160=F15'
# F13-F35 are available
``` saved (Control-X, Y, Enter) and made the shell script executable: ```
sudo chmod +x /usr/local/bin/multikeys
``` Then I edited the startup file for IceWM: ```
nano ~/.icewm/startup
``` and added in ```
multikeys &
``` Finally, I edited the keys file for IceWM ```
nano ~/.icewm/keys
``` and made sure these lines were in there: ```
key "F14"	aumix -v -5
key "F13"	aumix -v +5
key "F15"		aumix -v 0
``` After restarting IceWM, I then had volume controls on my keyboard working. The only problem is that *aumix -v 0* doesn't behave the way traditional mute actions behave. *Mute* usually toggles mute/unmute between volume 0 and the current volume. *aumix -v 0* makes the volume 0... so if you want the volume to be back to 25, you have to press the *aumix -v +5* key five times to get it back up there.

---

### Post by Albi on 2007-04-28
Aysiu, is there anyway to change/use a GTK theme without loading gnome-settings-daemon (which requires a gnome installation)

Also, check out my updated ThinBlack theme:
[http://gnome-look.org/content/show.php/ICEWM%3A+Thinblack?content=55648](http://gnome-look.org/content/show.php/ICEWM%3A+Thinblack?content=55648)

---

### Post by aysiu on 2007-04-28
> **Albi said:**
> Aysiu, is there anyway to change/use a GTK theme without loading gnome-settings-daemon (which requires a gnome installation)

Also, check out my updated ThinBlack theme:
[http://gnome-look.org/content/show.php/ICEWM%3A+Thinblack?content=55648](http://gnome-look.org/content/show.php/ICEWM%3A+Thinblack?content=55648)
Yes, check out [this post](http://ubuntuforums.org/showpost.php?p=2537051&postcount=209).

In the meantime, I'll check out your latest ThinBlack.

---

### Post by aysiu on 2007-04-28
For some reason, the menu and show-desktop icons aren't showing up for me with the ThinBlack2 theme. They show up fine in ThinBlack1, though.

---

### Post by Albi on 2007-04-28
Ok, that's strange...
Try running it from terminal, it should show what's wrong.

Surprisingly, no one has mentioned this before.

---

### Post by aysiu on 2007-04-28
Forgive my ignorance, but how do I run it from terminal?

---

### Post by deathbyswiftwind on 2007-04-28
> **aysiu said:**
> Forgive my ignorance, but how do I run it from terminal?


That is something Im not used to reading from you :lolflag:

---

### Post by Albi on 2007-04-28
Well there's two ways...

Either go to failsafe terminal and type icewm

Or from any light window manage (eg fluxbox openbox etc) type icewm --replace *whatever*

Sry for not explaining.  I'm checking it over right now to see if I missed to include some pixmaps, that happens sometimes

Edit: Ok,I tested it on my old machine (debian etch with pure icewm) and it works perfectly.
The only problem I could think of is if you didn't recreate the directories while extracting, so it doesn't know where to look for the toolbar pixmaps

---

### Post by aysiu on 2007-04-28
It's possible I may not have recreated the directories while extracting, but then I don't think I did anything differently from my previous download of the old ThinBlack theme.

In any case, here's the output: ```
IceWM: Warning: File still open: fd=5, target='pipe:[57773]' (missing FD_CLOEXEC?)
IceWM: Warning: Closing file descriptor: 5
IceWM: Warning: File still open: fd=9, target='pipe:[124799]' (missing FD_CLOEXEC?)
IceWM: Warning: Closing file descriptor: 9
icewmbg: using /home/username/.icewm for private configuration files
IceWM: Warning: File still open: fd=5, target='pipe:[57773]' (missing FD_CLOEXEC?)
IceWM: Warning: Closing file descriptor: 5
IceWM: Warning: File still open: fd=9, target='pipe:[124799]' (missing FD_CLOEXEC?)
IceWM: Warning: Closing file descriptor: 9
IceWM: using /home/username/.icewm for private configuration files
IceWM: Warning: Multiple references for gradient "menubg.xpm"
IceWM: Warning: Multiple references for gradient "menusel.xpm"
``` I'll try again and make sure to recreate directories.

**Edit**: I redid the extract, and now it's working fine.

---

### Post by msofer on 2007-05-05
I use (a slightly hacked) IceWM exclusively. 

Absolutely amazed that nobody mentioned the **window list** - it is an incredible feature that I have not found elsewhere, and the main reason I refuse to change.

The other feature I appreciate a lot is the workspace navigation from the keyboard.

---

### Post by finferflu on 2007-05-05
> **msofer said:**
> I use (a slightly hacked) IceWM exclusively. 

Absolutely amazed that nobody mentioned the **window list** - it is an incredible feature that I have not found elsewhere, and the main reason I refuse to change.

The other feature I appreciate a lot is the workspace navigation from the keyboard.
The window list feature is there for at least Gnome, KDE, E17 and Xfce, as far as I know...
You can set up window navigation by keyboard on Gnome and KDE (not sure about Xfce), and it ì's already set up with E17...
Just for info, not to put down IceWM, it's a great WM in my opinion.

---

### Post by emags on 2007-05-07
> **finferflu said:**
> 
You can set up window navigation by keyboard on Gnome and KDE (not sure about Xfce), and it ì's already set up with E17...
Just for info, not to put down IceWM, it's a great WM in my opinion.

Unfortunately, keybinding support has been broken on both KDE and Gnome. This has been listed and confirmed on various bugtrackers for the better part of a decade, but the developers haven't got around to fixing the simple Windows-key support as of yet.

IceWM correctly supports keyboard shortcuts. Unfortunately, Ubuntu's configured to use Gnome by default and IceWM integrates poorly, so there's no clear winning solution. :(

---

### Post by lapsey on 2007-05-07
IceWM is nicely complemented by gnome-settings-daemon (run on startup)

this way you get:

* gnome screensaver/lock
* easy gtk theming. (I used to do that via gtkrc but it was annoying.) 
* uncomplicated multimedia hotkey binding for volume control (to do this with xmodmap is a pain in the butt and doesn't work for mute function anyway(

I don't see any performance loss with gnome-settings-daemon either.

It should also be pointed out that Glipper is a great solution to IceWM's lack of a clipboard buffer.

---

### Post by aysiu on 2007-05-07
Wow--I'm the exact opposite. I used to use *gnome-settings-daemon* until I realized I could edit the *gtkrc* file. How funny!

---

### Post by lapsey on 2007-05-07
> **aysiu said:**
> By the way, earlier in the thread, I think I advised using *gnome-settings-daemon* to get GTK working properly (basically, using Gnome's theme manager), but I've been trying to get rid of all the Gnome crap to get my old laptop running faster.

I found you could still get all the GTK goodness by doing this: ```
nano ~/.gtkrc-2.0
``` This creates and edits a new file in your home directory. In the blank document, type ```
gtk-icon-theme-name = "*iconset*"
gtk-theme-name = "*theme*"
``` Then save (Control-X, Y, Enter).


don't forget 
```

gtk-toolbar-style = 0 # icons only	
gtk-toolbar-style = 1 # text only
gtk-toolbar-style = 2 # both, default

```

[http://gtk.php.net/manual1/es/html/gtk.enum.gtktoolbarstyle.html](http://gtk.php.net/manual1/es/html/gtk.enum.gtktoolbarstyle.html)

Huge icons in thunar bugged me for ages before I worked it out

---

### Post by aysiu on 2007-05-07
Thanks for the tip!

---

### Post by lapsey on 2007-05-07
Does anyone else find that IceWM is irrational when remembering 'restored' window dimensions? I was hoping they would get around to fixing it with the latest version..

Also pixmap digital clocks were invented by the devil and if you go out of your way to make a theme with one in you should be tried for crimes against design ;)

---

### Post by hanzomon4 on 2007-05-22
I just re-setup my Ice, I going to set this up for all of the other users that use this computer. I got compiz working close enough to where beryl was but the mum details regarding the merger and the fact that compcomm is not ready makes me feel lost, thus I'm going to just turn it off for awhile even though it works great. Anyway does anyone have a good menu config I can use?

OT thought: [color=purple][size=5]([/size][size=3]([/size]([/color]***Quinn where are yyyyyyyooouuuuuuuuuuuuu!!!, I want my bling back..*** :( [color=purple])[size=3])[/size][size=5])[/size][/color]

---

### Post by loathsome on 2007-05-26
Nah, I love my GNOME :D I eventually use KDE as well, but GNOME is the king.

---

### Post by BLTicklemonster on 2007-05-27
> **lapsey said:**
> don't forget 
```

gtk-toolbar-style = 0 # icons only	
gtk-toolbar-style = 1 # text only
gtk-toolbar-style = 2 # both, default

```

[http://gtk.php.net/manual1/es/html/gtk.enum.gtktoolbarstyle.html](http://gtk.php.net/manual1/es/html/gtk.enum.gtktoolbarstyle.html)

Huge icons in thunar bugged me for ages before I worked it out

Can you show me a screenshot of the differences between that and using gnome settings?

---

### Post by urukrama on 2007-05-28
Have you all seen [box-look.org]("http://www.box-look.org"), the new site for window manager themes? There isn't much there yet, but if you have any IceWM themes, you can upload them there. Or search for some in the near future.

---

### Post by lapsey on 2007-06-05
> **BLTicklemonster said:**
> Can you show me a screenshot of the differences between that and using gnome settings?

They both do the same thing. 

The reason I recommend using .gtkrc is because it is lightweight compared to all the Gnome libraries etc.

---

### Post by lapsey on 2007-06-05
> **urukrama said:**
> Have you all seen [box-look.org]("http://www.box-look.org"), the new site for window manager themes? There isn't much there yet, but if you have any IceWM themes, you can upload them there. Or search for some in the near future.

Cool, It's great to finally have a place other than themes.freshmeat.net!

---

### Post by ewookie on 2007-06-27
I really love icewm.  Mainly because you can have a double-height taskbar/panel like windows.  In windows and icewm, i always use a double-height taskbar.  The upper bar for shortcuts, monitors, clocks, etc. and the lower bar for the actual taskbar (opened windows).  I would be content with XFCE4, but you can't stack it's two panels ontop of each other.

I completely agree that most icewm themes suck though.  While the config files are fairly straight-forward and self-explanatory, there's ALOT of options in those SEVERAL files.  I like to use the 'icewm control center' but it is not in the ubuntu repos and i couldn't get the source to compile (fiesty).  So...atm, i'm using XFCE4.

---

### Post by IYY on 2007-06-29
Here are some IceWM themes that don't suck:

My new [IceTunes ]("http://themes.freshmeat.net/projects/icetunes/?branch_id=70125&release_id=256104")theme, designed to look like iTunes on Windows.

My [IceBuntu]("http://freshmeat.net/projects/icebuntu/") is a theme that looks exactly like the default Ubuntu theme.

[SilverXP]("http://freshmeat.net/projects/icewmsilverxp/") is a theme that looks like Windows XP.

[IceHybrid]("http://freshmeat.net/projects/icehybrid") is a Vista-inspired theme, but uses a palette more similar to Ubuntu.

[Windows Classic]("http://themes.freshmeat.net/projects/winclassic/") looks like Windows 2000.


[Thin Black]("http://ubuntuforums.org/showthread.php?t=321994") is yet another theme developed by UbuntuForums member Albi. Looks very slick.

Truth of the matter is that IceWM is actually very easy to create themes for; the only problem is that it's not popular enough to get the designers interested.

---

### Post by dptxp on 2007-06-29
Used ICEWM in Puppy Linux, it is good for Puppy Linux, but nothing like the simplicity and
smoothness of Gnome. Navigation is at its best.

---

### Post by pseudonym on 2007-06-29
Just switched to [Openbox]("https://help.ubuntu.com/community/Openbox?highlight=%28openbox%29") for my low-power second PC (a PIII 550MHz 384MB RAM), after years of using IceWM. Ice is a cinch to set up but I find Openbox to be even faster on this machine (and it needs to be as fast as I can get it). Plus the themes for it are better looking, whereas Ice's are pretty much all as ugly as sin (sure there's Icebuntu etc., but it slows down the desktop too much for my liking).

---

### Post by Circus-Killer on 2007-06-29
well, i voted for other.

the reason is cos i used iceWM, but that was back in 97 or 98, cant remember what year, i just remember at the time i was using redhat 5.2. but after i left redhat i stopped using icewm, never seen it since, so i dont have an opinion on it because i havent seen what works been done in recent years.

man, i cant believe i started using linux close to ten years ago. its seriously feels like a couple of years.

---

### Post by TeaSwigger on 2007-10-13
EDIT: Compiled 1.3.1 and it fixed the problem I'd first posted for. Now I have a new issue:

The tray doesn't seem to be working. I can start some KDE apps with tray elements, but they won't load in the tray and in fact seem not to be starting at all. Any ideas what might cause this behavior?

---

### Post by capink on 2007-10-13
I tried icewm a year ago. I was impressed. It was light and fast. It gave me a panel and a nice run box. And it was more theme-able than other light window managers. The thing that drove me away form it was lack of support of RTL languages and Arabic text shaping. I ended up using xfwm4.

---

### Post by -grubby on 2007-10-13
I love it! It's easy to use and lightweight! But, I don't use it much

---

### Post by RAV TUX on 2007-10-13
I tried IceWM for about a month, I just removed it today.
 __________________

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=46333&d=1192382949[/IMG][/CENTER]

---

### Post by RRS on 2007-10-14
Just finished installing for a friend on an old Dell, 900MHz Celeron with 129MB of ram. Got the rest of the week to set up a usable machine for him, made a bunch of notes from this and other threads so I might have a chance!

Used a text only install from the Gutsy RC1 alternate disc to dual boot with Win98 and then added X, Icewm, etc. as advised in this thread and also used Aysiu's site for guidance.

Only had enough time to explore some files and confirm the less then attractive default theme, etc, but should be able to change that tomorrow night.

I've never used anything but Gnome before so I'm looking forward to the experience :)

---

### Post by urukrama on 2007-10-15
Is there a way to make the highlight follow the mouse in the menu (as in the menus in most DEs or WMs)? 

Now it only selects the top entry of the menu, and only moves from there if I click on another, or use the keyboard arrows to move the selection.

EDIT: I found it. I changed the MenuMouseTracking option in the preferences file.

---

### Post by urukrama on 2007-11-14
Are the IceWM diggers still around?

Is it possible to disable icons in the menus? I have deleted them all manually now, but is it possible to remove even the empty space that is left (left of the menu entry)? I looked in the preferences file, but couldn't find anything that worked.

**TeaSwigger:** I have the same issue (no system tray) on IceWM 1.3.1 but for all applications (KDE and gtk). I can place windows in the tray with "Tray Icon" option in the window menu, so there is a tray. It seems to be [a known bug]("http://sourceforge.net/tracker/index.php?func=detail&aid=1818422&group_id=31&atid=100031"), but I haven't seen a workaround yet.

---

### Post by TeaSwigger on 2007-11-15
> **urukrama said:**
> **TeaSwigger:** I have the same issue (no system tray) on IceWM 1.3.1 but for all applications (KDE and gtk). I can place windows in the tray with "Tray Icon" option in the window menu, so there is a tray. It seems to be [a known bug]("http://sourceforge.net/tracker/index.php?func=detail&aid=1818422&group_id=31&atid=100031"), but I haven't seen a workaround yet.

I was surprised to discover that the latest stable also had the same tray issue. Have to go back a couple to get a working tray. Odd. I've reverted to the vers in the Feisty repos for the time being.

For the icons in the menu, that's a good question. I have none in my custom menu, so we must be alike there. If there's no specific option perhaps one could just delete the icon directories from the icon paths option? Probably still leaves the space.

---

### Post by urukrama on 2007-11-15
> **TeaSwigger said:**
> Probably still leaves the space.

It does. There are two things that stop me from loving IceWM fully: this issue and the fact that if you launch the menu through a key combination (Alt+F1) for me, it never appears where your cursor is (as with Openbox, and Fluxbox (?)), but always at the menu icon in the taskbar (or where it should be if you don't use the taskbar). 

Otherwise IceWM is great. Very configurable. And plenty of ugly themes :D

---

### Post by jis on 2007-11-29
> **pastored said:**
> The answer is very close to you! 

There are a couple of ways of doing this, one is in your ~/.icewm/preferences file, and one would be in your ~/.icewm/menu or ~/.icewm/toolbar files.

There is a setting in the preferences file for the Shutdown command:
```
#  Command to shutdown the system
ShutdownCommand=""
```

Just type in your "sudo shutdown -h now" command in between the quotes, and restart icewm. You'll see that you now have a Shutdown option in your Logout submenu. This is the "safe" way of shutting down, because the submenu forces you to think a moment before you shut your computer down.


I have the shutdown option in the menu, but it doesn't work. Maybe because it is a sudo command. I suppose you should change system so that you can run shutdown command without sudo. I don't know how to do it, though.

---

### Post by urukrama on 2007-11-29
You can change sudo into gksudo and have a dialog coming up that asks you for your password, or you can set shutdown etc to work without adminstrative privileges.

Open a terminal and edit the sudoers file with visudo:

> sudo visudo

(It is best to edit the sudoers file with visudo, as visudo will check for possible errors before saving, thus preventing you from messing up your system)

Add the following at the bottom of the page:

> ALL     ALL=NOPASSWD:/sbin/shutdown
Save and exit, and you won&#8217;t be needing your password to reboot or shut down.

---

### Post by jis on 2007-11-29
Thanks, urukrama. Gksudo did not work for me in the preferences file, but editing the sudoers file did. I still wonder, how shutdown works in Xfce even if no change was made to the file.

---

### Post by jis on 2007-11-29
I have to add that changing the sudoers file worked only for the first shutdown, When I restarted, it does not work anymore. In terminal:
```
$ shutdown -P now
shutdown: Need to be root

```

---

### Post by aysiu on 2007-11-29
After you've edited the /etc/sudoers to not require a password for shutdown, then make the shutdown command ```
sudo shutdown -h now
```

---

### Post by urukrama on 2007-11-29
> **jis said:**
> Thanks, urukrama. Gksudo did not work for me in the preferences file, but editing the sudoers file did. I still wonder, how shutdown works in Xfce even if no change was made to the file.

As far as I've understood, they are able to communicate to GDM (or whatever login manager you use) which is run as root. Try booting into the command line and press 'startx' -- xfce or gnome will then close and you will be back at the command line when you try to shut down.

---

### Post by jis on 2007-11-29
> **aysiu said:**
> After you've edited the /etc/sudoers to not require a password for shutdown, then make the shutdown command ```
sudo shutdown -h now
```

Thanks for the hint, aysiu. I used shutdown command without sudo prefix, but with sudo it works better. I use -P option instead of -h, because I want the machine to power off. But It is an old computer so it cannot power off even with the option. Maybe it is one of these power management issues. Puppy linux can power off the computer, though.

---

### Post by aysiu on 2007-11-29
> **jis said:**
> Thanks for the hint, aysiu. I used shutdown command without sudo prefix, but with sudo it works better. I use -P option instead of -h, because I want the machine to power off. But It is an old computer so it cannot power off even with the option. Maybe it is one of these power management issues. Puppy linux can power off the computer, though.
-h seems to work fine for me to power it off. Can you explain the difference between -h and -P?

---

### Post by urukrama on 2007-11-29
I also don't know the difference between -P and -h, but did you try "**sudo halt -p**"?

(You'll need adminstrative privileges, or add "ALL ALL=NOPASSWD:/sbin/halt" to the sudoers file (similar to above)).

---

### Post by jis on 2007-11-30
> **aysiu said:**
> -h seems to work fine for me to power it off. Can you explain the difference between -h and -P?

I don't know more than "man shutdown". I suppose -P may power off some systems more completely.

In Xubuntu 7.10 I can set autostarted applications at Settings > Autostarted Applications. I can check, uncheck, remove and add applications, but I can not see what the actual command is. Does anyone know how I could autostart Print Queue Applet in IceWM?

---

### Post by jis on 2007-11-30
urukrama, the "sudo halt -p" command does not power off my computer any better than using shutdown command.

---

### Post by jis on 2007-12-01
> **aysiu said:**
> In XFCE, I hated how it was difficult to edit the applications menu and how the "maximized" windows were never really maximized.


I think it is not that hard to edit the applications menu in Xfce. You get much of the items added automatically, unlike with IceWM, when you install application. To add items to automatically created submenus manually, you have to know a trick, though: Add submenu with same name above "--- include --- system" line.

Anyway, IceWM rocks in terms of starting speed on old computers.

---

### Post by Dr Small on 2007-12-08
I use IceWM and it is awesome, I am using the VistaBlack theme, and have been using it for awhile. I also brought the wiki article up to date, as it had some older apps to install that no longer exist.

Dr Small

---

### Post by BLTicklemonster on 2007-12-09
Been looking around, and I don't think I have found anything I like better than icewm. wiamea, kde, sawfish, qvwm or whatever, you name it, IceWM is just so much more what I like than the others. 

I was really disappointed in kde and the themes I found in it. I really thought I would find all kinds of really neat stuff in it, but was totally disappointed in it. Like XP has better looking themes default than anything I found in kde.

Besides, it's the ease with which I set up icewm and edit the menus and all that makes it what I really want to use over all the other stuff.

Now if I could just figure out how to put my network on the menu so I can browse from there, I'd be a lot better off.

---

### Post by ubuntu27 on 2007-12-09
> **aysiu said:**
> 

In XFCE, I hated how it was difficult to edit the applications menu and how the "maximized" windows were never really maximized.heme, and the settings will take effect.


> **jis said:**
> I think it is not that hard to edit the applications menu in Xfce. You get much of the items added automatically, unlike with IceWM, when you install application. To add items to automatically created submenus manually, you have to know a trick, though: Add submenu with same name above "--- include --- system" line.

Anyway, IceWM rocks in terms of starting speed on old computers.

Aysiu's post was made on September 23rd, **2006**. Lots of improvements has been made in xfce since then :) 

Both of you are right. Just that he is talking about Xfce in one year ago, and you are talking about the current Xfce :D

---

### Post by Chilli Bob on 2007-12-09
Well, I spent 2 weekends on it, but have given up on IceWM.  I love it's speed, I love it's look (with the right theme that is), I love it's ease of use.  BUT - no matter what I did, it would not automount my USB sticks.  That is the same problem that caused me to leave Windows in the first place.  Now I have xfce looking nice with compiz, so I guess I'll stick with it and actually do something constructive with my PC for a change.


(Who am I kidding, I'll have fluxbox on here before dinner.  I'm a pathetic WM junky.)


Edit:  I still use IceWM on Puppy though - Vista Black theme - sweet!

---

### Post by D-EJ915 on 2007-12-09
> **Chilli Bob said:**
> Well, I spent 2 weekends on it, but have given up on IceWM.  I love it's speed, I love it's look (with the right theme that is), I love it's ease of use.  BUT - no matter what I did, it would not automount my USB sticks.  That is the same problem that caused me to leave Windows in the first place.  Now I have xfce looking nice with compiz, so I guess I'll stick with it and actually do something constructive with my PC for a change.


(Who am I kidding, I'll have fluxbox on here before dinner.  I'm a pathetic WM junky.)


Edit:  I still use IceWM on Puppy though - Vista Black theme - sweet!
well a WM will never automount anything because it has nothing to do with anything but decorating your windows...so I don't really get your point, but alright.

---

### Post by Chilli Bob on 2007-12-09
> **D-EJ915 said:**
> well a WM will never automount anything because it has nothing to do with anything but decorating your windows...so I don't really get your point, but alright.

There is supposedly a workaround using ivman and rox that will allow you to automount in IceWM.  I tried my best with what google gave me, but a lot of it was for other distros and frankly I made a mess of things.  In the end IceWM was crashing or just acting bizarre and I just had to remove it. Now I get ivman error messages when I shut down out of xfce.  It may be time for a new install.

EDIT: Maybe I'm wording this badly.  IceWM worked properly, but I couldn't get my computer to do what I wanted it to do in the IceWM environment. How's that?

---

### Post by BLTicklemonster on 2007-12-09
Isn't there just a part of nautilus you can load at start up that deals with this without bloating icewm?

---

### Post by aysiu on 2007-12-09
Can't you add *gnome-volume-manager* to the ~/.icewm/startup file?

---

### Post by jis on 2007-12-09
> **Dr Small said:**
> I use IceWM and it is awesome, I am using the VistaBlack theme, and have been using it for awhile. I also brought the wiki article up to date, as it had some older apps to install that no longer exist.

Dr Small

Thanks for updating the IceWM page in the Community Ubuntu Documentation. But I don't want to use the Microsoft Windows logo in the start menu button for GNU/Linux. I have used the Infadel2 Ergonomic theme found in icewm package by default.

---

### Post by BLTicklemonster on 2007-12-09
> **aysiu said:**
> Can't you add *gnome-volume-manager* to the ~/.icewm/startup file?

Or that. (I figured you'd come along with the right answer as always)

---

### Post by khurrum1990 on 2007-12-09
I just looked at IceWM for the first time. I don't know why, it just doesn't look as good as Dolphin or Konqueror even, thats just my opinion though.

---

### Post by -grubby on 2007-12-09
> **khurrum1990 said:**
> I just looked at IceWM for the first time. I don't know why, it just doesn't look as good as Dolphin or Konqueror even, thats just my opinion though.

iceWM is a WM. Dolphin and Konqueror are file managers

---

### Post by jis on 2007-12-09
> **jis said:**
> I think it is not that hard to edit the applications menu in Xfce. You get much of the items added automatically, unlike with IceWM, when you install application.

Aysiu, in your  [Modest Spec or Barebones Installation of Ubuntu page]("http://www.psychocats.net/ubuntu/minimal") you instruct to include menu package, but how does it help you to generate menus in icewm?

---

### Post by Dr Small on 2007-12-09
[quote=jis]Thanks for updating the IceWM page in the Community Ubuntu Documentation. But I don't want to use the Microsoft Windows logo in the start menu button for GNU/Linux. I have used the Infadel2 Ergonomic theme found in icewm package by default.[/quote]

Dear Jis, that is just a screenshot of my desktop using the VistaBlack theme, of which I listed down below on the wiki. The theme is not default. I was just simply showing a screenshot of my desktop.

And as for the windows logo, I got Vista Blues and copied the Ubuntu start menu icon over to Vista Black so now I have Ubuntu logo for the start button instead of Windows Vista :D

Dr Small

---

### Post by jis on 2007-12-09
Some people tend to start same application many times by clicking on toolbar, since the cursor does not change as a sign. This is problem especially with heavy applications and slow computers. Of course, CPU graph and hard disk noise are feed back as well, but changing the cursor icon would be more noticeable, I think. I suppose this is better handled in Xfce. IMO best thing would be, if you could open heavy applications in the background so that they would not pop up, but appear minimized, instead.

---

### Post by Dr Small on 2007-12-09
It really doesn't bother me... Usually people who use IceWM are geeks with low system specs, and just want something lightweight that isn't going to get in their way. They know how to use the terminal, so cursor icons changing wouldn't be a big benefit or advantage to them....

---

### Post by jis on 2007-12-09
Dr Small, there are also some non-geek users that don't want to invest in brand new computer.

For me windows popping up are getting in my way sometimes.

BTW. I would like to see screenshot of your "Vista Blues" theme.

---

### Post by Dr Small on 2007-12-09
Here is the thread:
[http://ubuntuforums.org/showthread.php?t=360145&highlight=vista+blues](http://ubuntuforums.org/showthread.php?t=360145&highlight=vista+blues)

In the Vista\ Blues/taskbar/ directory is a image called icewm.xpm, and that is the image I replaced on Vista Black to get the little Ubuntu start menu image.

Dr Small

---

### Post by D-EJ915 on 2007-12-09
> **jis said:**
> Dr Small, there are also some non-geek users that don't want to invest in brand new computer.

For me windows popping up are getting in my way sometimes.

BTW. I would like to see screenshot of your "Vista Blues" theme.
screencap: [http://dej915.serveftp.com:777/mine/screencaps/IceWM_vista_blues.jpg](http://dej915.serveftp.com:777/mine/screencaps/IceWM_vista_blues.jpg)

---

### Post by Dr Small on 2007-12-09
Would someone please explain to me, how you get a second task bar ?
I see people with two, but I don't know how to do it... It must be something simple.

Dr Small

---

### Post by Darkhack on 2007-12-09
I'm glad this thread was bumped up.  I recently tried IceWM just a couple weeks ago and am now addicted.  Extremely lightweight, but still has plenty of features and it is easy to use.  I've fallen in love and I don't think I can go back.

The only downside I've seen is that when I run KDE or GNOME programs, sometimes, even after exiting the application, they still have some of their desktop processes sitting around in memory;  gnome-settings-daemon for example as well as kded and all the kio crud.

---

### Post by jis on 2007-12-10
> **Dr Small said:**
> Would someone please explain to me, how you get a second task bar ?


I can't tell, but I love to use vertical panel in Xfce especially, if I have many windows open, since the taskbar does not get messy of windows of same applications: When I hover an item, I get vertical list of titles of windows of that application. I don't know, if any other wm handles it as well..

---

### Post by ago on 2007-12-10
Did anybody try LXDE?

It is based on IceWM and looks really interesting:

[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

---

### Post by khurrum1990 on 2007-12-10
> **nathangrubb said:**
> iceWM is a WM. Dolphin and Konqueror are file managers
Oh yeah sorry.

---

### Post by timpino on 2007-12-10
> **ago said:**
> Did anybody try LXDE?

It is based on IceWM and looks really interesting:

[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

it seems interesting...

on a side note: if they need someone to clean up the english on their homepage, I would be glad to help :)

---

### Post by edemark on 2007-12-11
Hi all

I read through this thread after setting up my old laptop (p2 365 mhz with 128mb ram) with xubuntu and icewm using xfdesktop in icewm to manage the desktop and to have xfce menu. My only problem is that without killing explicitly xfdesktop i cannot log out of icewm. 
Is there any way to do that so? I tried writing a logoff script to get it executed on logout it does work but it does not kill xfdesktopand thus i cannot log out. Any idea how to solve this?

pd now i have a menu item killing xfdesktop (killall xfdesktop) and that way it works but i would like to get a better solution.
thanks

---

### Post by BLTicklemonster on 2007-12-11
Best thing I've found for gaming so far is JWM. Unreal Tournament starts almost immediately when I run it in JWM.

---

### Post by el_ricardo on 2007-12-11
I use iceWM on my laptop because its so lightweight, but at the same time (with a lot of effort) it looks ok! my laptop is ancient, it doesn't even run xfce smoothly, so i had to learn how to make iceWM look presentable!

on a half decent PC i'd choose KDE or xfce any day though, because they're so much simpler to work with tbh!

---

### Post by BLTicklemonster on 2007-12-11
Yes, indeed, I have a Dell Latitude 510, and though ubuntu gnome runs fine, I like it better with icewm. I used to use fluxbox alot, but recently, I haven't touched it. I'm trying to explore other stuff right now to see what other WMs there are to use, and to see if they are near as good as IceWM has been for me.

---

### Post by Albi on 2007-12-12
Just made these themes the past week, enjoy:
[http://box-look.org/content/show.php/KDE4?content=71528](http://box-look.org/content/show.php/KDE4?content=71528)
[http://box-look.org/content/show.php/True+Vista?content=71347](http://box-look.org/content/show.php/True+Vista?content=71347)

---

### Post by BLTicklemonster on 2007-12-12
Great looking stuff, Albi!

---

### Post by aysiu on 2007-12-12
> **Albi said:**
> Just made these themes the past week, enjoy:
[http://box-look.org/content/show.php/KDE4?content=71528](http://box-look.org/content/show.php/KDE4?content=71528)
[http://box-look.org/content/show.php/True+Vista?content=71347](http://box-look.org/content/show.php/True+Vista?content=71347)
Your IceWM themes are *phenomenal* and the main reason I stick with IceWM instead of going back to Gnome or KDE. 

Thanks for all your hard work!

---

### Post by Darkhack on 2007-12-12
I agree!  Those themes are incredible!  I installed both of them.  Thanks for your work.

---

### Post by -grubby on 2007-12-12
> **Albi said:**
> Just made these themes the past week, enjoy:
[http://box-look.org/content/show.php/KDE4?content=71528](http://box-look.org/content/show.php/KDE4?content=71528)
[http://box-look.org/content/show.php/True+Vista?content=71347](http://box-look.org/content/show.php/True+Vista?content=71347)

> **aysiu said:**
> Your IceWM themes are *phenomenal* and the main reason I stick with IceWM instead of going back to Gnome or KDE. 

Thanks for all your hard work!

nice themes! and thanks Aysiu for your tutorial on how to install them.

---

### Post by BLTicklemonster on 2007-12-12
I have just found and installed something pretty cool that you all might want to look at. It's called Look Win XP IceWM.

[http://sourceforge.net/projects/lxp/](http://sourceforge.net/projects/lxp/)

---

### Post by jis on 2007-12-14
Strangely, I don't get all Firefox windows opened when launching firefox after reboot even if I have "Show my windows and tabs from last time" selected in firefox preferences. Actually, I don't even have to reboot: logout and login is enough.

---

### Post by jis on 2007-12-14
[Bug #176338]("https://bugs.launchpad.net/ubuntu/+source/icewm/+bug/176338")

---

### Post by Dr Small on 2007-12-17
> **Albi said:**
> Just made these themes the past week, enjoy:
[http://box-look.org/content/show.php/KDE4?content=71528](http://box-look.org/content/show.php/KDE4?content=71528)
[http://box-look.org/content/show.php/True+Vista?content=71347](http://box-look.org/content/show.php/True+Vista?content=71347)
Absolutely gorgeous themes. I am using the Ultra Real Vista theme right now. I love it :D

---

### Post by Oldster on 2007-12-19
> **Dr Small said:**
> Would someone please explain to me, how you get a second task bar ?
I see people with two, but I don't know how to do it... It must be something simple.

Dr Small

Double height task bar maybe?

In the IceWm preferences file set as follows:

```

#  Use double-height task bar
# TaskBarDoubleHeight=0 # 0/1
TaskBarDoubleHeight=1

```

then restart IceWM.

---

### Post by Sir Nose on 2007-12-22
Icewm was the second window manager I tried back in '98, when I was starting with Linux (I had Red Hat 6.1 or 6.2). The first one was fvwm which was configured to look like Windows 95 :D
I liked icewm back then, and it was the one I used the most. I currently have it as default wm in my old box. It makes a pretty nice combination when used with rox.

---

### Post by K.Mandla on 2007-12-25
In hopes of better organizing all the window manager and desktop environment threads, this has been shifted to Desktop Environments.

---

### Post by erginemr on 2007-12-25
> **K.Mandla said:**
> In hopes of better organizing all the window manager and desktop environment threads, this has been shifted to Desktop Environments.

Thanks a million. I was looking for a secondary / backup desktop environment to my Gnome setting for a long time and did not find Fluxbox to my taste. Having installed IceWM based on your advice and decorated it with a few nice themes, I am very happy with its look and performance so far. 

Thanks again.

---

### Post by Hairy_Palms on 2007-12-25
i like icewm, its my seconday window manager on my hary box for when gnome screws up, also i use it as th actual wm on my ancient laptop.

---

### Post by simd on 2007-12-31
I really like IceWM, having been introduced to it via Xandros on my EEE PC. It's light, customisable and does everything I want it to.

I think the biggest barrier are the default settings. When you install KDE or Gnome, all the menu options are set up and they look pretty good. When you install ICEWM, you get an ugly interface, terrible themes and a mostly irrelevant menu.

I appreciate that a script has been set up to help people do this customisation, but wouldn't it be great if the default icewm install in ubuntu did this for you? Is this possible, without setting up a whole new distribution? Could we create an icewm-desktop package which installs the necessary and (possibly) default options such as rox? 

Or should we consider creating an ICEWM distribution? My personal feeling is, for many people on low powered machines, it would be a better option than XUbuntu.I'd be very happy to help, within my limited ability!

---

### Post by aysiu on 2007-12-31
I've had that same feeling, but I don't really have the knowledge (or willpower necessary to acquire the knowledge) to make an IceWM metapackage or a remastered IceWM Ubuntu version (like Fluxbuntu).

The only IceWM distribution I know of is Puppy Linux, and their package management kind of stinks in comparison to Ubuntu.

I'd be fully behind a good IceWM metapackage.

---

### Post by jamaisvu on 2008-01-01
> **aysiu said:**
> I'd be fully behind a good IceWM metapackage.

[FONT=Franklin Gothic Medium]Me too -- it might prove the solution to the problem of making that antique laptop with 64MB RAM good for use as anything more than a doorstop.[/FONT]

---

### Post by BLTicklemonster on 2008-01-01
Icebuntu, huh? Sounds like a great idea. I wonder why no one has done this yet? If there's a fluxbuntu, then surely ...

---

### Post by jis on 2008-01-03
Puppy Linux uses JWM by default: 
[http://puppylinux.org/wikka/JoesWindowManager]("http://puppylinux.org/wikka/JoesWindowManager")

Ubuntulite used to use IceWM; nowdays it uses Openbox: [http://ubuntulite.tuxfamily.org/?q=node/4]("http://ubuntulite.tuxfamily.org/?q=node/4")

---

### Post by urukrama on 2008-01-06
For those of you who hadn't seen it yet: **Icewm 1.2.35** is out.

Not much has changed, though. From the changelog:

> **1.2.35: 2008-01-05**
        - Application tray bug fixes
        - Add encoding/language to about dialog
(and from the previous version release a week earlier)
**1.2.34: 2007-12-27**
	- fix gmplayer switching to fullscreen
	- popup dialog focus fixes
	- fix screen change with xrandr 1.2

Icewm testing 1.3.2 has also been released.

Downloads are [here]("http://sourceforge.net/projects/icewm/").

---

### Post by ljsmithx on 2008-01-06
Would installing IceWM break my gnome apps?

---

### Post by urukrama on 2008-01-06
No. You will just get an extra sessions menu at the login screen (F10 > Sessions). You can use Icewm alongside Gnome, and you can use gnome-apps in Icewm.

---

### Post by simd on 2008-01-06
Some time ago Aysiu posted a script to this thread which enables an easy IceWM install for Ubuntu. I've written to him asking if I can post an upgraded version of the script, which will make "upgrading" Ubuntu to IceWM as easy as running the script, and will make IceWM look good and include the necessary defaults. Depending on the status of 1.3.2, it could possibly use the very latest version of IceWM too. 

More soon, I hope.

---

### Post by BLTicklemonster on 2008-01-06
You know, there's this really nice gnome desktop wallpaper I really like, and have used as my wallpaper in IceWM for a long time

[[IMG]http://img106.imageshack.us/img106/4067/gnomefinestdesktopgs0.th.png[/IMG]](http://img106.imageshack.us/my.php?image=gnomefinestdesktopgs0.png)

but I got to thinking, and I wanted a nice IceWM wallpaper.

So I made one 

[[IMG]http://img153.imageshack.us/img153/156/icewmdesktopnj0.th.png[/IMG]](http://img153.imageshack.us/my.php?image=icewmdesktopnj0.png)


Okay, I made two

[[IMG]http://img106.imageshack.us/img106/4572/icedwmwallpaperea0.th.png[/IMG]](http://img106.imageshack.us/my.php?image=icedwmwallpaperea0.png)


welcome to the ice age!

So now I can run IceWM and not feel like I'm driving a Guinness Stout truck while drinking Heineken. 

Oh, and what is the command in preferences to make the desktop wallpaper stretch to fill the screen, and why is it on a new install, the preferences in /usr/share/icewm doesn't have all the stuff it had in it in the olden days? I used to could just look in there and find all kinds of useful commands. Or am I looking in the wrong place as usual? I bet I am, lol.

---

### Post by simd on 2008-01-07
Looks great! If it's ok with you, I might include this in the IceWM configuration script I'm pulling together.

---

### Post by cheahk on 2008-01-07
Me too.  I use icewm on my old notebook.  Before with gnome, it used to swap so much with 256MB of RAM, and with ice, it's barely swapping.

-K

---

### Post by BLTicklemonster on 2008-01-07
Heck yeah, have at it! I wouldn't post an image on the net if I didn't expect someone might want it for their own use some day. I'd just hope they wouldn't ever say, "look what I did", of course. :) The Gnome one was someone else's original work, of course. I got it from a screenshot of someone's desktop, and made my own background from it, so I can't claim it as mine.


*Edit: 

On second thought, let me redo that. I didn't do shadows of the icecicles, and it just doesn't look right.

Oh, and the image of the mountain isn't mine, of course. i got it off the interetardnet, so I can't really say that it's an "all mine" image.

---

### Post by Albi on 2008-01-08
Yet another theme I made:
[http://box-look.org/content/show.php/FauxGlass?content=73238](http://box-look.org/content/show.php/FauxGlass?content=73238)

Enjoy

---

### Post by BLTicklemonster on 2008-01-09
Nothing in synaptic on tar.tg, and the only site I see online that says how to open one in linux is a gay pay to view expert site.

So I like your theme, please change the download to a common file type? tar.gz or something, please?

We had a dude at our forums who would make stuff and use some off the wall compression and no one could open his files. Took me forever to convince him to use .zip. He said used what he did because he was saving like 5 kb per meg. Ooookay.

So how do I open a tar.tg?

lmao, renamed it to tar.gz

---

### Post by Takmadeus on 2008-01-09
dunno.... I kinda like IceWM but windowmaker is the king of da' house ;)

---

### Post by fade_out on 2008-02-25
I solely use Icewm along with idesk and the IceNine theme. I've used all the other window managers/desktop environments and keep coming back to Ice, tho fluxbox is also good and fast.

---

### Post by solarwind on 2008-02-25
> **fade_out said:**
> I solely use Icewm along with idesk and the IceNine theme. I've used all the other window managers/desktop environments and keep coming back to Ice, tho fluxbox is also good and fast.

I'm going to try out IceWM. I've used it before on DamnSmallLinux but never really thought about it...

---

### Post by fade_out on 2008-02-26
> **Albi said:**
> Yet another theme I made:
[http://box-look.org/content/show.php/FauxGlass?content=73238](http://box-look.org/content/show.php/FauxGlass?content=73238)

Enjoy

Just seen you created the theme I'm using and would like to say thanks for your great work.

---

### Post by BLTicklemonster on 2008-03-22
Can gdesklets' starterbar be set to load automatically in icewm?

---

### Post by erginemr on 2008-03-22
> **BLTicklemonster said:**
> Can gdesklets' starterbar be set to load automatically in icewm?
This may help:
[http://gentoo-wiki.com/HOWTO_Autostart_Programs#IceWM](http://gentoo-wiki.com/HOWTO_Autostart_Programs#IceWM)

---

### Post by BLTicklemonster on 2008-03-23
> **erginemr said:**
> This may help:
[http://gentoo-wiki.com/HOWTO_Autostart_Programs#IceWM](http://gentoo-wiki.com/HOWTO_Autostart_Programs#IceWM)

Thanks, but I already tried that

gdesklets &

will load it, but I still have to manually set up my startbar every time. I tried setting a profile, but that doesn't do any good.

---

### Post by erginemr on 2008-03-23
Please consider this as a brain exercise, rather than a tried and tested method: 

I believe you want to use gdesklet startbar with IceWM, because you like to use MacOS-like deskbars (a la AWN) with the speed and simplicity of IceWM. Having largely been influenced by this thread started by **aysiu**, I also have been using IceWM as secondary to my Gnome desktop and am happy with it.

AWN (as well as Kiba-Dock and Cario-Dock) cannot be used in IceWM environment, because it needs a compositing manager such as Compiz Fusion, which IceWM does not support. However, as you may already know, there is a tool called **xcompmgr** providing pseudo-compositing capabilities to a number of desktops.

[http://wiki.archlinux.org/index.php/Xcompmgr](http://wiki.archlinux.org/index.php/Xcompmgr)

Out of curiosity, I had disabled Compiz once, downloaded and run xcompmgr, and then avant-window-navigator, and it worked, but did all that in Gnome, not in IceWM. So, I suggest you to look into the possibility of using AWN together with xcompmgr under IceWM.

---

### Post by BLTicklemonster on 2008-03-23
Oooh, no way, awn is totally buggared. Besides, I have been able to get the starter bar to come up at start in fluxbox, but haven't messed with that in ages, but want to use icewm with it now. And yes, gdesklets works fine with icewm, it's just that I can't get starterbar to load automatically already set up the way I want it.

As far as wanting a mac os type deskbar... I dunno, bro, I just like the way gdesklet's startbar looks.

---

### Post by x1a4 on 2008-03-23
I've tried IceWM from time to time, but never stuck with it, finding XFCE, AfterStep and FVWM-Crystal much better.  Recently, however I installed IceWM again, tweaked it a bit and decided that with some more tweaking it can be a pretty cool GUI.  Screenshot of my current setup attached.

---

### Post by BLTicklemonster on 2008-03-23
Finally figured it out.

I had my startup like this:

numlockx &
#idesk&
gnome-volume-manager &
gnome-settings-daemon &
#conky &
xbindkeys &
lomoco &
gdesklets start &

and the gnome stuff was messing gdesklets up, so I did this:

numlockx &
#idesk&
[COLOR="Red"]#gnome-volume-manager &
#gnome-settings-daemon &[/COLOR]
#conky &
xbindkeys &
lomoco &
gdesklets start &

and now gdesklets startbar comes up exactly how I had it before.

---

### Post by jis on 2008-03-24
1) Task grouping option for taskbar
2) Option to open a GUI app in background, no pop-up stealing focus.

---

### Post by x1a4 on 2008-03-24
> **jis said:**
> 2) Option to open a GUI app in background, no pop-up stealing focus.

You can change that by copying the file /usr/share/icewm/preferences to ~/.icewm/ and looking through the settings.  There are many settings related to raising and focusing windows and their dialogues.

---

### Post by fparri on 2008-04-28
Anyone knows how can I minimize an application so it goes in the try, in icewm. Whenewer I "close" skype or gajim they should finish in the tray, but no icon to restore them appears, while they're still working (I can see them with ps -aux).

Sorry for my bad English :)

---

### Post by urukrama on 2008-04-28
What version of icewm are you using? There was a bug in the system tray in earlier versions. Icewm 1.2.35 fixed that.

To find out what version you are running, type the following in a terminal:
> icewm --version

---

### Post by fparri on 2008-04-28
I have hardy's one, 1.2.33. Do you know if there's any 1.2.35 deb file available?
Otherwise, I might also want to check if I correctly launched icewmtray. This might be another of the reasons why it isn't working. I'll let you guys  know.

Thanks a lot, meanwhile :)

---

### Post by urukrama on 2008-04-28
> **fparri said:**
> I have hardy's one, 1.2.33. Do you know if there's any 1.2.35 deb file available?
Otherwise, I might also want to check if I correctly launched icewmtray. This might be another of the reasons why it isn't working. I'll let you guys  know.

Thanks a lot, meanwhile :)

I don't think there is a deb package for Icewm 1.2.35 available, but you could download the [source code]("http://sourceforge.net/project/showfiles.php?group_id=31") and compile that.

For more info on the system tray bug, read [this]("http://sourceforge.net/tracker/index.php?func=detail&aid=1818422&group_id=31&atid=100031").

---

### Post by fparri on 2008-04-28
Thanks a lot! If I recompile it, which doesn't seem too difficult, do I have to remove the previous installation, first? I imagine so, but not sure about that ;)

---

### Post by urukrama on 2008-04-29
You could, but it will probably be fine if you don't. I don't think I removed the old version when I upgraded. You'll have to restart icewm to use the new version, though.

---

### Post by fparri on 2008-04-29
In the end it seems I won't need compiling the new version, since I found out the reason of my problems... I didn't have icewmtray in my .xinitrc

The tray bugs solving in the latest version refers to another problem, which luckily, I'm not experiencing on my box (at least, a bug I'm not experiencing! LOL)

Thanks a lot for your help.

PS. May I ask if you guys can also suggest me a no-fat lightweight volume mixer application to use (and which can reside in the tray, since it's working now... ;) ?

Thanks a lot,
Fabio

---

### Post by urukrama on 2008-04-29
Glad it was solved. 

For a volumen control system tray: try [gvtray]("http://code.google.com/p/gtk-tray-utils/") or [this]("http://david.chalkskeletons.com/blog/?p=20") modification of it. [This post]("http://urukrama.wordpress.com/2007/12/19/managing-sound-volumes-in-openbox/") might also be useful for you.

---

### Post by fparri on 2008-04-29
Cool, thanks I'll check it ;)

---

### Post by Muni Beduhin on 2008-05-02
I like IceWm a lot. It's pager feature is weak, but I just started using Blackbox's pager (about 5 minutes ago). I like the fact that you can change themes from the main menu. I love the fact that it is very light without being ugly or puny. I like the way that it is easily themable--it took me about 10 minutes to tweak the SilverXP theme up by changing the "Start" button--I borrowed, with slight modifications (through Gimp), the "Start" button with Tux on it from the blue XP theme. I like how easy to understand the configuration files are. I like how easy it is to install themes. IceWM is a very good system--seems like not very many Linux distros, even the light ones, come with it by default. Well, maybe yours truly will remedy that some day...

---

### Post by Mark76 on 2008-06-06
I've been using IceWM for the best part of a week now. I like the ridiculously easy configuration (even though you do have to do it in text files, at least you don't have to do it in ancient Geek :D ). After much tweaking this is what I've got (see screenshots). I took the pager out of the taskbar because I don't really use virtual desktops (never have enough windows open to get them confused. Plus the Window List Menu makes them *virtually* superfluous) and moved it to the top of the screen ala OSX. I added the cairo-dock as a place to store launchers for my favourite/most used apps. Disappointed I can't have transparency, though; that black bar that pops up when you mouse over the dock is really annoying.  For file and backdrop management I'm using pcmanfm :). The IceWM theme is Elegance.

Couple of points, First one of which goes way back in the thread. Rox does have a navigation bar. You just press / and there it is.

And secondly, Whoever was asking about GUIs for changing the window theme. Did you ever consider GTK-Chtheme?

---

### Post by BLTicklemonster on 2008-06-07
Looks good! I tried cairo-dock just now, and it's nice, but I don't like the default launchers stuffed down my throat, and I can't find a way to simply put a launcher I want on the dock. Probably a notch past simple so I missed it, eh?

Seems like there ought to be a file somewhere one could edit to change the image used for the background (that black mass) and make it transparent. You'd think that everyone making these docks would make that an upfront standard option.

---

### Post by Mark76 on 2008-06-07
> **BLTicklemonster said:**
> Looks good! I tried cairo-dock just now, and it's nice, but I don't like the default launchers stuffed down my throat, and I can't find a way to simply put a launcher I want on the dock. Probably a notch past simple so I missed it, eh?

I'll say it is.  Just click on the dock, choose "Add A Launcher" and a filer window opens directly into /usr/share/app-install.  Just use the buttons at the top to navigate to /usr/share/applications and then choose your launcher (click on the desktop file). Viola!

> Seems like there ought to be a file somewhere one could edit to change the image used for the background (that black mass) and make it transparent. You'd think that everyone making these docks would make that an upfront standard option.

Yeah. That'd be nice.

---

### Post by BLTicklemonster on 2008-06-07
Oh.

:)

I just edited the properties of evolution and another couple of launchers to what I wanted: k3b, k9copy, exaile, etc. Now to put a couple of launchers up there, then edit them to Unreal Tournament and UT Cache Cleaner, muahahahaha. 

If only I could get rid of that stupid blackdrop. That actually makes the whole dock rather ugly. Course I could use a black wallpaper, but I like the icewm one I made the best.

---

### Post by bill-linux on 2008-06-12
In regards to making a deb for 1.2.35 version in order to solve the problems with the tray. You can make a "backport" deb from intrepid (the next version of Ubuntu coming out ... it has 1.2.35 ... see [http://packages.ubuntu.com/intrepid/icewm](http://packages.ubuntu.com/intrepid/icewm)).

To make a backport follow the directions at

[http://ubuntuforums.org/showthread.php?t=268687](http://ubuntuforums.org/showthread.php?t=268687)

Note:

- You can just install prevu with sudo apt-get install prevu

- Note line 2 when the author mentions changing souces.list -- in this case it should read "intrepid" where that one reads "feisty" (You make a back port from the next new version of Ubuntu ... at the time that was written fiesty was the new one!)


- After (or before) you create your backport deb remove all versions of icewm ... to see which ones type "dpkg -l | grep icewm"

- Install the new debs which will be in /var/cache/prevu/hardy-debs -- you can install them with this command:

sudo dpkg -i {name of new deb}

I had four to install: icewm, icewm experimental, icewm-gnome and icewm-common ... icewm-common had to be installed first.

As always with a backport your are on your own and you can break your system. I just did this a half hour ago and icewm appears to work fine.

---

### Post by Mark76 on 2008-06-22
Does anyone have any bespoke IceWM splash themes I can borrow?

I looked on gnome and box look, but I couldn't find any.

---

### Post by BLTicklemonster on 2008-06-22
I used to have a bespeckled one, but then I realized I'd just blew coffee out my nose on the monitor after reading funny post. Cleaned right up, didn't leave any stains.

---

