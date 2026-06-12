---
title: "need desktop environment overview"
date: 2007-04-28
forum: Desktop Environments
---

### Post by wog on 2007-04-28
Okay, so there's metacity... what does that do? Is that a window manager? What are the other window managers?

Then there's things like compiz, which seems to be loaded alongside metacity. What does compiz do that's different from metacity? What are the other kinds of software packages in its class?

Is there any other class of desktop environment software? What are those, and what are they called?

---

### Post by aysiu on 2007-04-28
Metacity is Gnome's default window manager.

Popular desktop environments are Gnome (which uses Metacity as a window manager) and KDE (which uses Kwin as a window manager). Xfce is a lighter-weight desktop environment (not sure what window manager it uses).

Then there are a lot of standalone window managers--IceWM, Fluxbox, Openbox, Sawfish, etc.

Read more here:
[http://xwinman.org/](http://xwinman.org/)

---

### Post by ComplexNumber on 2007-04-28
> Xfce is a lighter-weight desktop environment (not sure what window manager it uses).it uses its own called xfce4 or xfwm.

---

### Post by aysiu on 2007-04-28
Thanks for the clarification, ComplexNumber.

---

### Post by wog on 2007-04-28
So if Gnome uses Metacity as its default, what is compiz?

More to the point, why can Metacity and Compiz both be installed on the machine at the same time without interfering with each other? Can other Window Managers be combined without interfering with each other?

---

### Post by ComplexNumber on 2007-04-28
> **wog said:**
> So if Gnome uses Metacity as its default, what is compiz?
its a window manager that you can use instead of metacity. even though its default, this doesn't mean that it can't be changed.

---

### Post by wog on 2007-04-29
Okay. Somehow I got the impression Window Managers could be combined, but I guess not, huh?

Window Managers don't have anything to do with mouse controls, do they?

What's the difference between a Desktop and a Window Manager?

---

### Post by aysiu on 2007-04-29
This will answer your questions:
[http://penguinpetes.com/XWM_Guide/index.php](http://penguinpetes.com/XWM_Guide/index.php)

---

### Post by wog on 2007-04-30
That is being a very good overview.

I guess the only other question I have is: how do you switch between one Desktop Environment and another, or between one Window Manager and another? I mean, if I install Xfce, does it get rid of Gnome in the process, or can I return to Gnome if all does not go well? How much can I muck up my system by switching Desktop Environments and trying out different Window Managers?

---

### Post by aysiu on 2007-04-30
This will show you how:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by Nythain on 2007-04-30
hehe... now you get into desktop/login managers, such as GDM, and KDM... not sure what enlightenments is called, and i dont know if xfce has one of its own or if it just uses startx...

yes you can have multiple DE's installed, with options of choosing wich one to log into on your Login Manager... lke i have kubuntu wich uses kde and thus kdm... i have installed, but rarely ever use Enlightenment and Xfce... i just select wich one i want to log into at my log in screen.

Compiz is a window manager that generally loads well inside Gnome, but can be used inside KDE and probably Xfce.
Beryl is a fork/derivitave of Compiz that has tried to escape the reliance of gnome, so its more popular in other Desktop environments like KDE, though its gaining popularity even in gnome

KDE has default kwin or something like that, but the alternative aquamarine (wich i personally havent ever messed with)

and thats all i got on the subject, just a bunch of already stated info

---

### Post by aysiu on 2007-04-30
Enlightenment is a window manager
GDM and KDM are display managers (login screen)

---

### Post by Nythain on 2007-04-30
yeah, but i wasnt sure if enlightenment had its own login manager... ala entrance... i know that when i ran Elive it definately didnt use kdm or gdm or startx for that matter... thats what i was gettin at with that one

---

### Post by wog on 2007-04-30
Right now I'm pretty sure I'm down to a choice between Xfce and Fluxbox. I want the speed Gnome has gotten me used to having, but I also want the capacity to make my screen pretty when I figure out enough to do that. It's the artist in me, what can I say? :)

I got exposure to KDE when I tried SuSE. When Konqueror crashed, I had no alternatives because I didn't understand this stuff then. I'm still unsure I'd ever want to go back to a full KDE desktop. I'll take pieces of it, sure, but not the whole enchilada.

Ubuntu has been my one and only experience with Gnome. I like it a lot, but I apparently need an alternative until I can solve my theme problem.

So now I get to install both of those to decide which one I can cope with the best.
Wish me luck! :)

---

### Post by aanderse on 2007-04-30
hey i thought i would chip in here abit about the level of customization you can do.

i basically break a desktop environment down to 4 or 5 cattegories:
- window manager
- panels
- desktop manager
- session manager

all of these 4 components can be changed on gnome, kde, and xfce which is great for modularity.

example
default gnome uses metacity, gnome-panel, nautilus, and gnome-session respectively.  xfce uses xfwm, xfce-panel, xfdesktop, and xfce-session respectively.

now my current desktop is a combination of gnome and xfce because i use xfwm as my window manager, gnome-panel for my panels, xfdesktop as my desktop manager, and gnome-session as my session manager.  i don't have nautilus installed either, i have thunar for my file manager instead.  you can get real creative here though and use fluxbox or compiz as window manager, idesk or pcman to manager you desktop, the kde panel for your panels, and there are a few good session managers out there ... there are a seemingly endless comibination of desktops you can make.

hope this was helpful :)

