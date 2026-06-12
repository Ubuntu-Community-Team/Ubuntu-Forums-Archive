---
title: "[SOLVED] Use Metacity with Gutsy"
date: 2008-02-19
forum: Desktop Environments
---

### Post by Bruce M. on 2008-02-19
I have Compiz turned off:
[LIST]
[*]System>Preferences>Appearance
[*]Visual Effects: None
[/LIST]
However Compiz is still my "*window manager*" *See image.*
[CENTER]
[[IMG]http://img227.imageshack.us/img227/3371/compizhe0.th.png[/IMG]](http://img227.imageshack.us/my.php?image=compizhe0.png)
[/CENTER]

And I think it's stopping my conky from displaying automatically at startup.
Keep in mind I have an OLD computer (See my Sig.)

So two questions:
[LIST=1]
[*]What damage will it to to Gutsy if, through Synaptic, I "Mark for Complete Removal" everything "Compiz"?
[*]How do I go about making **Metacity** my **"Default"** window manager?
[/LIST]

***Note:*** Metacity is installed, just not running I think. :confused:

Thanks
Bruce

---

### Post by steeleyuk on 2008-02-19
1. None, removing Compiz will not cause any problems.
2. Metacity should be the default fallback if Compiz is not running.

If you want to run Metacity, the command is:

metacity --replace

---

### Post by Bruce M. on 2008-02-19
> **steeleyuk said:**
> 1. None, removing Compiz will not cause any problems.
2. Metacity should be the default fallback if Compiz is not running.

If you want to run Metacity, the command is:

metacity --replace

I knew about the replace command but not sure if it is/was "permanent".

I'll replace then remove compiz.

---

### Post by Bruce M. on 2008-02-19
[LIST=1]
[*]What damage will it to to Gutsy if, through Synaptic, I "**Mark for Complete Removal**" ***[COLOR="Red"]everything[/COLOR]*** "Compiz"?
[*]How do I go about making **Metacity** my **"Default"** window manager?
[/LIST]


> **steeleyuk said:**
> 1. None, removing Compiz will not cause any problems.
2. Metacity should be the default fallback if Compiz is not running.

If you want to run Metacity, the command is:

metacity --replace

[CENTER]
[SIZE="4"]**[COLOR="Red"]Warning[/COLOR]**[/SIZE]
While **"Mark for Complete Removal" *[COLOR="Red"]everything[/COLOR]*** "Compiz"

**May work for you.**
It did **[COLOR="Red"]NOT[/COLOR]** work for me!
I'm in the process of installing 186 Security Updates as I had to re-install Gutsy
[/CENTER]

Then I'll have to re-install:
[LIST=1]
[*]Conky
[*]Curl
[*]Lm-sensors - and set it up again
[*]Thunderbird
[*]Thunar
[*]jPilot - and set it up again
[*] and a few more
[/LIST]

**So the question still applies:**
[LIST=1]
[*]How do I go about making **Metacity** my **[COLOR="Blue"]"Default"[/COLOR]** window manager?
[/LIST]

---

### Post by Crooksey on 2008-02-19
In the gnome sessions menu, surely you can remove the option for compiz to start.

You can also add a new startup command within gone to run "metacity --replace".

---

### Post by Bruce M. on 2008-02-20
> **Crooksey said:**
> In the gnome sessions menu, surely you can remove the option for compiz to start.

You can also add a new startup command within gone to run "metacity --replace".

Strangely enough it is not there.
[CENTER]
[[IMG]http://img523.imageshack.us/img523/5379/startupzq6.th.png[/IMG]](http://img523.imageshack.us/my.php?image=startupzq6.png)
[/CENTER]
... and according to the "Current Session" Metacity is running, not Compiz:
[CENTER]
[[IMG]http://img523.imageshack.us/img523/1614/currentqo8.th.png[/IMG]](http://img523.imageshack.us/my.php?image=currentqo8.png)
[/CENTER]
and after running metacity --replace. The screen blinked on off a few times and I checked with "Configuration Editor --- it's still compiz.
[CENTER]
[[IMG]http://img123.imageshack.us/img123/8581/nometacitymw3.th.png[/IMG]](http://img123.imageshack.us/my.php?image=nometacitymw3.png)
[/CENTER]

So the question still applies:
[LIST]
[*]How do I go about making Metacity my "Default" window manager?
[/LIST]

---

### Post by Bruce M. on 2008-02-20
In Config Editor I made Metacity default and that fixed it.

Solved

---

### Post by bharadwaj on 2008-02-20
previously i had a problem with emrald my window borders disappear suddenly and then I had to do the same thing to get rid of it....

---

### Post by McLogic on 2008-03-03
> **Bruce M. said:**
> In Config Editor I made Metacity default and that fixed it.

Solved

I have Config Editor up, but what settings do I change? 

I have to type "metacity --replace" after each boot.

---

### Post by Bruce M. on 2008-03-03
> **McLogic said:**
> I have Config Editor up, but what settings do I change? 

I have to type "metacity --replace" after each boot.

So sorry, I should have posted the way to do it, I apologize.
Here's the solution:

If you want Metacity permanently in Gutsy

Set it up in Applications > System Tools > Configuration Editor

In Configuration Editor: desktop > gnome > applications > window_manager

Right click on the two keys ( Current and Default ) and edit them to read:

/usr/bin/metacity

I tried using "metacity --replace" but it's NOT change either of these keys, therefore not permenant.

---

### Post by McLogic on 2008-03-13
> **Bruce M. said:**
> So sorry, I should have posted the way to do it, I apologize.
Here's the solution:
If you want Metacity permanently in Gutsy
Set it up in Applications > System Tools > Configuration Editor
In Configuration Editor: desktop > gnome > applications > window_manager
Right click on the two keys ( Current and Default ) and edit them to read:

/usr/bin/metacity

I tried using "metacity --replace" but it's NOT change either of these keys, therefore not permenant.

I do not know why,** but that did not work**. I still come up to compiz with no window borders (can't move/resize, alt+tab, etc.). I can bring up a border less Gnome Terminal window, and then "metacity --replace" but that is a PITA. The Config Editor did say that **the keys that we modified were [deprecated]("http://www.google.com/search?hl=en&q=define%3Adeprecated&btnG=Search")** a couple of versions ago. 

This is my desktop machine: AMD 1900+, 512 MiB, VIA chipset, ATI Radeon video (old card, open driver). I don't think that any of the hardware matters.

---

### Post by Bruce M. on 2008-03-13
> **McLogic said:**
> I do not know why,** but that did not work**. I still come up to compiz with no window borders (can't move/resize, alt+tab, etc.). I can bring up a border less Gnome Terminal window, and then "metacity --replace" but that is a PITA. The Config Editor did say that **the keys that we modified were [deprecated]("http://www.google.com/search?hl=en&q=define%3Adeprecated&btnG=Search")** a couple of versions ago. 

This is my desktop machine: AMD 1900+, 512 MiB, VIA chipset, ATI Radeon video (old card, open driver). I don't think that any of the hardware matters.

It worked for me... but after I ran the "metacity --replace" now that I think about it and re-read everything here.

1 I ran: metacity --replace
2 then I reset the keys 

and everything after that was metacity.  But maybe I'm kidding myself, maybe because I changed those keys I believed metacity was running and it wasn't!  No wonder I find Xfce faster!

OK, how about:

Adding a new startup command within gnome to run "metacity --replace".
Thanks to: Crooksey

Bruce

---

