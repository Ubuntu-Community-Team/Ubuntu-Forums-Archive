---
title: "AwesomeWM or Tiling WM Users Unite!"
date: 2010-12-11
forum: Desktop Environments
---

### Post by DemonBob on 2010-12-11
So who here also uses awesomewm, or a tiling window manger? I've been using awesome for about 6 months at home, and started using it recently at my new job on my desktop at work. 

Weather it's at work or home, I've noticed that a tiling WM has increased my productivity 10 fold. I'm able to organize everything by tag, then tile. With awesomewm I have come to love it's reliainace on the LUA language. If I need a new feature, I can add it pretty easily. 

I.E. I have created custom prompts with some scripting to rdp and ssh into box's with the login information, resolution, already inputed. Put in some if/else in there also, for certain hostnames that require different credentials, or different settings. It also mounts the c$ or root drive once connected to my /ticket/##### directory. So it's a snap to copy any file over. 

With LUA i've been pretty much able to extend the window manger to my needs with any script I can imagine. 

So come on everyone, discus! Wether you are using awesomewn, or dwn or another great tiling window manager. Post your code, your settings, lets make this thread as big as the conky thread. 

I will post a screen shot Monday, and my rc.lua code. :) 

-- DemonBob
-- Overly Enthusiastic Tiling Window Manger User
-- DISCLAMER: I may have been a little tipsy when writing this post.

---

### Post by DemonBob on 2010-12-16
bueller... bueller?

---

