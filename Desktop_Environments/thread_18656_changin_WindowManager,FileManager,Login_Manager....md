---
title: "changin WindowManager,FileManager,Login Manager..."
date: 2005-03-08
forum: Desktop Environments
---

### Post by lizardking on 2005-03-08
[SIZE=2]I was wondering if there is an **how to to change in the most fastest and no probelmatic way the  WindowManager,FileManager,Login Manager**  instead of default Gnome Desktop Envroiment ubuntu. Gnome is great but I want to try some new fast windowmanager....
[/SIZE]
 :-({|=

---

### Post by kamstrup on 2005-03-08
Create the file ~/.xinitrc and MAKE IT EXECUTABLE. Then list the programs that you want started upon login in it. I have one that looks like this:

bbpager -w &
bbkeys -w &
blackbox

This will start the two programs bbpager and bbkeys in the window manager blackbox. Make sure that you have &'s ending every line _except_ the last. 

The last program started is special in the way that X is stopped (ie. you log out) when this program stops. In my case this is when I exit the window manager :)

To log in using this new setup you have to pick the session named "Default" from the login screen. If you are in a terminal with no X, then 'startx' should do it.

I am not sure... but you might have to use the filename ~/.xsession instead of ~/.xinitrc. I always just link xseesion to xinitrc to make sure... Just do : 'ln -s ~/.xinitrc ~/.xsession'

Happy hacking!

---

### Post by landotter on 2005-03-08
[QUOTE=kamstrup]{some crazy technical stuff}[/QUOTE]

;)

Just kidding--what kamstrup wrote is true and should be of interest--but adding new window managers and environments can be as easy as firing up the Synaptic package manager and selecting KDE, XFCE, Fluxbox, Blackbox, FVWM, IceWM or quite a few more for install--if you install them using Synaptic (or apt in a term of course ;)) they'll usually be available in the login manager.

I installed Blackbox from source yesterday, and that was quite easy--I did have to edit a couple files to get it to show up in gdm--but I could also just login in "failsafe mode" and type "blackbox" and get a blackbox session... ;)

Install them all or just a few--most window managers like the *box ones, are tiny, and today's discs are huge--nothing wrong with having a change of scenery.

---

### Post by kamstrup on 2005-03-08
Hehe got a point there landotter =D

Just spent a few hours in front of a Slackware box. I forgot how easy it was. Kids nowadays... They get all they ask for... ;-P

---

### Post by landotter on 2005-03-08
[QUOTE=kamstrup]Hehe got a point there landotter =D

Just spent a few hours in front of a Slackware box. I forgot how easy it was. Kids nowadays... They get all they ask for... ;-P[/QUOTE]
 Hey, since you seem to be a sharper knife than I and mentioned bbpager & blackbox--you wouldn't have happened to get bbpager working with the last version of blackbox (0.7)?  I can't seem to find a gui pager to work with it. Hmm, perhaps there is a dockapp?

---

