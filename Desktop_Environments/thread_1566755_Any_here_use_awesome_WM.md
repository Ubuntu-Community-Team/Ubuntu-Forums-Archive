---
title: "Any here use awesome WM?"
date: 2010-09-02
forum: Desktop Environments
---

### Post by DemonBob on 2010-09-02
I've been wanting to play around with the idea of switching to a tiling wm. So i started up virtual box and installed Ubuntu minimal, then installed awesome, gdm, terminator, Firefox, gedit, and a few other trinkets.

What i would like to know, is their any other programs that work good, and look decent in awesome. I switched to terminator from gnome-terminal because i like the look of terminator better when it is in awesome. 

Also, is their any distro that use awesome by default, i may be able to play around with or get ideas from? 

Post some screen shots, i'm interested in how everyone else is set up. Once, i get mine set up to fit me, i'm going to remastersys it, and use it on my production machine.

---

### Post by DuncanR on 2010-09-03
I use Awesome on my development machine at work. It's a Mac Pro so I have to compile it with macports (along with xorg, etc). Essentially I find it to be incredible productive, at least much more so that the normal OS X environment. Being able to split the screen up and organise things across tags quickly and efficiently is very powerful if you have dozens of terminals open, gvim, firefox, etc. Also, I prefer to do as much as possible via the keyboard so it suits my work-flow, and it 'integrates' very well with terminals (I like instances of rxvt) and vim.

I don't really customise the default setup much, except for defining hot keys for launching all my commonly used apps (command-f for firefox, command-v for vim, command-enter for terminal etc).

---

### Post by Spice Weasel on 2010-09-03
I do and love it. :) 

I use "Fair" for my open mrxvt terminals, so they tile equally. Just looks neater imo, have another specific tag (or "Virtual Desktop") for "Fair" and all of the rest are set to "Floating" (Like most WMs.). I honestly now find window borders pointless. Saves a lot of screen space too. :D

Be prepared to have to do a hell of a lot of Googling and RTFMing, though.

Default colours, but that's because I like them.

Screenshots:

