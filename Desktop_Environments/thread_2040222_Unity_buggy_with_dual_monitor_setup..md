---
title: "Unity buggy with dual monitor setup."
date: 2012-08-10
forum: Desktop Environments
---

### Post by Candlehawk on 2012-08-10
Hello, I am on Ubuntu 12.04, I have two monitors, and while Unity 'works' with it, there are the following issues:

1.) The icon bar shows up on both screens, and one is blue, one is black.
2.) Clicking on a top bar menu immediately closes the menu (e.g. I click 'file' and as soon as the menu opens, it goes away)
3.) The lens menu (or whatever it is called, the thing where I search for applications) is pitch black. The icons still show up, and functionality is still at 100%, but it is pitch black and the little graphic that goes across the top of the screen is not there. 
4.) My mouse scrolls from screen 2 to screen 1 fine, but screen 1 to screen 2 causes my mouse to jump to the left side of screen 2, like the monitor is on the opposite side.

Here is a link to a screenshot  for it is too big to just post  with image tags in my opinion, which sums up all of visual problems that I am having with Ubuntu:
[http://i.imgur.com/VdOIy.jpg](http://i.imgur.com/VdOIy.jpg)
[IMG]http://imgur.com/VdOIy[/IMG]

---

### Post by QIII on 2012-08-10
I think 1 and 4 should be easy to fix under the display settings dialog.

You should be able to choose where the launcher appears: left screen, right screen or both.  Choose the left screen.

Also find the "Sticky edges" setting and turn that off.  The movement from right to left is held up by two things:  Sticky edges and the "force" required to get past the launcher on the right screen.  I think what may be happening is that you have moved the mouse far enough to apply the "force" and the cursor suddenly snaps across the left screen to catch up to the mouse input.

---

### Post by Candlehawk on 2012-08-10
When I try to open the 'vanilla' Display settings, it gives me a randr missing error and does not option. There is no option for anything Unity related in the Nvidia x server settings. I do not thing the issue with my mouse is due to sticky edges, as it only jumpts when I move from one to another, but when I move back across the same space, it does not jump. ways, and I have moved very slow across the screen only to have it jump right to me.

---

### Post by Candlehawk on 2012-08-13
I would just like to update saying that I have tried to re install Unity to no avail.

---

