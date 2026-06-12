---
title: "Can Ubuntu do this?"
date: 2010-02-10
forum: Desktop Environments
---

### Post by Zornox on 2010-02-10
I had no Idea where to put this question, So I figured it would be a good place for Desktop Environments. 

Any ways, The question is that, Is there any way for Ubuntu to do what Windows 7 does. What I mean by that is, When you take a window and you drag it to the left or right, It Maximize's the whole entire window to half of the screen or what ever. I hope you understand what I'm saying. I"m just wanting to know if you can get Ubuntu to do something like that. 

Thanks.

---

### Post by blur xc on 2010-02-10
The only thing that I know that is similar, is the maximumzie plugin in compiz.  It's not exactly the same, but you can maximize a window to some portion of the screen.  It's pretty handy and I use it quite a bit.

BM

---

### Post by Zornox on 2010-02-10
> **blur xc said:**
> The only thing that I know that is similar, is the maximumzie plugin in compiz.  It's not exactly the same, but you can maximize a window to some portion of the screen.  It's pretty handy and I use it quite a bit.

BM

Well I have Compiz, and It is working Properly, So how can I find this plugin, in the manager?

---

### Post by blur xc on 2010-02-10
if you haven't already, search in synaptic (or add remove programs or the software center) for compiz config settings manager - OR enter

```
sudo aptitude update && sudo aptitude install compizconfig-settings-manager
```into your terminal.

(if you copy it from this post, use ctrl-shift-v to paste it to the terminal)

Then I think you will find it under system -> preferences.