[http://i52.tinypic.com/2druna8.png](http://i52.tinypic.com/2druna8.png)

[http://i51.tinypic.com/2zqfuxw.png](http://i51.tinypic.com/2zqfuxw.png)

[http://i55.tinypic.com/156x01l.png](http://i55.tinypic.com/156x01l.png)

---

### Post by DemonBob on 2010-09-03
Nice. 

I went-a-head and installed awesome on my production box, and am running in in place of gnome-wm. I'm liking it so far. I've always been more comfortable with not using the mouse. 

Still have a lot of customizing to go. Been spending the last few hours setting up rules in rc.lua for where and how my programs open.

---

### Post by Spice Weasel on 2010-09-03
Nice setup, I recommend you get a bottom panel though. Just makes everything neater.

---

### Post by DemonBob on 2010-09-03
I have both gnome panels on autohide at the moment, until i get use to it. Once i do, i'm removing the top panel.

---

### Post by Nythain on 2010-09-04
> **DemonBob said:**
> I've been wanting to play around with the idea of switching to a tiling wm. So i started up virtual box and installed Ubuntu minimal, then installed awesome, gdm, terminator, Firefox, gedit, and a few other trinkets.

What i would like to know, is their any other programs that work good, and look decent in awesome. I switched to terminator from gnome-terminal because i like the look of terminator better when it is in awesome. 

Umm... should use an rxvt, terminator is overkill since awesome can tile anyways and well, part of the beauty of awesome is not having window decorations and all that jazz, just my two cents though

other important apps
gtk-chtheme for changing the gtk theme
i use Geany over gEdit but thats a personal preference
crap, i dont know, in tiling window managers i use mostly ncurses apps like weechat for irc, mutt for mail, canto for news, htop, slurm, tty-clock, calcurse, cursetheweather, moc, you get the point...
Just about any lightweight GTK app for what you need will work though
> 
Post some screen shots, i'm interested in how everyone else is set up. Once, i get mine set up to fit me, i'm going to remastersys it, and use it on my production machine.Here's a link to my WMFS desktop (wich is borderline exactly what awesome used to be before it went all lua on me and decided to break its rc.lua every release)

[http://nythain.deviantart.com/#/d2xfakj](http://nythain.deviantart.com/#/d2xfakj)

ps, smooth work on your awesome setup so far, impressive

---

### Post by roggenschrotbrot on 2010-09-22
i switched to awesome two weaks ago when i got my hand injured so i don't want to use a mouse atm. love it so far, but if using xcompmgr the menus aren't drawn properly, most of the time the menu elements stay invisible until mouseover. it would be nice if anybody could provide any suggestions or workarounds on this.

wip:
[[IMG]http://img844.imageshack.us/img844/9193/awesomeshot.th.png[/IMG]](http://img844.imageshack.us/i/awesomeshot.png/)

---

### Post by ~LoKe on 2010-11-02
I tried to get Awesome up and running again but I'm not really having any luck.  I don't have the patience right now to go through all of the config to set the thing up the way I like it.

Sad part is that I wrote one of the original guides for compiling and configuring Awesome 2.1.  They just keep changing the damn thing so nothing I have can ever port over.

What's this rc.lua crap?  Grr..things seem to have gotten over complicated.

---

### Post by oarion7 on 2011-05-19
> **roggenschrotbrot said:**
> i switched to awesome two weaks ago when i got my hand injured so i don't want to use a mouse atm. love it so far, but if using xcompmgr the menus aren't drawn properly, most of the time the menu elements stay invisible until mouseover. it would be nice if anybody could provide any suggestions or workarounds on this.

wip:
[[IMG]http://img844.imageshack.us/img844/9193/awesomeshot.th.png[/IMG]](http://img844.imageshack.us/i/awesomeshot.png/)

I am having the exact same problem. Anyone know a fix?

EDIT: So my issue (it may not have been the exact same thing, but I think it's pretty close) was that if I included xcompmgr in my session startup script, or in any script included within that script, or if I set it to run within my rc.lua, no matter in what order I put my startup apps, xcompmgr would cause the AwesomeWM status bar at the top of the screen to flicker for a second and then completely disappear right after Awesome loaded. I would then have to either open a window or dialogue for my bars to appear, or I would have to wait about 60 seconds, and they would finally show up on their own... 

After quite a bit of searching I found another non-WM-bound compositing manager, cairo-compmgr. If I use this instead, I do not have this issue. Perhaps you don't mind giving this app a try instead (or at least in the mean time, until you find a fix for xcompmgr). If you are used to and fond of the simplicity of xcompgr, you may want to run **cairo-compmgr -c** early on in order to disable some of the settings and plugins (I turned them all off for now). Personally, I don't want any effects on my normal windows, just the ability for specific programs to call for certain effects (e.g. transparency of terminal window or an irc client).

I am using Lucid and downloaded these packages intended for Debian sid, no issues so far:

[http://cairo-compmgr.tuxfamily.org/download/debian-packages/](http://cairo-compmgr.tuxfamily.org/download/debian-packages/)

Using this compositing method in place of xcompmgr has enabled me to boot into a properly appearing and working desktop clean and simple.

---

### Post by roggenschrotbrot on 2011-05-19
> **oarion7 said:**
> I am having the exact same problem. Anyone know a fix?

replacing xcompmgr with xcompmgr-dana fixed this issue for me.

---

### Post by oarion7 on 2011-05-19
> **roggenschrotbrot said:**
> replacing xcompmgr with xcompmgr-dana fixed this issue for me.

Thanks. Cairo-compmgr was giving me some buggy results, and xcompgr-dana didn't resolve the issue I was having. I managed to fix it by delaying the startup script by a few seconds longer than I had tried before. Felt silly for not having tried that before getting into this mess. Anyway, my issue is resolved now, too. Thanks again for the recommendation.

---