### Post by roggenschrotbrot on 2010-12-17
using awesome for a few months now, and loving it.
[[img]http://www.abload.de/thumb/2010-12-16-103442_1440dnn5.png[/img]](http://www.abload.de/image.php?img=2010-12-16-103442_1440dnn5.png)
[[img]http://www.abload.de/thumb/2010-12-16-103541_14405uqy.png[/img]](http://www.abload.de/image.php?img=2010-12-16-103541_14405uqy.png)
i have some cleaning to do before i post my rc.lua though, its a total mess atm.

---

### Post by DemonBob on 2010-12-19
Nice, heres mine so far. 

[http://systemoverload.net/images/awesome_desktop.png](http://systemoverload.net/images/awesome_desktop.png)

In the process of re-working the theme this week.

---

### Post by jadonchristensen on 2011-01-10
Video of Bluetile - [http://www.bluetile.org/](http://www.bluetile.org/)

Bluetile is available in the Ubuntu Software Center.

---

### Post by Simian Man on 2011-01-10
> **DemonBob said:**
> ... the LUA language.

Please.  It's "Lua", not "LUA".

---

### Post by jadonchristensen on 2011-01-10
For anyone wanting to know where you can change your Window Manager after installing one...

System > Administration > Login Screen
Unlock
Select [name of manager] as default session
Close

When you logout, you should be able to select the Window Manager that you want to use at the bottom of your screen.

Ok, I am really liking Bluetile because it has several modes that allow me to snap windows, tiles, etc. I wish there was a way to hide the main Bluetile bar though.

---

### Post by 0nelove on 2011-01-19
anybody having success building from 3.4.9 stable?
[http://awesome.naquadah.org/download/](http://awesome.naquadah.org/download/)
rather than hijack this thread, I posted separately here:
[http://ubuntuforums.org/showthread.php?t=1670945](http://ubuntuforums.org/showthread.php?t=1670945)

---

### Post by leohart on 2011-02-15
Bluetile bar can be removed by editting your ~/.bluetilerc

---

### Post by ceti331 on 2011-10-10
i love the idea of the tiling WM's but have never got used to the hotkey layout on something like awesome, I'm always stumbling around with it.
tiles + tabs are a very interesting combination IMO, something like the lower screen edge being minimized window 'taskbar' and each pane having some windows in tabs would be a great way to work IMO, I think 'ion3' was a bit like this but not quite. 
I can't get used to anything that starts out with the VI mentality for hotkeys hjkl ..

i did get used to the brief text editor years ago, and could see myself learning something like that, e.g. if every switching/spatial type action was associated with the cursor keys (say win+cursor = move focus, just move offscreen to make/select new desktop, then chords like win+something then cursor to split current pane, etc etc)

i also find a lot of the gui apps seem to have strong preference for landscape or portrait, if they were all better at re-configuring themselves to different layouts as dictated by the tiling WM that would be better

---

### Post by markMDW on 2012-02-05
I'd like to learn about window managers and their configuration and am envisioning a project using Ubuntu or other major distribution as a base.  Then, I'd like the escape the PC paradigm (windows cascading everywhere, dialog boxes galore, having to spend half the productive time figuring out where the window or dialog box is that you need) and create something that boots into a custom appliance or kiosk like interface.   I want everything in its proper place and the computer to serve a special purpose that I define and setup.

It sounds like Awesome fits the bill.

It looks like Lua is similar to Python.  Is it relatively easy to learn?  I'm not a computer science major and know a little bit of scripting, and next to nothing about designing GUIs.  

I can imagine a system with several workspaces.  

One workspace would be tiled into four or so sections including one small section that handles a scrolling dialog interface, basic html rather than as the dialogs pop up prompt then ask [ok] or [cancle] ..ect.   it could be tabbed like a modern browser so that the user could just see just the application and user response, or alternately the entire message.  Another section would have a scrolling list of RSS feeds.  Another would have computer system functions like file manager, clock, system resources.   Another would have browser linked to the RSS, and another tile would have a text editor like Gedit.

Another workspace would have a place to run any other applications that are installed and could be cascading, or tiled in a way that the tiles could be easily dockable and adjustable (if not cascading).

Perhaps another workspace would offer terminals or the console and might be locked except to the administrator.  Also, considering that I'm not a programmer (but do know a little scripting with Python, JavaScript, and some of the OOP theory behind Java and Python)  I wouldn't be able to tackle complex GUI like programming, I don't think.  

Any recommendations on a good windows manager to tinker around with?

If everything were to go exceptionally well I'd like to have a custom Ubuntu based, special purpose distributions.  For instance one that focuses on Public Media RSS feeds for schools.  Or, other distributions customized for any other institutions special needs.  They'd like to have a computer that focuses on themselves rather than does anything, everything but nothing very well.  Thanks for any advice..  Mark 

Could Awesome handle a lot of these ideas?

---

### Post by ladadi on 2012-05-21
markMDW: Sounds a little bit like Awesome, not sure how you would do the notification stuff. Sounds to me it's more of a separate app than something the WM would do, but then again, it's not impossible.

About Lua, I don't really know what I'm doing, but it works, googling+guessing solves most issues (kind of like python ;)). I'm not a programming guru but I do work with languages such a matlab, ncl and fortran in my job.

I've been using Awesome for work since Oneiric came out, and its nice and efficient, once you've done all that customizing.  But if you're like me, you'll end up wasting all that saved time on customizing even more.  Anyway, having workspaces set up for specific tasks is great.

What I found most annoying when I started out with awesome was the gtk-themes.  With gtk3 this was even worse.
fix?
I installed from Xubuntu and let xfsettingsd handle the themes (works much better than e.g. gnome-settings-daemon for some reason).

Give Awesome a try you'll like it!
as for the alternatives, I've heard Xmonad is quite awesome as well.

Anyhow, I'm currently trying to get some awesome stuff working (see screenshot).
I want to set up a launch script that puts a document viewer as master window and tiles to slave terminals.  One of the terminals will be dedicated to vim-latex (big one) and the other will be used to run latex+bibtex (~5 rows).
Why not just use vim-latex for compiling documents?
Well, it doesn't run bibtex (maybe there a way to do this, I don't know) and I prefer to have one thing going on in each terminal. That's were tiling window managers get useful: Do many things without hiding them in the background.
The problem?
I haven't figured out how to resize the slave windows with cli, so I have to resize by hand, instead of having that awesome script which launches, arranges and resizes all in one go.

Anyone have any suggestions?

---

