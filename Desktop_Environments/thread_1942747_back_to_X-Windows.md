---
title: "back to X-Windows ???"
date: 2012-03-18
forum: Desktop Environments
---

### Post by ohnonot on 2012-03-18
Hello,

I wonder if it's possible to install some kind of simple X-Windows desktop environment as might have been 10 years ago.

I *do not* want to install the complete OS, but rather as a session option at the login menu: Plain X.

mostly for curiosity, but the idea comes from a particular wish of mine:
i like the old x-fonts very much and would love to use them system wide.
i started [another thread]("http://ubuntuforums.org/showthread.php?p=11774936#post11774936") on that.
plus, i like true minimal.

Is it possible?
What would work? What would not?

ps: i've seen threads "a day without X" - that's not what i'm looking for!

---

### Post by siepo on 2012-03-18
You can install some of the plain window-managers such as fvwm, icewm or openbox. They should appear as session options. Also install menu, which generates menus for them.

And install old-fashioned versions of applications which still use the old fonts, such as the xterm- or rxvt[-unicode] terminal emulators.

---

### Post by 3Miro on 2012-03-18
[https://wiki.archlinux.org/index.php/Xorg](https://wiki.archlinux.org/index.php/Xorg)

Xorg comes with default environment that can hardly be any more bare than that. Technically, you an set your own environment by specifying which programs to run at start. If you don't list something like a Windows Manager, then you will be stuck with the default Xorg environment.

---

### Post by 2F4U on 2012-03-18
You can get the feeling without installing anything with the WindowMaker liveCD:

[http://news.softpedia.com/news/Introducing-the-Window-Maker-Live-CD-258136.shtml](http://news.softpedia.com/news/Introducing-the-Window-Maker-Live-CD-258136.shtml)
[http://wmlive.sourceforge.net/](http://wmlive.sourceforge.net/)

---

### Post by ohnonot on 2012-03-18
wow, lots of nice answers.
:popcorn:
appreciated.

the Xorg-wiki seems worth looking at, also the window maker live cd.
and i will try to install some old window manager, see what happens.

see you soon.

---

### Post by gutterslob on 2012-03-24
Not quite "10 years ago" but you'll probably want to look at tiling window managers. Also install bitmap/fonts, grab a lightweight, modular terminal emulator (like rxvt-unicode) and research CLI alternatives for your regular programs. 

Here's an example of what you can get running on my netbook. Aside from the web-browser everything is a CLI/terminal app.

[[img]http://ompldr.org/tYzBhag[/img]](http://ompldr.org/vYzBhag)

---

### Post by ohnonot on 2012-03-26
> **gutterslob said:**
> Not quite "10 years ago" but you'll probably want to look at tiling window managers. Also install bitmap/fonts, grab a lightweight, modular terminal emulator (like rxvt-unicode) and research CLI alternatives for your regular programs. 

Here's an example of what you can get running on my netbook. Aside from the web-browser everything is a CLI/terminal app.

[[IMG]http://ompldr.org/tYzBhag[/IMG]]("http://ompldr.org/vYzBhag")this looks very nice.
and you still have all the graphical abilities, like watching movies and browsing the net?
what is this setup, what am i seeing there? basically 3 terminal windows running non-graphical apps?
2 totally minimalized panels? or is it conky?
what is the wm and desktop environment?

and i love the colors. 

and yes, i am intersted in tiling wm's. any suggestions to start with (meaning not *yet *giving up xfce)?

---

### Post by mexicanseaf00d on 2012-03-26
> **2F4U said:**
> You can get the feeling without installing anything with the WindowMaker liveCD:

[http://news.softpedia.com/news/Introducing-the-Window-Maker-Live-CD-258136.shtml](http://news.softpedia.com/news/Introducing-the-Window-Maker-Live-CD-258136.shtml)
[http://wmlive.sourceforge.net/](http://wmlive.sourceforge.net/)

that looks pretty good :)

---

### Post by gutterslob on 2012-03-26
> **ohnonot said:**
> and you still have all the graphical abilities, like watching movies and browsing the net?Yes. Web-browsing, Flash (if installed), Mplayer, Gimp (in single-window mode), Inkscape all work like normal. Only difference is that they're tiled instead of floated. Check wikipedia for an explanation on "tiling window manager" if you're unsure what it means. Basically, other than the way they're arranged, all GUI apps should work fine on most tiling window managers with little configuration.

 
[quote=ohnonot]what is this setup, what am i seeing there? basically 3 terminal windows running non-graphical apps? 2 totally minimalized panels? or is it conky?[/quote] 4 terminals actually. One on the right is running Vim (editor). Bottom-left is running ncmpcpp, a front-end for mpd (music player daemon). On top of that is just a script to display your custom terminal colorscheme (Xdefaults/Xresources) and in between those 2 is a small,  manually floated/resized terminal showing the prompt. The panel on top is the included bar, with conky-cli output piped into it.


[quote=ohnonot]what is the wm and desktop environment?[/quote]I'm using [SpectrWM]("https://opensource.conformal.com/wiki/spectrwm") (formerly known as scrotwm).


[quote=ohnonot]and i love the colors. [/quote]Thank you.


[quote=ohnonot]and yes, i am intersted in tiling wm's. any suggestions to start with (meaning not *yet *giving up xfce)?[/quote]That would be tricky, the "not yet giving up xfce" bit. Thing is, do you really need/want tiling? It works for me but might not work for you. From your initial post, it seems you want a pixel-sharp old-skool geek-pr0n look with bitmap fonts all around. You can achieve that with any window manager. Here's an old [example]("http://crunchbanglinux.org/forums/post/72528/#p72528") of mine while running a window manager called Openbox. You could probably even mimic that look in Xfce, but I wouldn't know how since I haven't used xfce in a long time. There's also a chance you could replace xfwm (xfce's window manager), but I'm not sure how well other window managers integrate into xfce. If you are enticed by the concept of tiling and want a tiling window manager, I wouldn't recommend SpectrWM. It's a bit too minimal, you won't get a systray for starters. Why not try [i3wm]("http://i3wm.org/"). It comes with tabs and systray support, the configuration file is human-readable and there's extensive documentation available on the site. 


One thing to note: Unlike desktop environments (Gnome, KDE, Xfce), most stand-alone window managers, whether floating (Openbox, Fluxbox, PekWM, Compiz...etc) or tiling (AwesomeWM, dwm, scrotwm, spectrwm, i3wm, xMonad... etc) require some amount of configuration/config file editing to get working. Whether it's worth your time or not is your decision to make.

Cheerz

---

### Post by lykwydchykyn on 2012-03-26
> **ohnonot said:**
> Hello,

I wonder if it's possible to install some kind of simple X-Windows desktop environment as might have been 10 years ago.

I *do not* want to install the complete OS, but rather as a session option at the login menu: Plain X.

mostly for curiosity, but the idea comes from a particular wish of mine:
i like the old x-fonts very much and would love to use them system wide.
i started [another thread]("http://ubuntuforums.org/showthread.php?p=11774936#post11774936") on that.
plus, i like true minimal.

Is it possible?
What would work? What would not?

ps: i've seen threads "a day without X" - that's not what i'm looking for!

Ten years ago we still had KDE, GNOME, and XFCE. :)

If you want a good dose of old-school, you need to try FVWM.  There's really no such thing as "plain X".

---

### Post by efball3 on 2012-03-28
> **lykwydchykyn said:**
> 
If you want a good dose of old-school, you need to try FVWM.  There's really no such thing as "plain X".

twm is the closest thing to "plain X", but it's pathetic. I started with twm in the '80s on HP-UX.  I switched to motif for a while, then VUE, but I found fvwm when I started using Linux (RedHat 4.2 in 1997) and I've been using fvwm ever since.  Its an excellent WM for machines without much RAM.  It probably has the best configurability/size ratio you can get.  fluxbox is another good choice.  I had been using gnome 2 for a while on my desktop, keeping fvwm for some older machines, but with the introduction of unity/gnome 3 I went back to fvwm full time.

tiling window managers look interesting.  I may have to give one a try, but I don't think I'd ever fully switch over.

---

### Post by lykwydchykyn on 2012-03-29
> **efball3 said:**
> 
tiling window managers look interesting.  I may have to give one a try, but I don't think I'd ever fully switch over.

I used to think I wouldn't switch, but once you go tiling, you never want to go back.  I started using awesome on my laptop last summer, and now I'm using it on my work computer.  You never realize how much manual window management you've been doing until you don't have to do it anymore. :D

---

### Post by ohnonot on 2012-03-30
> **gutterslob said:**
> Yes. Web-browsing, Flash (if installed), Mplayer, Gimp (in single-window mode), Inkscape all work like normal. Only difference is that they're tiled instead of floated. Check wikipedia for an explanation on "tiling window manager" if you're unsure what it means. Basically, other than the way they're arranged, all GUI apps should work fine on most tiling window managers with little configuration.

4 terminals actually. One on the right is running Vim (editor). Bottom-left is running ncmpcpp, a front-end for mpd (music player daemon). On top of that is just a script to display your custom terminal colorscheme (Xdefaults/Xresources) and in between those 2 is a small,  manually floated/resized terminal showing the prompt. The panel on top is the included bar, with conky-cli output piped into it.

I'm using [SpectrWM]("https://opensource.conformal.com/wiki/spectrwm") (formerly known as scrotwm).

That would be tricky, the "not yet giving up xfce" bit. Thing is, do you really need/want tiling? It works for me but might not work for you. From your initial post, it seems you want a pixel-sharp old-skool geek-pr0n look with bitmap fonts all around. You can achieve that with any window manager. Here's an old [example]("http://crunchbanglinux.org/forums/post/72528/#p72528") of mine while running a window manager called Openbox. You could probably even mimic that look in Xfce, but I wouldn't know how since I haven't used xfce in a long time. There's also a chance you could replace xfwm (xfce's window manager), but I'm not sure how well other window managers integrate into xfce. If you are enticed by the concept of tiling and want a tiling window manager, I wouldn't recommend SpectrWM. It's a bit too minimal, you won't get a systray for starters. Why not try [i3wm]("http://i3wm.org/"). It comes with tabs and systray support, the configuration file is human-readable and there's extensive documentation available on the site. 

One thing to note: Unlike desktop environments (Gnome, KDE, Xfce), most stand-alone window managers, whether floating (Openbox, Fluxbox, PekWM, Compiz...etc) or tiling (AwesomeWM, dwm, scrotwm, spectrwm, i3wm, xMonad... etc) require some amount of configuration/config file editing to get working. Whether it's worth your time or not is your decision to make.

Cheerzthanks for all that input. took me a while to reply. i downloaded scrotwm from the depositories. (could not compile or use spectrwm from git. not quite acquainted with git.) very intersting. but since it treats xfdesktop and conky as normal windows it requires configuration + getting used to new ways of navigating and seeing things.

some other wm's i've downloaded. some come with their own sessions, some work quite well from within xubuntu session...

i guess i'll try around some more and mayb i find sth that suits me.
i had a fluxbox distro earlier (and was using blackbox on windows) - it's really nice.
actually i think one reason why i didn't stick with it was that i could never find a decent standalone desktop manager. oh yes, and the almost total lack of gui. fiddling around with config files all the time. never the option to just tick/untick a box or choose from a dropdown.(*1)

my "back to X" is mostly a graphical thing.
also i'm not ashamed to admit that i just *love* the combination of old school graphics plus full compositing.(*2)

some insights about fonts [here]("http://ubuntuforums.org/showthread.php?p=11794003#post11794003").

(*1) plus a community that loves exactly that (inventing the wheel over and over). plus, not being able to use this software and that utility because it's designed for a different DE.

(*2) well, not necessarily exactly like that. i mean *stylish and minimalistic *and not *puritan.*

---

### Post by ohnonot on 2012-09-24
just coming back to this thread to say i finally tried out wmlive - it's great.
check this: ubuntuforums.org/showthread.php?p=12257296

---

