---
title: "multiple desktops?"
date: 2007-01-12
forum: Desktop Environments
---

### Post by mistafeesh on 2007-01-12
Hi,

I've just got ubuntu 6.06 installed, and I love it!

I was just wondering... I like the multiple workspaces idea - it's quite new to me....

But what I'd really like is to have different desktops in each of the workspaces too - ie different files on the desktop in them. Is that possible? (not bothered about the background  - just the files)

edit - oops! As I'm sure you've guessed I mean mul**t**iple desktops in the title!!

---

### Post by Sqwishy on 2007-01-12
That's a good idea, i googled it but didn't find much.
Anyone else know how to do this I might wana try!

---

### Post by tweedledee on 2007-01-13
> **Sqwishy said:**
> That's a good idea, i googled it but didn't find much.
Anyone else know how to do this I might wana try!

I do not believe this is possible - all the desktop manager does is read your ~/Desktop folder and display those icons on your desktop(s).  I'm sure nautilus can't handle multiple sources, it may be that another desktop manager (KDE or XFCE's) can, but I don't think so.

---

### Post by mistafeesh on 2007-01-14
darn!

Oh well. It's a nice idea though. Surely someone must have though of it who could actually invent it.... oh well.

---

### Post by tweedledee on 2007-01-16
> **mistafeesh said:**
> darn!

Oh well. It's a nice idea though. Surely someone must have though of it who could actually invent it.... oh well.

You could submit it (or see if someone else has and vote for it) as a feature request in Gnome, to encourage the developers to do so.

---

### Post by buuntuu! on 2007-01-18
hi there, just stumbled upon this...

i converted to linux a little while ago (finally its newb-friendly enough) so i'm still a little ignorant and just wondered: is there any advantage of having multiple desktops other than clearness when having numerous windows open??

---

### Post by tweedledee on 2007-01-18
> **buuntuu! said:**
> hi there, just stumbled upon this...

i converted to linux a little while ago (finally its newb-friendly enough) so i'm still a little ignorant and just wondered: is there any advantage of having multiple desktops other than clearness when having numerous windows open??

If you mean is the multiple desktop feature just a window organization tool, the answer is yes.  I find it useful to have programs that I run all the time but only check occasionally (e.g., mail) running in one desktop, and programs I'm activey working on in another.  But I frequently have as many 10 total windows open at once, so it would be crowded if I had to view them all at once, or keep track of which ones were minimized vs. open.

---

### Post by buuntuu! on 2007-01-20
thanks tweedledee!
that's what i like most about ubuntu: the community won't LOL at you when you post basic questions!

---

### Post by 3rdalbum on 2007-01-20
Actually, it's an awesome feature for when you're doing something that you shouldn't be doing... for instance, if you're playing Wormux and your parents come in, you can just hit "p" for pause and then your "switch to Desktop 3" key.

---

### Post by melusyne on 2007-01-25
> **tweedledee said:**
> I do not believe this is possible - all the desktop manager does is read your ~/Desktop folder and display those icons on your desktop(s).  I'm sure nautilus can't handle multiple sources, it may be that another desktop manager (KDE or XFCE's) can, but I don't think so.

Hi,
Since the desktop manager read the ~/Desktop, and since it's able to recognize different workspaces to display windows, it may be possible to split ~/Desktop into ~/Desktop/Work1 ~/Desktop/Work2 ... and make it display each content to the suitable workspace ?

I just don't know anything about how this works, but why couldn't the icons repartition be done if the windows repartition is already managed ?

Beside i thought Gnome was the base desktop manager in Ubuntu, nautilus being (basically) a file browser ?

And just to put a third question in there : is there a possibility to link the last workspace to the first, so that you can circle between them ? ( with Ctrl Alt Arrows i can just go from 1 to 2 to n and reward, but not from n directly to 1 or 1 directly to n)

Regards

---

### Post by tweedledee on 2007-01-25
> **melusyne said:**
> Hi,
Since the desktop manager read the ~/Desktop, and since it's able to recognize different workspaces to display windows, it may be possible to split ~/Desktop into ~/Desktop/Work1 ~/Desktop/Work2 ... and make it display each content to the suitable workspace ?

I just don't know anything about how this works, but why couldn't the icons repartition be done if the windows repartition is already managed ?

Conceptually, I agree that it is possible.  I'd guess it has not been implemented because many (most?) people who use their desktop to drop stuff on do so because they want access to it NOW.  Once you introduce sub-folders (or even just tags on the file, or some other implementation), you are making those people actually sort and locate.  At that point, you might as well go to a fully organized folder structure that may or may not use a desktop as a component.  In short, I think the barrier is more psychological than technical.

> **melusyne said:**
> Beside i thought Gnome was the base desktop manager in Ubuntu, nautilus being (basically) a file browser ?

Nautilus also manages the desktop.  Run gconf-editor, and go to Apps -> Nautilus -> Preferences, there is a "show desktop" option.  If you uncheck it, your desktop icons vanish.  "Gnome" is really Metacity (manages Windows & some of the mouse/keyboard) + Nautilus (manages everything to do with fiels) + a variety of small apps to do things like display dialog boxes.

> **melusyne said:**
> And just to put a third question in there : is there a possibility to link the last workspace to the first, so that you can circle between them ? ( with Ctrl Alt Arrows i can just go from 1 to 2 to n and reward, but not from n directly to 1 or 1 directly to n)

I don't belive so with Metacity.  You can change your window manager and get that behavior, although off-hand I don't remember which ones I've looked at work that way.  I'm currently back to Metacity, but I think about I'm about to change again - it has a couple of things that get on my nerves occasionally, although I like it's ease of use.

---

### Post by melusyne on 2007-01-26
Thanks tweedledee for all your answers !

i don't let myself much rubbish on my desktop, but was just thinking it could be useful to let hang the files on the Desktop where the related applications are displayed. Anyway i'm not looking for that kind of things.

as for the window manager, i'm going to stay with metacity a bit since i'm getting used to it and start playing to configure it to my needs... but i'll still look around for this circle-switching desktop thing.

thanks again !

---

