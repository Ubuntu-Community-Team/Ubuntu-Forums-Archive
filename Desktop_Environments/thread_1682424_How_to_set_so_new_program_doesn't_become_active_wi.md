---
title: "How to set so new program doesn't become active window?"
date: 2011-02-05
forum: Desktop Environments
---

### Post by wizodd0 on 2011-02-05
It drives me craxzy, and I can't find anything I can do about it.

When I start a new app--say FireFox, and I return to the window I was in, as soon as each window loads it insists that IT should become the active window.

This is a general issue with me--all window type OS's seem to do this, but what I want (and THAT is supposed to be what the computer will do 4 me--***what I want!***

No matter what, I want the active window to remain the active window regardless of what other windows are doing--including newly opening windows. If I want to do something with a new window, I'll go there on my own.

I'm often writing and want to research something so will open a browser window, but it takes time for the programs to load & during that time I usually want to continue with whatever I was doing until I finish the thought. As is, I'm reading or typing along, and suddenly the machine pops me into the newly opened window--a real pain,

Of course, if I could tell it to either become active or not depending upon *how* I call the program, or which program or which program is active, *that* would be perfect.

I'm not sure where the fix might be, but since it's a desktop interface problem, I'm posting it here.:confused:

Baring a solution, any suggestions as to where that kind of action originates so I can hunt the bugger down and modify it would be appreciated.

---

### Post by Copper Bezel on 2011-02-05
Hmm. Metacity has an option on focus for new windows in GConf-Editor that should do this, but it only has two options: the default, called "smart," and one that causes windows launched from terminal to stay in the background. I don't see anything in Window Rules and such in Compiz's settings that will help. Even setting focus-stealing-prevention to high doesn't keep new windows from getting it.

Not a bad idea, and I kind of wish this option was here as well.

---

### Post by Krytarik on 2011-02-06
I still believe it's managable to set it up the way you want, just try it.

I suppose, you are running Compiz. 
- "System -> Preferences -> CompizConfig Settings Manager  -> Window Management -> Window Rules"
- focus settings in "General  Options"

Those window matching guide may be handy for the first mentioned one:
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

---

### Post by wizodd0 on 2011-02-06
> **Krytarik said:**
> I still believe it's managable to set it up the way you want, just try it.

I suppose, you are running Compiz. 
- "System -> Preferences -> CompizConfig Settings Manager  -> Window Management -> Window Rules"
- focus settings in "General  Options"

Those window matching guide may be handy for the first mentioned one:
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

My menu stops at 'System -> Preferences ->'

Though compiz is installed, it isn't running. And I can't find anywhere in the GUI that will start it--just executing it from a launcher doesn't seem to do anything.

---

### Post by Krytarik on 2011-02-06
> **wizodd0 said:**
> My menu stops at 'System -> Preferences ->'

Though compiz is installed, it isn't running. And I can't find anywhere in the GUI that will start it--just executing it from a launcher doesn't seem to do anything.
Do you want to run Compiz then? It needs hw-accelerated video to work. Try enabling it via "System -> Preferences -> Visual Effects", set it to "Normal" or "Extra".

To get the settings manager I was referring to:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by wizodd0 on 2011-02-06
> **Krytarik said:**
> Do you want to run Compiz then? It needs hw-accelerated video to work. Try enabling it via "System -> Preferences -> Visual Effects", set it to "Normal" or "Extra".

To get the settings manager I was referring to:
```
sudo apt-get install compizconfig-settings-manager
```

I'll run anything that does what I want & doesn't steal from me....:p

I ran the command line.

There's still no  "System -> Preferences -> Visual Effects" in my menus.

---

### Post by Copper Bezel on 2011-02-06
Isn't the package name ccsm, not compiz-config-settings-manager?

And again, neither General Options - > focus settings nor Window Rules really help. The former can make windows focus by hover instead of by click, and the latter can make classes of windows unfocusable, neither of which helps the OP's case.

---

### Post by Krytarik on 2011-02-06
> **wizodd0 said:**
> I'll run anything that does what I want & doesn't steal from me....:p

I ran the command line.

There's still no  "System -> Preferences -> Visual Effects" in my menus.
Oh, I forgot "Appearance" in between.;-)

---

