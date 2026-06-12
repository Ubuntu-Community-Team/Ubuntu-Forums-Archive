---
title: "Emerald broke"
date: 2009-01-03
forum: General Help
---

### Post by PLANETARY on 2009-01-03
Well I did a fresh install, 8.04, reboot, updated,reboot, envy driver. reboot compiz settings and emeralds and the fusion icon. I played around with it, install adobe 10 on website, reboot. no borders, emerald wont load. I did the fusion icon reload, emerald --replace, emerald --replace both with and without the & added to sessions. I reinstalled emerald, did a complete removal and install. still wont load, compiz does.

I also replaced emerald no with emerald yes in a compiz document.

whats wrong, what do I have to do to get it to work right?

Thanks

---

### Post by soro2005 on 2009-01-03
Not sure whether this is on your list of things you did already, but make sure that "Enable Window Decoration" is checked in the CompizConfig Settings Manager under "Effects." In the settings, you can also enter "emerald --replace" under Command.

Sorry if that's the first thing you did anyway.

---

### Post by PLANETARY on 2009-01-03
I tried that nothing worked. 

is there anything else I can do or should I do a reinstall?

---

### Post by soro2005 on 2009-01-03
well, first thing you could type emerald --replace into your gnome terminal and quote the output here. That should tell us a whole lot on why it's not starting.

You could also type metacity --replace, and you'll almost certainly have window decorations, only without the visual effects.

Reinstalling the operating system only b/c compiz doesn't draw window decorations is not really the linux style. There is a solution to your problem. Just provide more info.

---

### Post by PLANETARY on 2009-01-03
I type 'emerald --replace' in the terminal then switch to metacity to see what posted and nothing happens. I can get metacity working. when I type emerald --replace in metacity mode it still doesnt post anything.
Any thoughts?

---

### Post by soro2005 on 2009-01-04
What do you get if, while running Compiz, you enter
```
compiz-decorator --replace &
```
Also play with the "Select Window Decorator" settings in the fusion icon, try out with "Loose Binding" (Compiz Options), and finally, it might be worth a try to kill fusion icon and try without it.

You may also want to reinstall Emerald, and open the Emerald Theme Manager (emerald-theme-manager if you don't have a menu entry) to try with a different theme.

Btw: It seems that Emerald is on its path to extinction.

---

### Post by PLANETARY on 2009-01-04
I get nothing, then when i switch back to metacity i get
```
[1] 5771
margaret@margaret-desktop:~$ Starting emerald

```

I installed 8.10, installed compiz manager, emerald and fusion icon then restarted. nothing has changed. this is weird

is there a substitute for emerald?

btw the computer has
geforce 3
amd athlon 1400 @ 1440mhz

---

### Post by soro2005 on 2009-01-04
Did you open the Emerald Theme Manager and select a different theme? Have you installed a theme for Emerald at all? It doesn't seem to be coming with themes. You can find some [here](http://www.compiz-themes.org/index.php?xcontentmode=103)

As an alternative to Emerald, you can use the GTK Window Decorator with Compiz. Either right-click on the Fusion Icon and 'Select Window Decorator' --> GTK Window Decorator, or, in a terminal,
```
gtk-window-decorator --replace &
```
This assumes you're using Ubuntu, and not Kubuntu or Xubuntu.

---

### Post by PLANETARY on 2009-01-04
I cant get gtk decorator to work with compiz, if I could that would be fine.

I DL the highest rated theme, extracted it, ran emerald(after installing it again) imported the .emerald file. clicked it then reloaded it. nothing. 

metacity alone works. compiz then removes teh decorator. I even checked the decorator command in compiz and it was set to the gtk when emerald was uninstalled. 

I ran that command and nothing happend while compiz was active. just a number appeared after the command.

I am using ubuntu 8.10.

Thank you for your help

---

### Post by soro2005 on 2009-01-05
Ok, so two things come to my mind:
(1) Make sure you have the package compiz-gnome installed:
```
sudo apt-get install compiz-gnome
```
(2) In your first post, you describe how the problem first occured. It sounds like it was a result of you installing Adobe 10? Did you have window decorations *before* you installed Adobe 10? What is Adobe 10? The flash player plugin? How did you install it? What exactly did you do right before the problem first ocurred?

You write that "just a number appeared after the command." That means that the process is getting a process id and starting. From what I see, it does not seem to crash or abort.

---

### Post by PLANETARY on 2009-01-06
Well yes everything was working fine, I installed adobe flash 10 from adobe's website, .deb file. I have done that before and it has worked well. flash wouldn't seem to work so i rebooted, it works now. thats when the window decoration wouldn't work. 

however I decided to burn a new cd of ubuntu 8.10 and install it. I updated, reboot, then vid driver, reboot, then compiz and emerald reboot. flash 10 reboot. 

emerald still doesnt work.

I put in that code and it says it already has the latest version.

---

