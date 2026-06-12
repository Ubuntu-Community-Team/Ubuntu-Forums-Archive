---
title: "Gnome 3 vs Gnome Shell vs Unity"
date: 2011-04-28
forum: Desktop Environments
---

### Post by tubunu on 2011-04-28
Please excuse my ignorance, but I need to get it straight. I've been reading and trying to find out more about these three new desktop environments, but still am rather confused. 

I have had Unity on my netbook for a couple of months now and know it inside out (more or less by now). The problem is: **what is the main difference between Gnome 3 and Gnome Shell**? 

To my understanding Gnome 3 will be a continuation of the panelled Gnome we are so used to? But then I read the panels will be gone forever, so I'm confused again... Gnome Shell is somewhat similar-looking to Unity, but I haven't had a chance to try it properly yet. 

Thanks.

---

### Post by vanadium on 2011-04-28
For Ubuntu users, this question does not yet matter: Ubuntu is still using Gnome 2.

Gnome 3 is the successor of Gnome 2. Has been in developpement for a very long time, relies on largely rewritten gtk 3 libraries, etc.

Gnome Shell is just the surface of the system: the software that you see first when your computer is ready and that allows you to start applications and work with data. Ubuntu has decided not to use Gnome Shell but its own shell: Unity.

As of now, Unity is still working on top of Gnome 2. I guess the next version of Ubuntu, 11.10, will bring us Gnome 3, also with Unity as the shell.

---

### Post by MundoMondo on 2011-04-28
> **vanadium said:**
> For Ubuntu users, this question does not yet matter: Ubuntu is still using Gnome 2.

Gnome 3 is the successor of Gnome 2. Has been in developpement for a very long time, relies on largely rewritten gtk 3 libraries, etc.

Gnome Shell is just the surface of the system: the software that you see first when your computer is ready and that allows you to start applications and work with data. Ubuntu has decided not to use Gnome Shell but its own shell: Unity.

As of now, Unity is still working on top of Gnome 2. I guess the next version of Ubuntu, 10.10, will bring us Gnome 3, also with Unity as the shell.

I think you got the versions mixed up there a tad bit ;)

But as i have been struggling to figure this out myself, i have to ask just to clarify. So any gnome version, be it Gnome 1 / 2 /3 / 45, it is gnome shell becuase it is the graphical interface which allows us use the mouse, point and click and start programs outside the terminal interface? Unity then is another shell? What i don't get is why Ubuntu would possible gain from laying Unity on top of gnome no matter what version. From what i know, ubuntu has quite a few softwares so t ightly nitted into the shell that it makes it tricky to switch. For example, if you login to gnome 3 then it breaks unity. It would be much nicer if there wasn't a load of packages lying around that i want nothing to do with. In this case, Unity. I prefer gnome :P

---

### Post by vanadium on 2011-04-28
I have corrected my post, thanks ;)

> So any gnome version, be it Gnome 1 / 2 /3 / 45, it is gnome shell becuase it is the graphical interface which allows us use the mouse, point and click and start programs outside the terminal interface? Unity then is another shell?

Gnome is actually a collection of many programs, build on common libraries. Together, they provide the user with a "desktop experience".

"Shell" is not precisely what allows you to use mouse, point and click, etc. "Shell" rather designates the program (or collection of programs) that provides e.g. a launcher and other items to start applications and change system configuration.

For example, gnome-control-center is an application that allows access to all applications that relate to configuring your system. In the Unity shell, you can access it through the logout button on the panel ("System Settings", last menu entry). Thus, it looks like an integral part of the Ubuntu system, whereas in reality, all what the Unity shell needs to do is launch that program.

This is what a shell does: it "integrates" different utilities. In that sense, the gnome-control-center is in its turn also a shell to all individual utilities you can launch from it.

> 
What i don't get is why Ubuntu would possible gain from laying Unity on top of gnome no matter what version.
"unity" is appearance, a way of interacting with the desktop. Instead of rewriting a whole new desktop, Canonical developpers just put their interface of choice on an existing desktop system, the Gnome desktop. The gain is that they can implement their own interface which they deem better than the new one of Gnome, yet they do not need to rewrite an entirely new desktop: they continue to use Gnome, which indeed is a high quality desktop.

> 
From what i know, ubuntu has quite a few softwares so t ightly nitted into the shell that it makes it tricky to switch.

Not quite, as I illustrated with gnome-control center above. This modular approach used in linux desktops allows for great flexibility.

> 
For example, if you login to gnome 3 then it breaks unity. It would be much nicer if there wasn't a load of packages lying around that i want nothing to do with. In this case, Unity. I prefer gnome 
The reason of these problems is more of a technical nature. The underlying toolkit and libraries of the new Gnome 3 has drastically changed and are incompatible with the toolkit of Gnome 2. Unity is now still operating on top of Gnome 2. Replacing Gnome 2 with Gnome 3 would obviously break it. In the next version of Ubuntu, Unity will operate on top of Gnome 3. Only then, it will probably be trivial to switch between Unity and gnome 3 shell.

---

### Post by pony-tail on 2011-04-28
The whole thing is , at present somewhat of a mess - but it will clear up in a year or so . This happened with the transition from Gnome 1.x to Gnome 2.x - different libraries , different interface , quite a bit of early confusion but it cleared after a couple of point releases as it will again .
I personally do not like Gnome shell or Unity but after the masses get hold of them and start tweaking them they Might just work .
There is a lot of code in a gui and things get missed or left out to make deadlines - maybe time will put them back .
To the OP . Your confusion is understandable and I believe that you will not be alone . 
I will try to clear some things up 
Gnome 2.x has a shell called panels ( the one you are familiar with ) 
Unity is built on Gnome 2.x and has Panels as a fall back  ( Ubuntu 11.04)
Gnome 3 has Gnome 3 shell as a shell ( the one you are Not familiar with )
The next Unity ( I have been told ) will be built on Gnome 3 without Gnome 3 shell . 
I also suspect there may be a Ubuntu 11.04.1 with some missed issues fixed 
But that is just a suspicion .

---

### Post by elcalamar on 2011-05-06
I installed Gnome shell from the PPA three weeks ago and it did break Unity. But an update today (May 6/11) from the PPA fixed it. I now can switch between Unity and Gnome Shell without issues.
The log-in screen has also been cleaned, and now it offers the option of Ubuntu and Gnome-Shell only. No more "Ubuntu classic".

Both shells are remarkably close. Gnome-shell is quite more polished, but still you get the occasional "gnome-daemon has closed unexpectedly", with Apport not being able to send the bug report because it is not a supported package.

---

