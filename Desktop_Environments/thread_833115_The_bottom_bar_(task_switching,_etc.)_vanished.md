---
title: "The bottom bar (task switching, etc.) vanished"
date: 2008-06-18
forum: Desktop Environments
---

### Post by wanorris on 2008-06-18
Somehow, this morning the bottom bar of the Ubuntu GNOME desktop disappeared. I had set down my notebook, and when I picked it up, that bar had disappeared.

I'm pretty sure I hit something picking it up, so I'm assuming that's what caused the problem, but since I didn't see what it was, I don't know what to do about it. I tried right clicking on other desktop elements and I went through the Preferences section of the System menu, but I didn't see anything that looked like the right way to repair this.

I assume that this is a fairly straightforward thing to fix, but I have no idea how to go about it. Help would be greatly appreciated. Thanks!

---

### Post by Hamchan on 2008-06-18
Sounds like you deleted your lower panel. This is a easy fix if you still have your top panel, just right click on that and select "new panel" This will create a new panel along the bottom of the screen.

This new panel will not be your old panel as it will have nothing on it, but you can rebuild it to be just like your old panel. You right click on this new panel to add elements such as the window switcher (you get a choice of two but probably want the window selector)

---

### Post by PokieCarlwin_is_borked on 2008-06-20
hi,

I somehow ended up with the same problem, where i closed my computer and upon opening it I had no task bar, but I deleted one of them months ago so now I have nothing:confused: How do I fix this?  

thank you

---

### Post by VMC on 2008-06-20
> **PokieCarlwin_is_borked said:**
> hi,

I somehow ended up with the same problem, where i closed my computer and upon opening it I had no task bar, but I deleted one of them months ago so now I have nothing:confused: How do I fix this?  

thank you

Maybe this:

```
gnome-panel
```
Also could try going to System-Administration-System Monitor, and look for gnome-panel, and do a End Process

Here's a more severe fix

```
sudo rm -r ~/.gnome2
```
You might have to reboot to back panel back to life

---

### Post by PokieCarlwin_is_borked on 2008-06-20
VMC-

Only by using Ctrl Alt F1-F6 can I get a terminal to pop up, and where in the response 'cannot open display;
Run "gnome-panel --help' to see full list of available command line options.  and in response I get

 gnome-panel [OPTIONS]

and then I get errors when trying to open the 
'--help-gnome-ui'      'show GNOME GUI options'

I tried to add g infront of ui and put a space between all - but got  
'error: no such option: -g 
'-bash: -gnome-ui: command not found

---

### Post by PokieCarlwin_is_borked on 2008-06-20
-VMC

what will happen after i remove the '-/.gnome2' file ??? will there be something to back it up??

---

### Post by AndThenWhat on 2008-06-20
> **PokieCarlwin_is_borked said:**
> -VMC

what will happen after i remove the '-/.gnome2' file ??? will there be something to back it up??

Don't use that method.  Just go to CTRL+ALT+F7, which should be your default.  Once you are there, check this website out:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by PokieCarlwin_is_borked on 2008-06-20
Rad!!  THAT WAS QUICK AND EASY  THANK YOU SOOOO MUCH!!!!:KS:guitar::KS


> **AndThenWhat said:**
> Don't use that method.  Just go to CTRL+ALT+F7, which should be your default.  Once you are there, check this website out:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by PokieCarlwin_is_borked on 2008-06-22
I still seem to have a problem.   Andthenwhat  gave me a way to get my bars back but when I reboot I lose my panels again, WTF!!  I can restore them by his techniques, but how do I keep them from disappearing next time I reboot?

thanks in advance

---

