---
title: "minimal ubuntu + xfce vs xubuntu"
date: 2011-10-06
forum: Desktop Environments
---

### Post by _ari on 2011-10-06
[RIGHT]*I am a minimalist when it comes down to IT and a functionality enthusiast.*
*Therefore - combined with the fact that i want the most speed out of my new SSD, which also has not much space - i am sure that i want to use xfce as my desktop environment (for my notebook)*
[/RIGHT]


_Advantages of minimal ubuntu + xfce compared to xubuntu:_
-) minimalistic install: from the start on there are only programs running that i want and i can control every library (and etc) that is being installed (therefore: no space is wasted and i have total control over my system)
-) all the advantages of ubuntu: drivers, updates, community, flexibility, support, et cetera

_Disadvantages of minimal ubuntu + xfce compared to xubuntu:_
-) it seems .... "complicated" is not the term i am looking for.. you could call it "unnecessary work" to decide from scratch about every application....


That's how far i got with my train of thought about this.

I really would like **your opinions** about this and if you think what i wrote so far makes sense or if you totally disagree.


[CENTER][U]Thanks in advance, _ari
[/U][/CENTER]

---

### Post by ajgreeny on 2011-10-06
> **_ari said:**
> I really would like **your opinions** about this and if you think what i wrote so far makes sense or if you totally disagree.


[CENTER][U]Thanks in advance, _ari
[/U][/CENTER]

If you want an even more minimalistic desktop than xfce have a look at both LXDE and openbox.  Maybe also enlightenment is worth considering.

---

### Post by _ari on 2011-10-06
> **ajgreeny said:**
> If you want an even more minimalistic desktop than xfce have a look at both LXDE and openbox.  Maybe also enlightenment is worth considering.

xfce seems like my kind of desktop environment, cause it looks plain and simple but also i want a useful graphical environment and therefore i think it's my ideal choice.
I probably will go for choosing between openbox and xfce on start up maybe and i have already some experiences with openbox, so...

But what do you think of my idea basically?
Is minimal ubuntu + xfce better then xubuntu or is this just the vision of a dreamer?

---

### Post by ajgreeny on 2011-10-06
It really depends on what "better" means to you, which may not be the same as it is for me.  Basically though, I think you have a good point, and if you want to choose the packages you have installed, and just add the things that you need, rather than the packages that ubuntu thinks you need, you have a good idea.

I actually did that same thing a couple of years ago with the minimal install CD, added xorg and all that came with that, then just installed the packages I was missing, as I needed them.  It worked OK but eventually I decided that it was just too much hassle, and rather limiting when I found I did not have something I wanted or needed, and then had to mess around installing it.

Your own requirements may, of course be totally different to mine, and the whole idea may suit you very well.

---

### Post by _ari on 2011-10-06
> **ajgreeny said:**
> 
[.......]
I actually did that same thing a couple of years ago with the minimal install CD, added xorg and all that came with that, then just installed the packages I was missing, as I needed them.  It worked OK but eventually I decided that it was just too much hassle, and rather limiting when I found I did not have something I wanted or needed, and then had to mess around installing it.

Your own requirements may, of course be totally different to mine, and the whole idea may suit you very well.

At this point: Thanks for your insights so far. You are really helping me with this.

Yes, this is my concern. That it will be just too much trouble to go through.
When you did this (with minimal cd and xorg), did you ever have a stable system at one point where no configuration was needed (where you just were able to relax for a few weeks without working on your system), or was it an everlasting ongoing task of *configure this program to that* and *thinking hard about the different libraries and how to get things to work*?

Also does xubuntu have disadvantages compared to ubuntu, or are the desktop environment and the other applications the only difference between those two?

---

### Post by ajgreeny on 2011-10-07
In my case I did it as an exercise in managing a system, rather than as a needed option for a smaller OS, and it did run with no problems at all, needing no more configuration than any other linux OS that I've used, and certainly not being any more difficult to use for most things.

