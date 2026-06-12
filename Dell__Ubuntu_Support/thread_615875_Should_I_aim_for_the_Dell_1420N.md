---
title: "Should I aim for the Dell 1420N?"
date: 2007-11-17
forum: Dell  Ubuntu Support
---

### Post by gamelord12 on 2007-11-17
I'm looking to get a laptop for use in class that'll last me the remainder of my 4 years in college (I'm a freshman at the moment).  I figured that getting a Dell laptop with Ubuntu would be good since Ubuntu offers modern OS features while taking up far less resources than Windows Vista for less money.  What I'd like to know is:

1) How does the battery life differ between an Ubuntu Linux laptop and a Windows Vista laptop?

2) Will I definitely be able to get Compiz-Fusion running fine on the X3100 easily, as in without manually editing configuration files?  I kind of want to be able to show off on my laptop in some ways...long story.

3) Is there a cheaper laptop that will suit my needs for the next 4 years (C2D/Athlon X2, 2 GB of RAM, decent graphics, not running XP) than the 1420N?

---

### Post by gamelord12 on 2007-11-17
bump?

---

### Post by Chayak on 2007-11-17
I don't know about that laptop but I personally use a Lenovo T60 with ubuntu on it and I've never been disappointed.  With the 9 cell battery I can easily go six hours on battery power while using wireless which will easily get me thorough a class or meeting.

My previous laptop was a Dell XPS and it would eat it's battery in about an hour.

---

### Post by fragos on 2007-11-17
I just bought a 1420n with Ubuntu and it performs beatitifully.  The only option I bought was the 9 cell battery.  The OS calculated time on battery is over 5.5 hours.  Performance is excellent.  Even huge programs like OpenOffice start up quickly.

---

