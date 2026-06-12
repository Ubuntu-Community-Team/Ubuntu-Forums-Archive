---
title: "gtk-recordMyDesktop extremely slow"
date: 2010-01-14
forum: Desktop Environments
---

### Post by sourabhsharma149 on 2010-01-14
Hi Friends,

I have Dell Inspiron laptop with 1 GB RAM and 1.7 GHz core 2 duo machine.

In Karmic while I run gtk-recordMyDesktop to record screen system becomes extremely slow.

In that case everything seems in slow motion i.e. there is while burn effect it takes 4 times more time so does rotation cube and all effects.

Also while not even recording and opening gtk-recordMyDesktop system becomes slow and screen doesn't refresh correctly. ( You can see trace of random color fire in the attachment)

I am attaching screen shots of setting of the gtk-recordMyDesktop. Could anyone please suggest where things are not optimal?

Also if there is any alternate s/w for recording screen activity?

Thanks

---

### Post by sourabhsharma149 on 2010-01-18
Hasn't ne body r&d'd on that ? :(

---

### Post by hellocatfood on 2010-01-18
I'm having the same problems as you. I've submitted a bug report about it [here](https://bugs.launchpad.net/ubuntu/+source/gtk-recordmydesktop/+bug/509111) and you can try some of the solutions posted [here](http://thefunkcorner.blogspot.com/2009/05/trials-with-recordmydesktop.html) [here](http://blog.sudev.in/archives/89) and [here](http://www.piotrkrzyzek.com/broken-pipe-overrun-occurred-8-step-recordmydeskop-solution-in-ubuntukubuntu-karmic-9-10/), though they've not worked for me

---

### Post by terran4000 on 2010-02-02
sadly there is no common fix for gtk-recordMyDesktop. Though you can use RecordItNow, which is much much much better than anything I've tried so far in linux. I've also created a little tutorial for anyone who needs help installing and start using RecordItNow [here]("http://www.piotrkrzyzek.com/screencasting-in-linux-with-recorditnow-pulseaudio/"). Hopefully it helps.

---

### Post by hellocatfood on 2010-02-02
Thanks, looks like a good one. Do you know if it'll work in GNOME?

Also, the Gnome Shell thankfully includes [screencasting software](http://live.gnome.org/GnomeShell/CheatSheet#Screencast_recording) by default, though not sure what framerate it'll do yet. We'll have to wait until October for it to arrive in Ubuntu though :-(

---

### Post by niffcreature on 2010-02-02
there is something called "istanbul desktop recorder" too

---

### Post by hellocatfood on 2010-02-02
> **niffcreature said:**
> there is something called "istanbul desktop recorder" too

Like many people I've tried all of them... xvidcap, recordmydesktop, ffmpeg, instanbul, vnc2flv and now recorditnow. All but the last two bring my computer to a halt upon recording and have problems encoding sound.

vnc2flv works with a decent frame rate (around 10), but it's command line and has a few bugs and limitations. The only one to work with at least 15 fps is recorditnow and even then it's stuttery.

It's annoying that, despite having a fairly good computer (see my sig), my old computer from 2004 running XP and a copy of [Cam Studio](http://camstudio.org/) (it's open source) was always faster/better than any of the offerings Linux has given me.

But, like a lot Linux solutions, they work for some and not for others. It's just a shame that for me, in this instance, there's no working alternative.

---

### Post by terran4000 on 2010-02-07
I'm glad recorditnow works for you. It's been a heaven for me since I found it. Never know why someone didn't make a decent one before!

Anywho, about poor performance (I know you've tried my tips [here]("http://www.piotrkrzyzek.com/broken-pipe-overrun-occurred-8-step-recordmydeskop-solution-in-ubuntukubuntu-karmic-9-10/")) ... I'm guessing you've increased the FPS on RecordItNow to something like 24 (which is what I keep it at)?

Also, did you try turning off compiz? From your computer specs it doesn't seem to even matter, sounds like you've got one nice computer. Which makes me wonder why it's really slow. 

"Something" has to be slowing it down. For a test, maybe try switching from ATI drivers to VESA drivers and recording a small 640x480 window using those drivers.

Good luck.

---

### Post by hellocatfood on 2010-02-07
hmmm, seems like it's stopped working now... I just get crashes when I start to record. Oh well...

I've tried everything you suggested (though I only have access to one graphics driver) and nothing works. Hmmm.... Well, hoping that the updates to recorditnow fix things.

---

### Post by terran4000 on 2010-02-08
You can try this though:

[LIST]
[*]uninstall recorditnow
[*]remove ~/.kde/share/apps/recorditnow/
[*]Install recorditnow again
[*]disable timeline and all options in the "RecordItNow" tab thingy in the configure window
[*]Also disable all plugins except for RecordMyDesktop
[/LIST]

In all probability, it could also be a audio problem. Bleh, dunno though :)

You can try running recorditnow from the command line with the following options:

> recorditnow --nocrashhandler

This, in theory, will produce a full core dump. Though, I dunno if it will be helpful at all.

---

### Post by hellocatfood on 2010-02-11
Tried all of that and still my system goes a bit choppy when recording.

Nevermind, looks like I'm back to playing the waiting game

---

### Post by terran4000 on 2010-02-17
Good luck. Hope it works out for you someday. Drop me a line when you get it to work. I'm curious as to what the solution will be and what the problem is/was.

---

### Post by hellocatfood on 2010-04-04
It looks like the problem for many users could be related to the graphics driver that they're using

[https://bugs.launchpad.net/recordmydesktop/+bug/509111](https://bugs.launchpad.net/recordmydesktop/+bug/509111)

I found that disabling it brought me back to an ok frame rate. This obviously isn't a solution, so if anyone else is having to the same problem please click on the "Also affects you" button.

---

### Post by Tikkyca on 2010-04-04
If you have ATI graphics card,don't try any screen recorder,because it will lagg,only way to fix this,is to just wait for the perfect ATI drivers to come out.

---

### Post by hellocatfood on 2010-04-07
Well, it looks like the problem has now been identified (libfb doesn't get hardware acceleration) but no idea how long it'll take to get fixed

[http://ati.cchtml.com/show_bug.cgi?id=1451](http://ati.cchtml.com/show_bug.cgi?id=1451)

---

