---
title: "Evolution on Acer Aspire One"
date: 2009-01-07
forum: General Help
---

### Post by jadoti on 2009-01-07
Hello, 

I hope this question/issue is appropriate here, not sure where to gripe at...

I recently acquired an Acer Aspire One netbook, wiped Windows and installed Ubuntu 8.10 on it.

I like Evolution for email, and since it comes preinstalled, it's a win for me.

Like everyone else who has tried setting up Evolution initially, I had all the issues with buttons being off the screen and having to count 'tab' presses to get to the "Next" buttons, etc. with no way of resizing the setup wizard to all fit on the screen.  I crawled through this process, but eventually got it installed and had email. 

Today, however, I tried to go in and setup my calendar and such for use, and I get a related issue.  Once switched to the calendar view, it seems I can't click on anything.  As soon as I click on something (say the Task area to add a task) the whole window shifts up (allowing me to now see the bottom of the window and pushing the title bar off the top of the screen).  If I click it again, the whole window shifts down, bringing the titlebar back into view at the top of the screen, but hiding the bottom of the window off the bottom of the screen.

In both instances (clicking and it going up, or clicking and it going down) it doesn't seem to register that I clicked on the Task area to add a task.  The same thing happens when I click on the Mail button on the left side of the window to switch back to the mail view, the window just bounces up and down.

Does anyone have a fix for this?  This is no doubt an issue simply because of the AAO's smaller screen, but I would think that I should just be able to hit the Maximize button in the titlebar and have Evolution adjust itself to my available screen size. (Hitting the maximize button on the titlebar, by the way, causes the jumping up and down issue as well, as does any kind of right clicking on the titlebar or application).

Thanks in advance for any solution/advice.

Mike

[Edit] - Guess the app is opening up maximized.  When I right-click the app on the bottom toolbar in ubuntu (I don't know what it's called) and click 'unmaximize' the app is usable.  I'm going to leave the question up just incase anyone has any ideas how to use it maximized without the jumping issues.

---

### Post by dcstar on 2009-01-07
> **jadoti said:**
> Hello, 

I hope this question/issue is appropriate here, not sure where to gripe at...

I recently acquired an Acer Aspire One netbook, wiped Windows and installed Ubuntu 8.10 on it.
.........
It sounds like your PC install has a "Virtual" resolution that is greater than your actual screen resolution, so the whole screen scrolls when the app exceeds the available "Real" screen real-estate.

You may be able to get around this by modifying your /etc/X11/xorg.conf file - have a look at it and do a forum search for detailed instructions on changing things in it.

---

### Post by jadoti on 2009-01-07
Well, it's not the whole Ubuntu screen that scrolls up, just the application.  My ubuntu bars all stay in place...

---

