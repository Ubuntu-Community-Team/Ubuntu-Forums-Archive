---
title: "Beginner questions: finding programs, networking, installing programs from source"
date: 2005-09-03
forum: Desktop Environments
---

### Post by ragesoss on 2005-09-03
I've just recently started to learn linux and need some help:

Question 1: I just installed a program (DOSBox) through Synaptic, but I can't find where it is or how to run it.  In general, how do you access programs that aren't in the basic GNOME menus?  I noticed that after I installed the OOo 2 preview (version 1.9.79, I think) through Synaptic, it would show up in KDE menus, but Gnome would only go to the OOo 1.1.3.  How can I add buttons to the menus or desktop for the programs I use?

Question 2: I previously tried to install Debian (and the install was slightly corrupted by some bad RAM), and once I got the basic install running, it automatically detected my windows computer, which is connected through the same router.  I had put in the same name somewhere in the install as my windows workgroup, and I had access to the shared files on the windows (XP) computer, without having to configure anything.  How do I make it do this with Ubuntu?  I installed samba through Synaptic (and found it through the KDE menus) and put in the same workgroup name, but the windows computer isn't showing up.

Question 3: How do I install a program that I downloaded as source?

Question 4: I used Run Application and tried to install some things through apt-get, but nothing happened.  When I entered the command line, it simply closed.  What gives?

I haven't seen clear answers to these questions in the documentation, so any answers or links will be greatly appreciated.

[Edit] I just figured out the answer to the fourth question.  Obviously, I was mistaking Run Application for the Terminal command line.  Seems like that's a pretty important thing; why is it hiding in the second layer of menus?

---

### Post by sumadartson on 2005-09-03
> Question 1: I just installed a program (DOSBox) through Synaptic, but I can't find where it is or how to run it. In general, how do you access programs that aren't in the basic GNOME menus?

There's a fast and useful command line tool for locating files called locate. In order to use it you first have to setup its database you have to enter ```
sudo locate -u 
``` in the terminal. Then, you can run it from the command line by ```
locate thingToSearchFor
```. If you're completely new to the command line, but are interested in using it, see the links in my signature.

Installed programs usually have an executable file located somewhere in /usr/bin or a similarly named directory.

If you've just installed a program and nothing is showing up in your Gnome menu you have several options. Firstly, you can refresh your gnome panels by ```
killall gnome-panel
```. Secondly, you can install [smeg](http://ubuntuforums.org/showthread.php?t=38183&highlight=smeg) , a program to use for editing your gnome menu's.

> Question 3: How do I install a program that I downloaded as source? 

Ah, you'll be compiling and making. This is too big a subject to address here, but there's a decent, and probably too big howto [here](http://www.tldp.org/HOWTO/Software-Building-HOWTO.html) . If anyone knows of a less intimidating intro, feel free to add.

I hope this will at least get you underway. This is written is haste though, I didn't even have time to look at your second question.

---

### Post by mlomker on 2005-09-04
#1 -  Most things can be started by typing in its name on the command line.  You can find out where they were installed to by going into the properties of the package in Synaptic after they are installed.

#2 -  Your debian install probably had some add-ons that don't come with Ubuntu.  That's one of the primary differences between distributions.  At the risk of starting a holy war, I'd recommend that you switch to Kubuntu (Ubuntu with the KDE desktop) if you are more familiar with windows than linux.  Check out [Kubuntu Screenshots](http://shots.osdir.com/slideshows/slideshow.php?release=306&slide=33) and see if you prefer the look to that of gnome.  It's decidedly easier to browse Windows machines and probably has more of a look/feel that you're accustomed to.  If you like it you can apt-get install kdestop to retrieve it.  You'll want a fast Internet connection...I think it's 80 MB or something like that.

#3 -  Depending on the program, this can be quite difficult.  It's far preferable to find the program in Synaptic or download it as a .deb file (a debian package).  If you want to compile from source you'll need to apt-get install build-essential at a minimum.  Beyond that you'll have to figure out what other development file packages are required for that particular program (dependencies).  It's not trivial if you're new to linux.  Look for a prebuilt package or ask someone else to do it for you if it's important for you and not otherwise available!

#4 - Linux is not user-friendly.  It was designed by programmers for geeks.  Microsoft spends millions doing usability analysis for Windows...nobody does that for Linux unless you buy a commercial package like Xandros or Linspire.

---

