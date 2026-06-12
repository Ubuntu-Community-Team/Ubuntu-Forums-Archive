---
title: "[SOLVED] Beryl/Emerald improper rendering of maximized windows"
date: 2006-12-26
forum: Desktop Environments
---

### Post by stalker145 on 2006-12-26
OK, here we go again. 

I have finally gotten Beryl and the Emerald Theme Manager running almost perfectly on Edgy except my maximized windows fail to pick up on the theme. Anything less than maximized works just fine. 

I *think* I've checked all possible settings in Beryl and Emerald... knowing me, though, I've missed one that was right in my face. Anyone have any thoughts, suggestions, ideas? Thanks in advance.

---

### Post by bmhm on 2006-12-27
How can I get those fancy readings on my Desktop?

How can I get a console IN the Desktop without having a frame or menu?

---

### Post by stalker145 on 2006-12-27
> **bmhm said:**
> How can I get a console IN the Desktop without having a frame or menu?

To get a terminal in the desktop is rather easily done. [Here's the HowTo ]("http://ubuntuforums.org/showthread.php?t=202249&highlight=devilspie")that I used to do it. Took, maybe, 10 minutes from opening the terminal to completion. :cool: 

> **bmhm said:**
> How can I get those fancy readings on my Desktop?

The desktop readings are done using Conky. [Here's the HowTo]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky+howto") that I used to do it. This one toook a little longer to get the configurations the way I like it, but there are [plenty of ideas here]("http://ubuntuforums.org/showthread.php?t=281865") on what to do with your setup.

---

### Post by bmhm on 2006-12-27
[FONT="Verdana"]Thanks... didn't find them with forum search :) Didn't even know what to search ^^"[/FONT]

---

### Post by stalker145 on 2006-12-28
Bump...

Bueller... Bueller... Bueller... Bueller :)

---

### Post by peckerhead26 on 2006-12-29
Stalker145,

I am nick the new guy, so I do not have a clue how to get your "theme" to display maximized.  One question though, why does this interface look so much like Windows?

---

### Post by stalker145 on 2006-12-29
> **peckerhead26 said:**
> One question though, why does this interface look so much like Windows?

One reason why it looks so much like Windows is that a GUI is a GUI is a GUI. Another reason is that I like to "Keep It Simple Sometimes (KISS)" ©  8) 

Welcome to the forum.

---

### Post by peckerhead26 on 2006-12-29
Stalker,

Why is a GUI is a GUI is a GUI a reply to creativity?  I thought Ubuntu was a unique OS, what is so unique about copying windows?  
Again, I am the new guy so can you explain how Ubuntu is unique?

Thanks,

Peckerhead26

---

### Post by stalker145 on 2006-12-29
> **peckerhead26 said:**
> Why is a GUI is a GUI is a GUI a reply to creativity?  I thought Ubuntu was a unique OS, what is so unique about copying windows?  
Again, I am the new guy so can you explain how Ubuntu is unique?

I think I understand you question now, though it is a bit off-topic.

There truly is no unique GUI. Each GUI still has the same basic function and design. Most every GUI has windows (not the operating system) through which you control or access various parts of your system or perform certain functions. Along those lines, most windows (again not the OS) have a title bar that usually has the window name, a menu bar that gives access to the application's functions, and also a place to perform the application-specific functions - be they word processing, IM, or whatever. The [history of the GUI]("http://en.wikipedia.org/wiki/History_of_the_graphical_user_interface") is a long and sordid affair that you can check out if you'd like.

The things that make Ubuntu unique are not so much the GUI as  [the philosophy]("http://www.ubuntu.com/ubuntu/philosophy") and [the community]("http://www.ubuntuforums.org").

Ubuntu, and Linux in general, may copy some of the looks or functionality of Windows(who  copied from Apple), but in no way do they copy the Windows OS; it is much preferred to have a stable, hardened, low/no cost system that you can change in any way you want - not just the look, but function as well.

Feel free to PM or IM me if you have any other questions. There are also many threads already started on the forums that could probably explain this a heck of a lot better than I can, but I tried ;)

---

### Post by stalker145 on 2006-12-30
Another failure :( 

I guess everyone out there has this same problem and there is not workaround for it.

Either that  or I am the only person in the entire existence of Beryl that this is happening to and no one has been able to recreate or figure out the problem.

<sigh>

Well, on I go to find something else to tinker with.

---

### Post by Waappu on 2006-12-31
Hi

Could this solve your problem?
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)

---

### Post by stalker145 on 2006-12-31
> **Waappu said:**
> Hi

Could this solve your problem?
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)

Well, it definitely took me in a new direction. Thank you. 

I've noticed on the Beryl forum quite a few people that have similar problems and their posts have gone unanswered. Hopefully this one will be answered :rolleyes:

---

### Post by stalker145 on 2007-01-01
Thanks to Waappu for turning me on to the Beryl Forums and to khwu on the Beryl Forums for [this answer that has worked perfectly.]("http://forum.beryl-project.org/viewtopic.php?f=36&t=1571&p=9777#p9777")

> Try to edit xorg.conf, add

Code:
Option      "AGPSize" "32"


under section "Device" .


---

### Post by danboarder on 2007-01-14
Thank you all for figuring this out!  This was the biggest glitch on my system so far, and now it is solved.  

I am running a Sony GRX560 with an ATI Radeon Mobility 7500 ... Ubuntu/Gnome/Beryl are now running smoothly thanks to you all!  

I added "AGPSize" "32" to the Device section of my xorg.conf, and also followed the advice here: [http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)

If anyone else has trouble with ATI Mobility 7500, let me know, I can send my xorg.conf or anything else you might need.  It has taken a while to get things working right on this machine since it is getting older and ATI no longer supports this chipset. 

Thanks again! Hope I can help in the future.

---

### Post by Waappu on 2007-01-14
> **danboarder said:**
> 
If anyone else has trouble with ATI Mobility 7500, let me know, I can send my xorg.conf or anything else you might need
You can post you file already so if someone need it

---

