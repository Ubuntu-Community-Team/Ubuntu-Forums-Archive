---
title: "Gnome Panel Forgets Its Position on Reboot"
date: 2007-02-23
forum: Desktop Environments
---

### Post by legalizemeth on 2007-02-23
Hi everyone.  I use Ubuntu basically 100% of the time and I love it.  My work machine, my home machine, and my laptop all run it.  I even installed it on my girlfriend's computer; it's great!

I do have one small annoyance though.  I like to have the two panels on the bottom of the screen, with the one that is on top by default at the very bottom (see the attached screenshot 'what_i_like.png').  This is no problem; I drag the top panel to the bottom of the screen and I'm good to go.  That is, until I log in after turning on or rebooting the machine.  Then, both panels are on the bottom of the screen, but their order is reversed: the one with 'Applications', 'Places', etc is on top of the one that shows open windows.  (See the other attached screenshot 'on_boot.png'.)  I can switch them back to how I like it, but the changes always get lost on a reboot.  :confused:  (This happens with Dapper and Edgy.)

Does anyone know how to make this stick?

---

### Post by louis_nichols on 2007-02-23
I used to have this problem too. Never did find a solution, so I resorted to simplifying my panels.

I would like to see a solution, though...

---

### Post by legalizemeth on 2007-02-23
> **louis_nichols said:**
> I used to have this problem too. Never did find a solution, so I resorted to simplifying my panels.

I would like to see a solution, though...
Thanks, I would too.  I'm hoping this isn't a gnome (not just Ubuntu) issue, but I'll dig into the sources if I have to.

---

### Post by John Bennett on 2007-06-24
> **legalizemeth said:**
> ...I log in after turning on or rebooting the machine.  Then, both panels are on the bottom of the screen, but their order is reversed

I have the same annoying problem.

If anyone knows how to make our preferred panel order persist after a reboot, please tell us!

---

### Post by malspa on 2007-07-07
I am having a similar problem.  Using 6.06.  When I log in, the top panel is no longer up at the top of the screen, but is repositioned to about two-thirds of the way up.

My work-around for now is to go to the Panel Properties, select Expand, then de-select Expand, and then the panel returns to its proper position.

Anyone know how to correct this behavior?

---

### Post by John Bennett on 2007-09-15
Anyone?

---

### Post by malspa on 2007-09-17
Still no luck fixing this behavior for me.

---