### Post by gamelord12 on 2007-11-18
So does Compiz-Fusion work with all of its effects on that laptop?  If not, should I consider getting the other configuration of the laptop (the one that doesn't ship with Ubuntu) with a GeForce 8400?

---

### Post by joker2of5 on 2007-11-18
I have a Dell 1420n.  It came with ubuntu 7.04 pre-installed and I upgraded to 7.10

I like the computer fairly well but it does have some issues for which I am not pleased.   

First let me tell you that this is my first linux box and I have been a Windows  user for around 17 years.  The transition has brought me some anxiety, but overall I love Ubuntu and think it is much better than windows.

Now for the computer.   Compiz fusion does not work with this computer.  My understanding is the the x3100 graphics chip has been blacklisted.  I think there are some work arounds but I have not yet tried them as it is not that important to me.

The only other issue I have not resolved yet is the S-Video TV out doesnt work.

When I bought this computer I was also considering System 76.  I only went with this one because I get an employee discount from Dell through the company I work for.  

If I had it to do over again I think I would buy the System 76.  This is a good computer, but it does not "just work" 

I have not had the oportunity to use a System 76 computer so im not sure how it compares, but I still think that I would go with them and not Dell.

---

### Post by fragos on 2007-11-18
It works fine with 7.04 shipped by Dell.  Dell will provide an upgrade to 7.10 that will be fully compatible with the 1420n.  To date I've accepted all 7.04 updates from Ubuntu and have had no problems.  I use 7.10 on my desktop and will upgrade the 1420n as soon as Dell makes it available.  The 1420n dose "just work".  The wireless is amazing and even roams.

---

### Post by gamelord12 on 2007-11-18
When is this Dell 7.10 supposed to come out?  The desktop edition has been out for about a month now, and Dell still ships their laptops with 7.04.  Will I be able to download the upgrade or will I have to buy the computer after the update is available?  The new Macbook now has an X3100 and it's capable of some good graphics, so I'm failing to see why it would be any different on Linux, which is all in all a much lighter OS.

---

### Post by wnwek on 2007-11-18
Does the Dell 1420N offer bluetooth connectivity as well?

---

### Post by frbe0101 on 2007-11-18
I got a Inspiron 1420 for use in grad school (when I'm in the lab or class) for as long as possible (4-6 years I hope). I got it with the extra large battery and it does last for many hours (never ran it dry) and it should last for awhile, Also I plan to buy a backup battery discharge it to 40% and put it in a freezer until this battery starts to fail. Its best to buy a backup battery now while they are cheap and freeze it instead of waiting for when it fails and buy it when it not in optimum production at a higher price, or worse try to buy one when they don't produce them anymore.

---

### Post by gamelord12 on 2007-11-18
Hmm...how about Compiz-Fusion though?

---

### Post by frbe0101 on 2007-11-18
Other points I should add:

- Supposedly it has blue tooth but i have never gotten it to work (actually I have never tried to get it to work)
- I've upgraded to 7.10 with some problems, but I fix all that and it works great, all the fixes can be found on this forum and takes only minutes to do.
- After several required upgrades-downloads the ethernet connection is now stable.
- I have been amazed over and over again at how compatible ubuntu is, (Its no redhat that is for sure!) I had to do a powerpoint presentation recently and I pluged in the projector crossed my fingers and hit the Fn+F8 and boom work perfectly (turn on open office afterwards to make sure the presentation fits the screen right) then just unplug and push Fn+F8 and it went back to normal screen-size. Also I pluged in a powerpoint remote control I borrowed from a professor I told him it was unlike to work because this was linux, I plug it in and with no popup message demanding a driver or anything it simply worked perfectly and seamlessly, I was amazed.
- I never cared for the effects so I never ran fusion, so i can't say how good the graphics are (I have a home made game machine desktop for "graphics", the laptop is all business and no play in my opinion). 4 desktops with Cassini-Saturn backgrounds and wallpapoz is enough flar for me.
- I downloaded KDM (kubuntu) and run that as well, After trying it for awhile I found problems such as controlling the screen brightness, FN buttons don't work, sound control flacky, etc) so I stayed with gnome but with the benefit of being able to run KDM apps.

---

### Post by joker2of5 on 2007-11-19
> **fragos said:**
> It works fine with 7.04 shipped by Dell.  Dell will provide an upgrade to 7.10 that will be fully compatible with the 1420n.  To date I've accepted all 7.04 updates from Ubuntu and have had no problems.  I use 7.10 on my desktop and will upgrade the 1420n as soon as Dell makes it available.  The 1420n dose "just work".  The wireless is amazing and even roams.


As I said before I am quite new to Linux and Ubuntu.  So I upgraded my 1420n just a few days after I bought it.  Probably a mistake, but overall I really like it.

Just curious though, do the desktop effect on compiz fusion work with 7.04?

---

### Post by sciurus on 2007-11-19
Bluetooth works.

CompizFusion works but is disabled by default because it breaks playback of videos using xv. However, you can use gsteamer-properties to disable xv, then run ```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
``` and UBuntu will let you enable desktop effects.

---

### Post by gamelord12 on 2007-11-20
The wireless works fine, right?  Other than taking notes in class, connecting to the internet okay is the most important thing to me.

---

### Post by fragos on 2007-11-20
The wireless works great on my 1420n.  It even roams without any configuration.  It worked out of the box as did everything else.

---

### Post by frbe0101 on 2007-11-20
> **sciurus said:**
> Bluetooth works.

CompizFusion works but is disabled by default because it breaks playback of videos using xv. However, you can use gsteamer-properties to disable xv, then run ```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
``` and UBuntu will let you enable desktop effects.

Yeah because you questioned it, I tried to see if CompizFusion worked and with a little messing around it does, It worked back with 7.04 as well but I turned it off then just as I did now, simply because I have spartan aesthetics, personal preference nothing more. Never new about the video problem, good I kept it off then.

---

### Post by Sims2789 on 2007-11-20
> **Chayak said:**
> I don't know about that laptop but I personally use a Lenovo T60 with ubuntu on it and I've never been disappointed.  With the 9 cell battery I can easily go six hours on battery power while using wireless which will easily get me thorough a class or meeting.

My previous laptop was a Dell XPS and it would eat it's battery in about an hour.

Except for the mute button, my T61 with Ubuntu worked perfectly out-of-the-box. Also, the ThinkVantage button doesn't bring up a useless solution center in Ubuntu but I think that's a plus! :-D

---