It was simply a case of me sometimes needing to do a particular or special job on the computer quickly, and then finding that to do so I needed to install a package or packages, plus all the dependencies.  That was easy enough if I knew exactly what did that job in a normal ubuntu installation, but it could also involve some searching for the packages needed to do it.  The dependencies of everything were, of course, dealt with easily by using synaptic, which is something I couldn't manage without;  if you don't use it personally, give it a good try out and I think you will find it is an incredibly useful package manager, and far better than the USC, in my opinion.

The difference between the ubuntu, xubuntu, kubuntu OSs is really as you suspect, just the DE used.  Every package is available for all OSs, no matter what DE is being used, though to add k3b, as an example, will also pull in a lot of KDE with it.

Why not give it a try?  It is easy enough to do, and if you find as I did that it's too much hassle, all it needs is the command ```
sudo apt-get install *ubuntu-desktop
``` for the standard OS to magically appear.

---

### Post by aeiah on 2011-10-07
i always install with the minimal install now. i guess it depends what you need, and on a laptop you probably want session and power management but on a desktop all that's really needed after install is
```

sudo apt-get install openbox thunar tint2 xinit chromium-browser file-roller feh etc etc 
```

xorg and all that jazz is automatic. xinit is needed for 'startx'. if you're just using standard software it isn't that inconvenient to open synaptic or use apt-get

---

### Post by _ari on 2011-10-07
> **ajgreeny said:**
> 
The difference between the ubuntu, xubuntu, kubuntu OSs is really as you suspect, just the DE used.  Every package is available for all OSs, no matter what DE is being used, though to add k3b, as an example, will also pull in a lot of KDE with it.

 
Yeah, a lot of KDE libraries and stuff necessary to run K3b i think.
So technically if i would install minimal ubuntu and xfce and then all the programs xubuntu would have, then i'd have just xubuntu all the same?
Sounds funny...

I think I'll go for it. I can see it as an experiment and when it really isn't working out for me, then - you are right - it's nothing that i couldn't fix easily

> **aeiah said:**
> 
i always install with the minimal install now. i guess it depends what you need, and on a laptop you probably want session and power management but on a desktop all that's really needed after install is
[....]


Ofc you are able to install those things like "power management" manually?
Guess I'll go for it

---

### Post by snowpine on 2011-10-07
Minimal install is a fun exercise; for many distros this method is actually the "normal" way to install. Definitely go for it if you are curious! You want to avoid the "xubuntu-desktop" package (that will give you the exact same thing as a full install of Xubuntu) and install "xfce4" instead for a leaner install.

Just a word of caution however, if you are truly devoted to a "minimalist" philosophy then eventually you will probably outgrow the Ubuntu way of doing things and experiment with distros like Arch, TinyCore, CrunchBang, etc. Just my personal experience. ;)

---

### Post by _ari on 2011-10-07
> **snowpine said:**
> 
Just a word of caution however, if you are truly devoted to a "minimalist" philosophy then eventually you will probably outgrow the Ubuntu way of doing things and experiment with distros like Arch, TinyCore, CrunchBang, etc. Just my personal experience. ;)

It's nice to have all the drivers for ubuntu ready when needed, therefore i don't think so but we'll see....
Maybe you are right :D

> **aeiah said:**
> 
i always install with the minimal install now. i guess it depends what you need, and on a laptop you probably want session and power management but on a desktop all that's really needed after install is
[...]


Not being an expert but being dedicated, will i be able to handle openbox as desktop environment?
Isn't it kind of hard?

---

### Post by _ari on 2011-10-08
[I]*This post was made by accident and since i wasn't able to delete it, changed into this sentence*
*Please see post before* Thank you and Sorry
[/I]

---

### Post by Elfy on 2011-10-08
you can use the report abuse button to alert staff to things other than abuse - for instance to remove mistaken posts :)

---

### Post by _ari on 2011-10-08
So let me say a last time:
Thanks for all your help :)

Minimal install worked, to install xfce wasn't any problem, but like some of you have predicted (correctly), i've already switched to openbox (as de) and am very interested in ArchLinux (also since there wikis and forums helped me out much already concerning some "problems" with openbox :))

Greetings, _ari

---

