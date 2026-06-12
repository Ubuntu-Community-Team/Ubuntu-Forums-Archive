---
title: "Xubuntu? Ubuntu?"
date: 2009-04-27
forum: General Help
---

### Post by YigalB on 2009-04-27
When would I install Xubuntu instead of Ubuntu?

---

### Post by prem1er on 2009-04-27
There are many articles written on this subject. In short,  Xubuntu is primarily for slower systems/people who don't like gnome desktop.  Xubuntu runs the Xfce desktop environment, which uses much less system resources.

---

### Post by YigalB on 2009-04-27
> **prem1er said:**
> There are many articles written on this subject. In short,  Xubuntu is primarily for slower systems/people who don't like gnome desktop.  Xubuntu runs the Xfce desktop environment, which uses much less system resources.

How do I define the line in between? is there a guideline that with X MHz of CPU, Y MB of DDR with certain speed, or hard disk cache? 
I am installing many PCc\s, many of them are old. I always think what performance limit should I consider.

Today I set my limit to P3 500MHz with 512MB DRAM level. So far, I used Ubuntu only. Does it make sense? 
Should I start using Xubuntu instead with the lower level PCs? 

The PCs are donated to kids mostly, ages 4-15.

---

### Post by mcduck on 2009-04-27
> **YigalB said:**
> When would I install Xubuntu instead of Ubuntu?

When you want to use XFCE4 as your desktop environment instead of Gnome.

Basically all Ubuntu variants are one and the same OS. They all just include different desktop environment by default, Gnome in Ubuntu, KDE in Kubuntu and XFCE4 in Xubuntu. Of course you can install any of these desktop environments (or all of them) on the same Ubuntu install if you want.

XFCE4 is a bit lighter on resources than Gnome and KDE are so it's able to run on slightly older hardware than the other two. But it's definitely a nice desktop environment and many people prefer using it on new computers as well so you shouldn't consider it as something made for old computers.

edit: there is no absolute rules to what you should use. If you are happy with the performance you get with Gnome, an like it more than XFCE, then use it. If you feel it runs too slow then try something lighter instead. It's really just a question of what *you* prefer.

However, Ubuntu has a minimum RAM recommendation of 384MB while Xubuntu's minimum RAM recommendation is 192MB (although they both will work with even less than that).

---

### Post by mb_webguy on 2009-04-27
If you're using Ubuntu and want to try the Xfce desktop environment, just install the xubuntu-desktop package in Synaptic or in the terminal using "sudo apt-get install xubuntu-desktop".  Then, at the login screen, go to Options->Select Session to choose whether you want to use Gnome or Xfce.

---

### Post by YigalB on 2009-04-28
Thanks for the answers. Obviously, I tried Xubuntu. It looks nice, but I got some small things which I dont understand if it's a "bug of feature":
- when I right click the aplications through the menu, I dont get the "send to screen/top/...." - instead the applications start to run. Is that a different approach?
- I installed the hebrew version. With Ubuntu, I get all menus and most of software in Hebrew. Here I got the main menu in English (on the left hand side...) and some of the sub menus in Hebrew. Is it because less resources were invetsed in Xubuntu?
- Also the menu structure was different. I got no "system" menu. I assume that this is just a cosmetic change.

Unless I made a mistake, I assume I will go back to the mainstream, playing the safe side.

---

### Post by Ugluk on 2009-04-28
> **YigalB said:**
> I installed the Hebrew version. With Ubuntu, I get all menus and most of software in Hebrew. Here I got the main menu in English (on the left hand side...)

It's true, localization quality in Xubuntu is much inferior.

And what is the 'System' menu?

---

### Post by YigalB on 2009-04-28
> **Ugluk said:**
> It's true, localization quality in Xubuntu is much inferior.

And what is the 'System' menu?

When the OS boots, there are 3 main menus: applications, places, system.

---

### Post by DJonsson2008 on 2009-05-04
One has to consider what depth of localization they need.
On the surface I think most of the menus are modifiable
in Xubuntu, as well you can create your own launchers.

8.4 had a nice feature of storing all menu and panel
items in XML which was handing for manually editing
and migrating using a text editor any text panel text.

---

### Post by DJonsson2008 on 2009-05-04
YigalB,

Be sure to check out and use Xubuntu 
Applications>Accessories>Appfinder

Or on terminal xcfe4-appfinder, it is
an instant solutions to being able to 
get any any app that may be on your system.

I also suggest loading Debian menu for 
more comprehensive menu listings.

Xfce Appfinder though can save massive time poking
around menus wished I would have had it on Ubuntu 
when I first started.

---

### Post by YigalB on 2009-05-04
> **DJonsson2008 said:**
> YigalB,

Be sure to check out and use Xubuntu 
Applications>Accessories>Appfinder

Or on terminal xcfe4-appfinder, it is
an instant solutions to being able to 
get any any app that may be on your system.

I also suggest loading Debian menu for 
more comprehensive menu listings.

Xfce Appfinder though can save massive time poking
around menus wished I would have had it on Ubuntu 
when I first started.
Thanks for the idea. However, I already installed Ubuntu instead of Xubuntu because of the missing Hebrew support (the PC is donated to a kindergarden age, so it must have local language).
I will install another PC soon - and will retry Xubuntu.

Thanks
Yigal

---