### Post by Krytarik on 2011-02-06
> **Copper Bezel said:**
> Isn't the package name ccsm, not compiz-config-settings-manager?
Nope, checked it before.
> **Copper Bezel said:**
> And again, neither General Options - > focus settings nor Window Rules really help. The former can make windows focus by hover instead of by click, and the latter can make classes of windows unfocusable, neither of which helps the OP's case.
You seem to be right, I took me some time to run a bunch of test. But to be correct, one has to say, that the desired behaviour obviously isn't that the newly created window doesn't has the focus/be active, but that it should be below the currently used one.

---

### Post by Copper Bezel on 2011-02-06
True, that's a much more accurate way of putting it.

Just tested the "strict" setting in Metacity in gconf. It works, and you could set launchers to "run in terminal" to force them to load in the background, but Compiz overrides the setting.

---

### Post by wizodd0 on 2011-02-06
> **Krytarik said:**
> Nope, checked it before.

... isn't that the newly created window doesn't has the focus/be active, but that it should be below the currently used one.

Guys, this kind of thing has bugged me ever since we started working in a windowed environment, so please bear with me as I try and define what I need/desire.

[B]"Don't interrupt the boss when I'm working!"

[SIZE=4]Diagram[/SIZE][/B]

**Interrupt?** [SIZE=2]*(open window to it's normal size and change focus to the new window.)*[/SIZE]
Yes|No|{No on live input}|{Check w/ focus window/program override}

-Yes
-No
-No if input active
-Allow override by current focus window (What are the default settings for the particular program I'm working with in the current focus window.

It's *usually* o.k. to interrupt me and change focus if I am not actively using an input device. 

It's *default* should be to load in the background if I am currently sending input.

**Other wants**

When I open a new window, based upon where the focus was when I launched, what was running in that window, what program is being called, what keys were pressed when it was launched. (All other window settings should ALSO be able to be set based upon these factors.)

For instance, if I'm reading a book and I pop up a window for a browser, I'm probably going directly to that window because I'm probably googling to find out something. But sometimes I'm just tossing off a search to find out more about something for later interest.

If I'm in my email program and launch a browser, the same things apply--but if a window pops up and I am currently typing or moving the mouse, I want the window to go to the background and leave me to what I'm doing.

Gee, explaining it redefines it as so often happens.

the other stuff would be nice--like changing window boarders based upon settings & active programs, it could be very useful--heck, maybe it exists.

But a simple switch that I could throw which would prevent any program from taking focus or overlaying any part of my screen would be a HUGE improvement.

Thoughts?

---

Appears I don't have the hardware in this machine to  run compiz.

Under the '~->visual effects' I had three choices, no/medium/hi effects. Hi doesn't work.

---

### Post by Copper Bezel on 2011-02-06
He was just putting that in more technical terms. I agree with you, this does seem like a good idea, but it might not be possible to implement it.

The closest thing I've found is gdevilspie, which should, technically, allow you to launch all programs, or any of a list of programs, minimized. Unfortunately, I can't actually get it to work. (Too bad for me, too - another application of the program would be to force document windows to maximize vertically on launch, something I'd really love.)

Edit: Never mind; I figured it out, and it does allow you to launch backgrounded, along with configuring basically everything else to do with what happens when you start programs. I think this is the solution. My problem was this: if you create or change a rule, you have to restart the daemon.

---

### Post by wizodd0 on 2011-02-06
I'm 100% certain that it is *possible* to do all of these things.
 
 But I'm ignorant right now about what is *currently available*--how  many features on the want list exist somewhere is important, but like I  say, the single ability to force all new programs to launch in the  background would make life easier for me.

---

### Post by Copper Bezel on 2011-02-06
First, I said "possible to implement," that is, available, so no semantic silliness here. Second, did you ... not read the other part of my post?

You need two applications: devilspie, a rules program for exactly all of the things you want, and gdevilspie, its manager.

sudo apt-get install devilspie gdevilspie

Then, run gdevilspie . There will be a checkbox to run on startup. Create the rules you want, then restart devilspie and close gdevilspie.

You can set any program you like to run in the background with Action - > Background. It's not a single switch, but it's damned close.

---

### Post by wizodd0 on 2011-02-09
> **Copper Bezel said:**
> 
Never mind; I figured it out, and it does allow you to launch backgrounded, along with configuring basically everything else to do with what happens when you start programs. I think this is the solution. My problem was this: if you create or change a rule, you have to restart the daemon.

I've got it running, but I don't know how to write the rules--could you please post the rule you wrote?

(re:'implement' pardon, in my universe, implementation has usually included design & coding. I'm over 10 years out of date.)

***

So basically, this provides static rules for handling--as in the rules may not dynamically change though they may be programmed to do different functions depending upon window states?

---

