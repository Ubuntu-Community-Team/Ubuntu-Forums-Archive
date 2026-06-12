---
title: "Shutdown Script"
date: 2009-09-29
forum: Desktop Environments
---

### Post by fryser_d on 2009-09-29
I need to run a Script *[SIZE="4"]**_[COLOR="Red"]<<"BEFORE">>[/COLOR]_**[/SIZE]* everything else, even before gnome shutdown. I've read countless thread that say to use the:
**/etc/rc0.d ** scripts
Or
**/etc/gdm/PostSession/Default** to point on[B] ~/.bash_logout
[/B]
The problem is that it start a command that close and execute a lot a stuff, **BEFORE** starting my script...

[COLOR="Red"]_What I want:_[/COLOR]
Click on "shutdown"(Top right menu) > BOOM! my script start(before or after the shutdown countdown) it's not that important; BUT it must not start anything else after. :guitar:

_[COLOR="Red"]What I need:[/COLOR]_
If someone can point me out where's the script to customize the shutdown "function" or customize the menu or HOW to bypass that function. :P

Thanks for your time.
Fryser

---

### Post by kerry_s on 2009-09-29
what is this script? why so important before anything else?
doing it that way can corrupt your system.

---

### Post by fryser_d on 2009-09-29
^What? :-s

Nah, I don't think so.

---

### Post by kerry_s on 2009-09-29
> **fryser_d said:**
> ^What? :-s

Nah, I don't think so.

okay, it's your system.
if it were me, what i would do is rename the /sbin/shutdown to something else put my script as the /sbin/shutdown & call the original shutdown on the last line of the script, that should be safe, but you would need to watch out for updates that would overwrite it.

you might have to do the same with reboot & halt.

---

### Post by fryser_d on 2009-09-30
Thx kerry_s!

Maybe that would just do it... but where do I find that **/sbin/shutdown** ?? 

And is that a script or a bin to compile!?

Thx again for your time. 
Fryser

---

### Post by karlson on 2009-09-30
> **fryser_d said:**
> Thx kerry_s!

Maybe that would just do it... but where do I find that **/sbin/shutdown** ?? 

And is that a script or a bin to compile!?

Thx again for your time. 
Fryser

Simpler way to do this is create a K00AAAA_my_script in /etc/rc0.d

It will the first script to execute.

---

### Post by fryser_d on 2009-09-30
Thx karlson

I tried your suggestion, it didn't work properly.(it executed but way after I need it)

I think Ubuntu must work something like that:

```
Gnome: Click on top-right menu "Shutdown"
Gnome: verification Choice (OK-Countdown/ Cancel)
Gnome: Gnome verification: try to close all windows.
If success
    fallback on Ubuntu system
Else
    Cancel Shutdown
    exit
Ubuntu: Run /etc/rc0.d
```
:popcorn:

my script must run somehow before: (Gnome: Gnome verification: try to close all windows)

Someone have an idea Gnome masters? :KS

Thx for your time.
Fryser

---

### Post by kerry_s on 2009-09-30
> **fryser_d said:**
> Thx kerry_s!

Maybe that would just do it... but where do I find that **/sbin/shutdown** ?? 

And is that a script or a bin to compile!?

Thx again for your time. 
Fryser

no, you would just rename it.
for example:

sudo mv /sbin/shutdown /sbin/shutdown2
gksudo gedit /sbin/shutdown

#!/bin/sh
my script i want to run
/sbin/shutdown2


make it executable:
chmod +x /sbin/shutdown

so it runs your script first, then the actual shutdown.

---

### Post by fryser_d on 2009-10-01
Thx for the precise reply kerry_s

I tried what you suggested and I still have the same result :S

Like I explained:
I think Ubuntu must work something like that:
```
Gnome: Click on top-right menu "Shutdown"
Gnome: verification Choice (OK-Countdown/ Cancel)
Gnome: Gnome verification: try to close all windows.
If success
    fallback on Ubuntu system
Else
    Cancel Shutdown
    exit
Ubuntu: Run /etc/rc0.d
```

I think it's a Gnome GUI issue, where it's not yet at the point where it interact with the Ubuntu systems. Gnome must have it's own "shutdown protocol", and if everything is OK and clean, it falls back on Ubuntu.

The problem is with my system I have so much things to do, to have an OK and Clean that frustrate me every time I shutdown. I could execute my script and call for a shutdown,... but grrr, I'd love to have it clean. :guitar:

Someone knows in the gnome system, how to access the GUI menu behaviors? :KS

Thx for your time guys.
Fryser

---

### Post by falconindy on 2009-10-01
I must be missing something... Why not just run your script and have it finish with a call to /sbin/shutdown?

---

### Post by kerry_s on 2009-10-01
what is this script that it has to be first?

i do know where your coming from, i use a script for my shutdown, but i'm not doing anything fancy, i just wanted my own dialog with all the out options & no countdown.

---

### Post by fryser_d on 2009-10-05
^ok I see a shortcut with the panel.

Bu someone know how to customize the "Fast Switch user Menu"?

---