---

### Post by wog on 2007-04-30
Well, okay.

I understand what a Window is.
I understand what a Desktop is.
What are panels, and what are sessions?

---

### Post by airtonix on 2007-05-01
+ panels are the bars that hold the "Applications, Places, System' menu you proly most familiar with, or the notifcation tray that your familiar with from windows otherwise known as the 'system tray'.
- the gray bar at the bottom of a windowsXP desktop is a panel.(for the life of me a cant remember what i used to call it.)
+ Gnome-panels can behave like drop down menus also.....xfce-panel deals with sub panels differently, iwish i could combine them both.
+ they can slide off the screen to the right,left, top or bottom.

+ a session is the state of your windows apps and panel widgets, it is the thing that tracks and 
remembers which window will show the next piece of data....a session manager controls which programs you start up after login, it (should) control the setting up of each users language settings(which it dies i think)

+ and once you come to shutting down for the day....the session manager will (if you ask it) remeber the location and state of each window you had open, and possibly( if the said application was programmed in line with gnome-ui specs) it will open the last document at the last place you edited....

at least that is the idea.

---

### Post by wog on 2007-05-01
So to get Xfce I do
```
sudo aptitude install xubuntu-desktop
```

and to get fluxbox I do
```
sudo aptitude install fluxbox-desktop
```

...right?

---

### Post by aysiu on 2007-05-01
I don't think there is a *fluxbox-desktop* right now.

---

### Post by RedSquirrel on 2007-05-01
> **wog said:**
> So to get Xfce I do
```
sudo aptitude install xubuntu-desktop
```and to get fluxbox I do
```
sudo aptitude install fluxbox-desktop
```...right?

There is no fluxbox-desktop (unless you count [fluxbuntu]("http://www.fluxbuntu.org")).

For Fluxbox, I would recommend:

```
sudo apt-get install fluxbox fluxconf feh
```(or you can use aptitude instead of apt-get if you want)

fluxconf is a graphical tool to help you configure Fluxbox. I've never used it. I find it easier to edit the configuration files directly, but it's up to you. feh is a program that can be used to set a wallpaper in Fluxbox.

If you do a search in Synaptic for "fluxbox", you'll find some other things you might want to install at some point. Examples are: fbpager and fbpanel.

Fluxbox looks very plain when you first install it, but you can make it look very nice with a bit of effort.

---

### Post by wog on 2007-05-02
So is it then just
```
sudo aptitude install fluxbox
```

?

---

### Post by Kent84 on 2007-05-02
Hi all,

I am new to linux too and have found this thread great. I have one question: What is beryl? I've heard it looks very nice and you can get features like expose on the mac with it.

---

### Post by RedSquirrel on 2007-05-03
> **wog said:**
> So is it then just
```
sudo aptitude install fluxbox
```?

Yes. That will give you everything you need to begin with. The other things such as fluxconf, fbpager, fbpanel are extras. As I said though, if you plan to set a background (wallpaper) you will need a separate program for that. feh is a nice one.




> **Kent84 said:**
> Hi all,

I am new to linux too and have found this thread great. I have one question: What is beryl? I've heard it looks very nice and you can get features like expose on the mac with it.


[http://www.beryl-project.org/](http://www.beryl-project.org/)

---

### Post by aysiu on 2007-05-05
I've moved the Samba question to [its own thread](http://ubuntuforums.org/showthread.php?t=433933).

---

### Post by ironcladlou on 2007-05-08
A lot of the information in this thread would be of great use in a sticky or in a wiki somewhere. Especially the breakdown on WMs, session managers, desktop managers, login managers, functions. I've always wondered exactly how they all relate and what their functions are, and how I can mix and match them. Now I know, and wish I had found it sooner.

---