[http://www.youtube.com/watch?v=j_CJhdynfTE](http://www.youtube.com/watch?v=j_CJhdynfTE)

BM

---

### Post by Zornox on 2010-02-10
> **blur xc said:**
> if you haven't already, search in synaptic (or add remove programs or the software center) for compiz config settings manager - OR enter

```
sudo aptitude update && sudo aptitude install compizconfig-settings-manager
```into your terminal.

(if you copy it from this post, use ctrl-shift-v to paste it to the terminal)

Then I think you will find it under system -> preferences.

[http://www.youtube.com/watch?v=j_CJhdynfTE](http://www.youtube.com/watch?v=j_CJhdynfTE)

BM

Well Why thank you, But It says something about Pushing the "super" + M on the keyboard. WHen I do that, My screen the color of it goes to the Negative color and when I push them both again, it goes back to normal. Is there a reason why its doing this?

---

### Post by 3Miro on 2010-02-10
From System -> Prefs -> Compiz Config Manager, you have to set up the corresponding effects. Currently you have the "negative" effect set up and it is associated with Meta + M. You will have to set up the maximizing effect yourself (check the corresponding box).

---

### Post by warp99 on 2010-02-10
Sure it can for the longest time. You have to have the CompizConfig Settings Manager (CCSM) installed. Once that's done make sure you have the "Grid" plugin turned on. Then use your keys ctrl+alt+key pad(KP) numbers 1 thru 9 to place the window that has focus in any location you want. Side by side vertical or horizontal, opposite corners, four windows at a time, your name it. When I saw Microsoft advertising this "feature" I almost fell out of my chair since I was laughing so hard.

Edit: Also by pressing the KP again you can resize the window further so in reality you can fit up to 6 windows on a grid.

---

### Post by falconindy on 2010-02-10
Yet another solution:

[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

But really, why all the workarounds to do something that tiling WMs have been doing flawlessly for nearly 2 decades now?

---

### Post by blur xc on 2010-02-10
> **falconindy said:**
> Yet another solution:

[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

But really, why all the workarounds to do something that tiling WMs have been doing flawlessly for nearly 2 decades now?

Make us a tiling WM that doesn't look like it was created by a 14 yr old kid in his parent's basement, and doesn't require hours of configuring by editing plain text files, without a steep learning curve, them maybe we'll start using them.

Even openbox, as nice at it is, when you install a new program it doesn't automatically get added to the applications menu.  It has to be done manually.  It's pain...  But at least there's a gui menu editor.

BM

---

### Post by kamitsukai on 2010-02-10
> **blur xc said:**
> 
Even openbox, as nice at it is, when you install a new program it doesn't automatically get added to the applications menu.  It has to be done manually.  It's pain...  But at least there's a gui menu editor.

BM

Just thought I'd point at that many see this as a feature rather then a flaw :D if you want it to add applications automatically then you can use a pipe menu such as debian

---

### Post by falconindy on 2010-02-10
> **blur xc said:**
> Make us a tiling WM that doesn't look like it was created by a 14 yr old kid in his parent's basement, and doesn't require hours of configuring by editing plain text files, without a steep learning curve, them maybe we'll start using them.

Even openbox, as nice at it is, when you install a new program it doesn't automatically get added to the applications menu.  It has to be done manually.  It's pain...  But at least there's a gui menu editor.

BM
Last I checked, people are using tiling WMs like XMonad and DWM on top of environments like Gnome, replacing the bloatware that is Compiz. 

So what if applications menus dont dynamically update? You should be using a launcher like Gnome-Do or dmenu, which does (and makes a lot more sense).

You can have your wobbly-windowed, 13-sided desktop cube painted with flames (zomg so fast). I'll be getting some work done.

---

### Post by Neodarkness on 2010-02-10
Openbox is really nice, very clean and simple. Highly open in it's configuration options, doesn't hide stuff from you.
Anyway, back on topic:

If you don't want compiz on your sys, and don't feel like a Tilling WM, you can use Pytyle. It tyles windows and is very easy to use.

---

### Post by blur xc on 2010-02-11
> **warp99 said:**
> Sure it can for the longest time. You have to have the CompizConfig Settings Manager (CCSM) installed. Once that's done make sure you have the "Grid" plugin turned on. Then use your keys ctrl+alt+key pad(KP) numbers 1 thru 9 to place the window that has focus in any location you want. Side by side vertical or horizontal, opposite corners, four windows at a time, your name it. When I saw Microsoft advertising this "feature" I almost fell out of my chair since I was laughing so hard.

Edit: Also by pressing the KP again you can resize the window further so in reality you can fit up to 6 windows on a grid.

I can't believe it's taken me so long to discover the grid plugin.  Thanks for the tip!

BM

---

### Post by blur xc on 2010-02-11
> **falconindy said:**
> Last I checked, people are using tiling WMs like XMonad and DWM on top of environments like Gnome, replacing the bloatware that is Compiz. 

So what if applications menus dont dynamically update? You should be using a launcher like Gnome-Do or dmenu, which does (and makes a lot more sense).

You can have your wobbly-windowed, 13-sided desktop cube painted with flames (zomg so fast). I'll be getting some work done.

I'm open for being proven wrong.  Prove to me that a tiling WM will improve my productivity (even though I don't "work" per se, on my home computer) over  my current compiz setup.  And no, I don't run a 13 sided "cube". Mine's got 3, and it's a cylinder.  3 works out nice, because every workspace is only one away from the one I'm on.

From other posts in this forum, I understand that compiz only takes like 20mb of ram.  Hardly bloat ware...

And dynamically updating menus was just an example-  I actually like openbox but I like using my computer more than I like configuring it.

BM

---

### Post by falconindy on 2010-02-12
Compiz and other non-tiling window managers create an environment that requires extensive use of the mouse -- clicking icons, navigating menus, resizing and moving windows. You're forced into a situation that requires 2 input devices rather than one, and you're constantly switching between the two.

Tilers, on the other hand, create an environment where everything is centered on the keyboard. You absolutely do **not** need a mouse to work at 100% effectiveness in a tiler. In addition, windows use maximum real estate at all times, relieving you of the manual job of window managing. Removal of a mouse from the equation means switching between applications is fluid, causing minimal interruption in your workflow. Navigation within programs is just as quick and easy. This does, of course, require the cooperation of said programs.

</soapbox>

Personally, my enjoyment of a tiling WM increased greatly when I got my hands on an HHKB. If you look at the truly hardcore tiling WMs (such as RatPoison), you'll find an abundance of HHKBs and other high end keyboards. [Side note: using a HHKB for the past 3 months has ruined my ability to use a text editor other than Vim, and has severely hampered my ability to type on a regular keyboard. However, I do not regret it.]

I'll propose the theory that perhaps it takes a certain mindset to be "attuned" to the idea of a tiling WM. When I ditched Windows and moved to Gnome, I felt like I was recreating my Windows desktop. I moved to Linux explicitly to get **away** from Windows. Linux, to me, is a programmer's haven. I wanted an interface that supported this. That's where tilers come in.

Another admission: moving to a tiling WM has made me somewhat of a purist, despite my computer's resources not limiting me to such (C2D with 2gb of RAM). My tiler of choice, DWM, is under 2000 lines of source code and comandeers a whopping 1.5mb of RAM with a half dozen windows open. It does exactly what I need and no more. I do my best to adhere to the Unix philosophy whenever possible. My mention of "bloatware" refers to the idea of using software that does far more than you'll ever want/need it to do.

---

### Post by syncmasterpt on 2010-02-12
> **Zornox said:**
> I had no Idea where to put this question, So I figured it would be a good place for Desktop Environments. 

Any ways, The question is that, Is there any way for Ubuntu to do what Windows 7 does. What I mean by that is, When you take a window and you drag it to the left or right, It Maximize's the whole entire window to half of the screen or what ever. I hope you understand what I'm saying. I"m just wanting to know if you can get Ubuntu to do something like that. 

Thanks.

YES, KDE 4.4 SC does that and much more. If using Gnome, I think you're out of luck.

---

### Post by blur xc on 2010-02-12
> **falconindy said:**
> Compiz and other non-tiling window managers create an environment that requires extensive use of the mouse -- clicking icons, navigating menus, resizing and moving windows. You're forced into a situation that requires 2 input devices rather than one, and you're constantly switching between the two.

Tilers, on the other hand, create an environment where everything is centered on the keyboard. You absolutely do **not** need a mouse to work at 100% effectiveness in a tiler. In addition, windows use maximum real estate at all times, relieving you of the manual job of window managing. Removal of a mouse from the equation means switching between applications is fluid, causing minimal interruption in your workflow. Navigation within programs is just as quick and easy. This does, of course, require the cooperation of said programs.

</soapbox>

Personally, my enjoyment of a tiling WM increased greatly when I got my hands on an HHKB. If you look at the truly hardcore tiling WMs (such as RatPoison), you'll find an abundance of HHKBs and other high end keyboards. [Side note: using a HHKB for the past 3 months has ruined my ability to use a text editor other than Vim, and has severely hampered my ability to type on a regular keyboard. However, I do not regret it.]

I'll propose the theory that perhaps it takes a certain mindset to be "attuned" to the idea of a tiling WM. When I ditched Windows and moved to Gnome, I felt like I was recreating my Windows desktop. I moved to Linux explicitly to get **away** from Windows. Linux, to me, is a programmer's haven. I wanted an interface that supported this. That's where tilers come in.

Another admission: moving to a tiling WM has made me somewhat of a purist, despite my computer's resources not limiting me to such (C2D with 2gb of RAM). My tiler of choice, DWM, is under 2000 lines of source code and comandeers a whopping 1.5mb of RAM with a half dozen windows open. It does exactly what I need and no more. I do my best to adhere to the Unix philosophy whenever possible. My mention of "bloatware" refers to the idea of using software that does far more than you'll ever want/need it to do.

Ahh - I now see your flaw in reasoning.  You are making the assumption that EVERYONE's use case would benefit from using the mouse less.

That's great if you spend all your time doing CLI type activities.  Back in my dos 5 days using word perfect, I could fly once I memorized all my keyboard shortcuts.  If you do a lot of typing, coding, etc., I can fully understand how this would be faster.  But if one's use case REQUIRES a lot of mouse clicking, then keeping one hand on the mouse save a ton of effort.

Use GIMP or any other graphics program.  I can have a bunch of images open at the same time, use my mouse to make selections and adjustments, right click on the edge of my screen to initiate the scale plugin, select another image, and continue working - fast - smooth - efficient.

Maybe to educate me further, you can explain how one browses the net efficiently w/o a mouse?

A lot of times (I know this doesn't work for many people) I have to use the computer w/ just one hand.  We have a baby in the house, sometimes he's needing to be held, and I don't have a free left hand to put on the keyboard.  My wife breast feeds while using the computer- she's become ambidextrous w/ the mouse...  How well would a tilling wm work then?

But- when I'm on the command line, I use terminator, vi, and park the mouse...

Tiling WM's and compiz have their place...

For my normal day's computer use, keeping the left hand on the keyboard and the right hand on the mouse, is most efficient.

BM

---

### Post by falconindy on 2010-02-12
Again, your programs need to work with your setup. Unfortunately, Windows set the standard long ago for mouse-based interfaces and so that's what the majority of software developers create, without giving it a second though. Those accustomed to Windows moving to Linux will look for similar software, as that's what they're used to. Or, perhaps they're not aware of the "dark side".

You cannot expect a mouse-centric setup to just work immediately as keyboardless simply by virtue of switching your window manager. In response to your query about web browsers: Uzbl, elinks, Vimprobable, Vimperator, w3m, etc. I use apvlv for PDF viewing, ncmpcpp for music, mplayer from a terminal, the console interface for Deluge, GNU coreutils for file management, and many of my own scripts to replace other day to day functions (backups, system monitoring, maintenance, and administration). While I still use word processing, I could switch to LaTeX. Spreadsheet apps are actually surprisingly keyboard friendly on their own.

It's unfortunate, imo, that many users prefer software that looks good over an equivalent solution that's easier to use but may not look as polished. Case in point: Vim (with its vertical learning curve) does everything and more than every other text editor I've ever used in the past 10 years combined. This includes EditPlus, NotePad++, GEdit, and Geany.

I will happily admit that there are many programs for which a full keyboard replacement is not possible -- graphical design being the most obvious. However, I notice that many folks who are into this realm have, again, ditched the mouse in favor of a more natural input device: a pen and tablet.

People have gone as far as to adapt one handed keyboard layouts. Throw Dvorak, Colemak and QWERTY to the wayside -- they go their own route. A bit of an extreme scenario, but it happens more often than you think.

[http://ratpoison.antidesktop.net/wiki/Keyboard_Gallery](http://ratpoison.antidesktop.net/wiki/Keyboard_Gallery) (rcyeske-kbd in particular)
[http://www.geekhack.org](http://www.geekhack.org)

---

### Post by blur xc on 2010-02-12
> **falconindy said:**
> Again, your programs need to work with your setup. Unfortunately, Windows set the standard long ago for mouse-based interfaces and so that's what the majority of software developers create, without giving it a second though. Those accustomed to Windows moving to Linux will look for similar software, as that's what they're used to. Or, perhaps they're not aware of the "dark side".

You cannot expect a mouse-centric setup to just work immediately as keyboardless simply by virtue of switching your window manager. In response to your query about web browsers: Uzbl, elinks, Vimprobable, Vimperator, w3m, etc. I use apvlv for PDF viewing, ncmpcpp for music, mplayer from a terminal, the console interface for Deluge, GNU coreutils for file management, and many of my own scripts to replace other day to day functions (backups, system monitoring, maintenance, and administration). While I still use word processing, I could switch to LaTeX. Spreadsheet apps are actually surprisingly keyboard friendly on their own.

It's unfortunate, imo, that many users prefer software that looks good over an equivalent solution that's easier to use but may not look as polished. Case in point: Vim (with its vertical learning curve) does everything and more than every other text editor I've ever used in the past 10 years combined. This includes EditPlus, NotePad++, GEdit, and Geany.

I will happily admit that there are many programs for which a full keyboard replacement is not possible -- graphical design being the most obvious. However, I notice that many folks who are into this realm have, again, ditched the mouse in favor of a more natural input device: a pen and tablet.

People have gone as far as to adapt one handed keyboard layouts. Throw Dvorak, Colemak and QWERTY to the wayside -- they go their own route. A bit of an extreme scenario, but it happens more often than you think.

[http://ratpoison.antidesktop.net/wiki/Keyboard_Gallery](http://ratpoison.antidesktop.net/wiki/Keyboard_Gallery) (rcyeske-kbd in particular)
[http://www.geekhack.org](http://www.geekhack.org)

How do you display graphical web content in elinks?  I've tried elinks and I didn't get very far.  I could barely figure out how to navigate this forum.  I couldn't see what the benefit was for every day use.  I would like to know how to use it, in the case of a crashed gui- to still be able to get online and search for a fix if need be...  I've seen the vimperator addon for firefox but haven't tried it...  maybe I will...

I guess a big part of the problem is learning curve.  There are a lot of programs that I might need to use on occasion, maybe for a 10min or even a 1hr task- so what would I use?  A fast, powerful, efficient application but has a 10hr learning curve, or one that's slow, clunky, limited, but gets what I need done w/o needing to really spend any time reading up on how to use it (windows movie maker, for example).  That's especially true if I won't need to use it again any time soon.  

I understand, if it's something you will use very frequently - but how often do I write something up in a word processor?  Once a month maybe?  

vim on the other hand, I get.  I'm just a beginning vim user, but it's a great program.  Like I said, if I have to use it, I'm probably already in the terminal.  Terminator splits windows, so it's like having my terminal session tiled- and I get that.  I'm trying to learn a bit of python and bash scripting- and in those cases, it makes a great deal of sense to keep both hand on the keyboard.

And I did try a normal US Dvorak keyboard layout once, and it made my hands cramp up.  Old habits are hard to break.

BM

---