### Post by Wolki on 2007-09-17
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/gnome-panel/+bug/22807](https://launchpad.net/ubuntu/+source/gnome-panel/+bug/22807) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is a known bug

Gnome Bugzilla: [http://bugzilla.gnome.org/show_bug.cgi?id=126990](http://bugzilla.gnome.org/show_bug.cgi?id=126990)
LP: [https://launchpad.net/ubuntu/+source/gnome-panel/+bug/22807](https://launchpad.net/ubuntu/+source/gnome-panel/+bug/22807)

malspa: I think your problem is a different one.

---

### Post by hessiess on 2007-09-17
i have a simaler problem, but insted of the whole pannel moving, the objects in the pannel move around, and soetimes disapier, espetialy when locked to pannel is checked

---

### Post by oomingmak on 2007-09-17
> **hessiess said:**
> I have a similar problem, but instead of the whole panel moving, the objects in the panel move around, and sometimes disappear, especially when locked to panel is checked.
I get that too. It's **really **annoying.

I set up my panel objects to be positioned just how I want them, then I make sure each one is locked so that it can't be moved, but then on about 8 out 10 reboots, the panel objects will have shifted so that I have to re-position them all over again.

This comes as no great surprise to me, windows don't stay where you put them, icons don't stay where you put them, so why should panel objects be any different? :roll:

---

### Post by malspa on 2007-09-18
> malspa: I think your problem is a different one.

Yes, it's not exactly the same problem, but it still points to the issue of things on the desktop not staying where they're supposed to.

> This comes as no great surprise to me, windows don't stay where you put them, icons don't stay where you put them, so why should panel objects be any different?

My sentiments exactly.  One of the few issues that I have with Gnome in Ubuntu.

---

### Post by Wolki on 2007-09-19
> **malspa said:**
> Yes, it's not exactly the same problem, but it still points to the issue of things on the desktop not staying where they're supposed to.

Sure, but a solution for one likely isn't a solution for the other, so they are seperate bugs and should be treated separately. Just in case you wanted fo file them (which you probably don't need as I think they're alrady known).

To the people getting panel applet order mixups, are you changing your screen resolution? If so, that's a known (and very annoying bug) in gnome-panel.

---

### Post by malspa on 2007-09-20
> Sure, but a solution for one likely isn't a solution for the other, so they are seperate bugs and should be treated separately.

Yes, Wolki, I'm sure you are absolutely correct and they are completely separate bugs and completely separate issues.  I had to go back and look at the beginning of the thread.

Anyway, one thing about my separate bug is that I haven't even done anything to reposition that top panel in the first place.  It just started repositioning itself for no apparent reason.  Nice.

And another thing about my separate bug, why is it that there are these separate bugs in Gnome where things on the desktop don't stay where they're supposed to?  Instead of a separate bug, sounds more like an infestation.

And finally, is there a config file or something that I could take a look at to see why my top panel is out of place each time I boot back into Ubuntu?

Oh, well, other than this little issue, Dapper's been treating me well, so if nobody knows how to fix this one thing, I'll live with it until the next LTS comes out.

peace

---

### Post by Wolki on 2007-09-20
> **malspa said:**
> And another thing about my separate bug, why is it that there are these separate bugs in Gnome where things on the desktop don't stay where they're supposed to?  Instead of a separate bug, sounds more like an infestation.

Yeah, there are several annoying bugs related to that. I guess there are reasons, but I'm not that much of an expert. I know that the panel architecture is kind of messy, especially with applet positioning. Your problem might be one from interactions between configuration options that were not tested, or some other reason. BTW, did you take a look at the GNOME bugzilla to see whether your panel placement issue is already known? And how is your panel configured, from your description I think your panel isn't set to expand?

The window placement remembering issue is actually rather difficult. Problem is that it's not clear whether the window manager or the applications themself are supposed to do the remembering. Both have advantages and disadvantages: If the applications do it themself, window position of applications that don't do this are not respected. If the window manager does the remembering, applications that want to remember the window positioning and size per document might not be able to do this correctly if the window manager forces another size on the windows.

---

### Post by malspa on 2007-09-20
> BTW, did you take a look at the GNOME bugzilla to see whether your panel placement issue is already known?

No, sorry, posting here has been the only step I've taken to try to find out what's going on..

> And how is your panel configured, from your description I think your panel isn't set to expand?

This part is very strange.  OK, right-clicking on the panel handle and going into Preferences, the box next to "Expand" is not checked.  This is the case for both top and bottom panels.  But both panels do expand -- the top top panel expands if I add icons to it, and the bottom panel expands as needed depending on what applications I have open, etc.  And also both panels are centered.

But if I put a check in "Expand" box then things get weird.  The panel will move all the way over to the left, and the right-side handle will move all the way over to the right.  Sometimes if I do this with the bottom panel, the desktop pager will also move over to the right, with everything else moved over to the left.  So I leave the "Expand" box unchecked, so that the panels stay centered and expand as needed.

Sounds crazy doesn't it?  Maybe I've done other things to this desktop that have affected things, because I have played around with it a bit, similar to how I would do with a KDE desktop.  But the KDE desktop seems predictable and understandable, while the Gnome desktop seems kind of mysterious.  I'm not very knowledgeable about Gnome to begin with, I'm very KDE-centric.  I also like to use Fluxbox, and I have Fluxbox installed with Ubuntu, and I use that sometimes instead of Gnome.  Ubuntu is not my primary OS; I also have Mepis and PCLOS on this PC, and I run Kubuntu (Dapper) on my notebook.  I decided to install Ubuntu Dapper just so that I could become more familiar with Gnome, and because I like the LTS concept.

Now I'm hesitant to touch anything else... I just want to leave things mostly as they are, because right now things are ok to work with once I boot up and fix the positioning of that top panel

Since things are getting closer to the next LTS, I am just going to hang around with Dapper as it is instead of reinstalling and starting over.  Then when Hardy Heron comes out I'll do a fresh install and then maybe learn some more things while I'm setting that up.  Perhaps I'll do better with setting up my desktop, and perhaps my problems with the top panel do not occur beyond Dapper.

---

### Post by Wolki on 2007-09-20
> **malspa said:**
> No, sorry, posting here has been the only step I've taken to try to find out what's going on..

Still not quite sure what exactly is happening. Does one of these bugs match?
[http://bugzilla.gnome.org/show_bug.cgi?id=478630](http://bugzilla.gnome.org/show_bug.cgi?id=478630)
[http://bugzilla.gnome.org/show_bug.cgi?id=338538](http://bugzilla.gnome.org/show_bug.cgi?id=338538)
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/39856](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/39856)


> This part is very strange.  OK, right-clicking on the panel handle and going into Preferences, the box next to "Expand" is not checked.  This is the case for both top and bottom panels.  But both panels do expand -- the top top panel expands if I add icons to it, and the bottom panel expands as needed depending on what applications I have open, etc.  And also both panels are centered.

Expand does not mean that the panels expand to fit the size of your applets (would be a pretty useless setting - of course the panel must be as large as needed). It means that the panel is as large as possible, usually a beneficial setting so that you can make full use of the screen edges (fastest point to access with the mouse) and so that applets tend to be in the exact same spot.

I'm sure that there are people with an aesthetic preference for non-expanded panels. but after scanning bugzilla, it seems they're quite buggy though - panels are quite complex things, especially very modular ones like the gnome panel (which, to makes things worse, seems to have some architectural deficits). And a setting that is used by fewer people (I assume) is likely to be more buggy, since it's less tested, especially if combined with other options that affect them.

---

### Post by LowSky on 2007-09-20
I bet the issue liew with the  Applications(etc.) Menu. Gnome/Ubuntu must think that this bar has to be above al the other to open correctly..

If you putting both bars on the bottom, why not condence everythin onto one and make the one bar thicker.

---

### Post by malspa on 2007-09-21
> Expand does not mean that the panels expand to fit the size of your applets (would be a pretty useless setting - of course the panel must be as large as needed). It means that the panel is as large as possible, usually a beneficial setting so that you can make full use of the screen edges (fastest point to access with the mouse) and so that applets tend to be in the exact same spot.

Well, both panels expand depending on what's showing on the panel, as needed.  The behavior is exactly what I would expect from the word "expand."  I don't think I'm misunderstanding anything there, I've used panels that expand before.  Just find it odd that they do expand although the "Expand" box is unchecked.

Anyway, as to the bug reports, I don't think any of them match what I'm seeing.

Wolki, I really appreciate your efforts, but I'll step out of this thread.  My issue is slightly different than the original issue.  I don't want to distract from the original focus of the thread, so maybe I shouldn't have posted, or I should have started a different thread.  And it's just not a big enough deal for me to want to pursue it anymore.  Thanks very much for your help!

---

### Post by puddy488 on 2007-09-21
I had the same issue a while ago.  It seems that for some reason the 'newer' panels are placed closer to the center of the screen when you reboot, regardless of where they were put.  

I had two panels on the bottom edge of the screen - menus and window list on top (the original panel from the default desktop), application launchers underneath (a new panel I made some time later).  Whenever i logged in though, the menus panel would always be below the application launchers.

I 'fixed' it by creating a new panel, moving then menus and window list to it and deleting the old one. It's pretty inelegant, but it worked for me.

---

### Post by John Bennett on 2007-09-26
> **puddy488 said:**
> I 'fixed' it by creating a new panel, moving then menus and window list to it and deleting the old one. It's pretty inelegant, but it worked for me.

I tried that.  It did not work.

This bug of panels not remembering their position has been known since 2003 !

[http://bugzilla.gnome.org/show_bug.cgi?id=126990](http://bugzilla.gnome.org/show_bug.cgi?id=126990)

---

