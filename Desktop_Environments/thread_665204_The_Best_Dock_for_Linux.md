---
title: "The Best Dock for Linux"
date: 2008-01-12
forum: Desktop Environments
---

### Post by loneowais on 2008-01-12
I have been switching Docks for almost a year now..
Once I was introduced to cairo-dock in these very forum, where I first time witnessed opensource community development. I was overwhelmed by it, I mean they started with little piece of code called cairo-dock & ended with one great app..it was awesome to see people contribute little code to the project & mae it big..:KS


 Ok..Now that I'm done with the little story of whatever..Let me introduce you to something that has really taken the shape of what it was intended to be...

Its the cairo dock.....its awesome...Much bettter & faster than Avant Window Navigator 

 [http://developer.berlios.de/project/showfiles.php?group_id=8724  ]("http://developer.berlios.de/project/showfiles.php?group_id=8724")




After installing add "cairo-dock" to your sessions, so that it starts automatically

---

### Post by staticvoid on 2008-01-12
cool thanks!!

I've only tried kibadock and awn

i'll check it out. i've always hated docks... lol

sv

---

### Post by exactopposite on 2008-01-12
looks interesting. i'm pretty satisfied with AWN right now, but i might check it out.

---

### Post by CupAnoodleS on 2008-01-18
when i download the .deb and run it i get an error
"Error: Dependency is not satisfiable: libglitz1"
help plz "/
[img]http://img401.imageshack.us/img401/5226/screenshot1nv1.png[/img]

---

### Post by PeterJS on 2008-01-18
> **CupAnoodleS said:**
> when i download the .deb and run it i get an error
"Error: Dependency is not satisfiable: libglitz1"
help plz "/


Are you having trouble installing other software with apt? libglitz1 is available in the main Ubuntu repository. You should be able to install libglitz1 with:
```

sudo apt-get install libglitz1

```
After that try installing Cairo Dock again.

---

### Post by Mysticpriest on 2008-01-25
how do I add this to my desktop after the install?
Where do I find it to launch it?

---

### Post by wolterh on 2008-02-04
Well, just hit <alt>f2 and type in cairo-dock
I don't know owhy you would want it on your desktop.
Go to Preferences > Sessions > Startup
And add an entry with the command cairo-dock. This will launch the dock everytime you turn on the computer

---

### Post by fatbuttlarry on 2008-02-04
Amazing thread.  I've been using avant-window-navigator for months, and its ok, but not half-as thought out as cairo.  Thank you!!!! This is great.

-Tres

---

### Post by tom957 on 2008-02-04
wow, i already like this one way more than awn. it's quick!

---

### Post by puelocesar on 2008-02-05
Last time I checked Cairo-dock wasn't truly a dock, it was just a launcher of applications.

A docker is more than that, on Mac, the dock is an application launcher and a kind of taskbar, where you and see what applications are open, see the status of the applications and switch between applications.

On AWN, i can do almost all of those things, but it depends on composite enabled and it's very very slow, so I can't use it..

And a last thing, the nice part of a docker isn't the effects, it's the usability features, because you have a more rich media for showing open applications than a taskbar, so you can have a more "organic" way of seeing what apps you are working at.

The attachment exemplifies that.

---

### Post by walkerk on 2008-02-05
> **puelocesar said:**
> Last time I checked Cairo-dock wasn't truly a dock, it was just a launcher of applications.

A docker is more than that, on Mac, the dock is an application launcher and a kind of taskbar, where you and see what applications are open, see the status of the applications and switch between applications.

On AWN, i can do almost all of those things, but it depends on composite enabled and it's very very slow, so I can't use it..

And a last thing, the nice part of a docker isn't the effects, it's the usability features, because you have a more rich media for showing open applications than a taskbar, so you can have a more "organic" way of seeing what apps you are working at.

The attachment exemplifies that.

You can show tasks with cairo-dock now...

---

### Post by puelocesar on 2008-02-06
And can I run it without composite? :P

Composite is slow on the nv6200 that I use at work.. And I use really a lot of apps, so a docker is always better for this than taskbars...

[edit] well, so it's time to test it again! ;)

[edit2] walkerk , thanks for the reply

---

### Post by broekskw on 2008-02-06
this look great, but in a terminal when i type in cairo-dock and select the type of layout,look good but then close the terminal it goes away because i shut down the terminal, how to i set it up to stay??:lolflag:

---

### Post by purpleberries on 2008-02-06
^ALT + F2 and type cairo-dock

One reason I like Cairo over AWN is it has a fisheye zoom hover effect. Also, every time I try AWN it seems too slow and buggy for me.

---

### Post by broekskw on 2008-02-06
alt + f2 dose not work for me ubuntu 7.10.need to keep the terminal open for this to work all the time:guitar:

---

### Post by KhaaL on 2008-02-06
so nice... I'm already contemplating replacing AWN with this!

EDIT: just a question, to me cairo-dock seems a bit thick... how do i make it slimmer?

---

### Post by puelocesar on 2008-02-06
> **walkerk said:**
> You can show tasks with cairo-dock now...

I installed version 1.4.6.3 on Ubuntu Gutsy and it doesn't have taskbar capabilities.

And yet I get a black background because it needs composite..

---

### Post by syms on 2008-02-06
> **broekskw said:**
> alt + f2 dose not work for me ubuntu 7.10.need to keep the terminal open for this to work all the time:guitar:
u need press alt key not in right side, but in left side, caus right alt dont work

---

### Post by robucf on 2008-02-06
Awesome dock, much better than awn.

Here is a community doc on the install I found:

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by broekskw on 2008-02-06
just got home from work:guitar: syms my alt key on the left or right side both do not work for this, the only way to get this to load is from a terminal and then have to leave terminal open for it to stay:confused:

---

### Post by Gourgi on 2008-02-07
> **broekskw said:**
> just got home from work:guitar: syms my alt key on the left or right side both do not work for this, the only way to get this to load is from a terminal and then have to leave terminal open for it to stay:confused:
**type : **
```
cairo-dock &
```

that puts cairo-dock as background process

---

### Post by syms on 2008-02-09
> **broekskw said:**
> just got home from work:guitar: syms my alt key on the left or right side both do not work for this, the only way to get this to load is from a terminal and then have to leave terminal open for it to stay:confused:
hmm, somethink is really strange here, every ubuntu release i have (ubuntu/kubuntu/xubuntu feisty/gutsy) alt + f2 working fine.

---

