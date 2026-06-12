---
title: "Pop-up Windows end up too large and cannot be resized."
date: 2013-07-10
forum: Desktop Environments
---

### Post by alphaamanitin on 2013-07-10
Hello Forum,

Sometimes, particularly when updates or the like pop up, if I do something like expand a pop-up window for more info, the window becomes too large.  By too large I mean that the buttons for things lik accept or cancel slip beneath my tool bar, even if I drag the window to the top of my screen, and I cannot resize the window because the areas to resize it are not availabe.  I have to hit tab or alt-c or whatever to get the appropriate buttons.  Any thoughts?

Id

---

### Post by dino99 on 2013-07-10
to resize, hover the mouse on the taskbar and right click to select what you need, then move the mouse either up,down,left or right, and click again to stop the resizing mode.

---

### Post by alphaamanitin on 2013-07-10
That is my point, the area where you hover your mouse to resize is off the screen.  I don't know what is going on with my computer.  For instance, when I open a pdf with the doc viewer, the view opens larger than my screen, you can see the document through my transparrent taskbar at the bottom of my window.  If I do something like, ctrl+f to search for words, the little box that opens is not even viewable as it is "below" the screen.  

For windows like the doc viewer I can simply hit the button to maximize the window and it goes to the normal full side mode.  If, however, it is a pop up like what occurs with updates, and has no button to resize, I cannot do anything.

~AlphaA

---

### Post by RadicaX on 2013-07-10
Have you changed the resolution of your screen? That happen to me when i first started on Ubuntu 11.10, I needed to manually change the resolution in it. If you can, find out your monitor and what resolution it is able to handle. Then try and size it from the settings to that.

---

### Post by alphaamanitin on 2013-07-11
I have never changed the resolution since I installed Xubuntu, and it is set on the maximum resolution for the screen, per the PanP9 specs.

~AlphaA

---

### Post by RadicaX on 2013-07-11
Then shrink it. That is sometimes what needs to be done. If you have to, you can press Super+T to pull up the terminal to adjust it in the shell. 

[http://anhe51.wordpress.com/2012/01/30/change-resolution-of-unknown-monitor-in-ubuntu-11-10/](http://anhe51.wordpress.com/2012/01/30/change-resolution-of-unknown-monitor-in-ubuntu-11-10/)

This is the commands I had used back then. Part of the reason I really think this is resolution, is because of it going off screen like that. 

Can you take a screenshot?

---

### Post by Dennis N on 2013-07-11
I looked at the PanP9 and the display is described as "15.6 in 720p High Definition LED Backlit Display ( 1366 x 768 )"

If that is correct, and with the vertical res. of 768, you MIGHT have the same problem as in this thread:

[http://ubuntuforums.org/showthread.php?t=2092723](http://ubuntuforums.org/showthread.php?t=2092723)

IF that is your problem, you will find a workaround in post #3. It refers to Lubuntu, but the same problem is seen in Xubuntu. If you upgrade to release 12.10 or 13.04 most of these issues are fixed, especially the open, save, and save as dialogs. They now retain their sizes across sessions.

---

### Post by alphaamanitin on 2013-07-12
> **Dennis N said:**
> I looked at the PanP9 and the display is described as "15.6 in 720p High Definition LED Backlit Display ( 1366 x 768 )"

If that is correct, and with the vertical res. of 768, you MIGHT have the same problem as in this thread:

[http://ubuntuforums.org/showthread.php?t=2092723](http://ubuntuforums.org/showthread.php?t=2092723)

IF that is your problem, you will find a workaround in post #3. It refers to Lubuntu, but the same problem is seen in Xubuntu. If you upgrade to release 12.10 or 13.04 most of these issues are fixed, especially the open, save, and save as dialogs. They now retain their sizes across sessions.

This sounds EXACTLY like my problem.  I don't really want to upgrade, I use this computer for my PhD thesis work and it is just a bit too much of a risk for me to upgrade in place.  It would take too much time to get all the programs back up if something went wrong, get the custom perl scripts for bioinformatics back up and all the dependencies, etc etc.  

Thank you though for this.

~AlphaA

---

### Post by Dennis N on 2013-07-12
> **alphaamanitin said:**
> This sounds EXACTLY like my problem...  I don't really want to upgrade...It would take too much time to get all the programs back up...  

~AlphaA

I hope the workaround helps. It may sound strange that reducing the system default font size will reduce the height of the dialog windows, but it does in releases 11.10 and 12.04. On one of my laptops, which has the same resolution as yours, the largest usable default font size is 11 with Xubuntu 12.04.

Good luck.

---

