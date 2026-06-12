---
title: "Xubuntu Panel Questions"
date: 2011-05-05
forum: Desktop Environments
---

### Post by buster2209 on 2011-05-05
So Unity did my head in and Gnome3 didn't fair much so I'm now on Xubuntu..... which I like!

I have a few questions though......

1 - The lower panel.  How can I change this to show the icons of the windows that are open?

2 - How can I arrange the icons on the top panel?  They want to snap left or right all the time........

Thanks in advance!

---

### Post by Toz on 2011-05-05
1. Right-click the panel, select Panel then Add New Items. Select Window Buttons from the list and click on the Add button.

2. You have to use separators (add them the same way as #1). They are probably snapping left or right because the existing separator is set as an expanding separator. Right-click the panel, select Panel then Panel Preferences. On the Items tab, you can see where the separators are and how they are configured.

---

### Post by Toz on 2011-05-05
Perhaps this might help as well:

[http://docs.xfce.org/help/xfce4-panel/C/preferences.html](http://docs.xfce.org/help/xfce4-panel/C/preferences.html)

---

### Post by buster2209 on 2011-05-05
> **Toz said:**
> 1. Right-click the panel, select Panel then Add New Items. Select Window Buttons from the list and click on the Add button.

That shows the open windows *with the text*.  I just want to see the icon.....

> **Toz said:**
> 2. You have to use separators (add them the same way as #1). They are probably snapping left or right because the existing separator is set as an expanding separator. Right-click the panel, select Panel then Panel Preferences. On the Items tab, you can see where the separators are and how they are configured.

I removed all the seperators but when I right click on the applet and select 'move' then drag it where I want, it still snaps back to where it was......

---

### Post by Toz on 2011-05-05
> **buster2209 said:**
> That shows the open windows *with the text*.  I just want to see the icon.....

Right click the "Window Buttons" section and select Properties. Uncheck the "Show button labels" option.


> I removed all the seperators but when I right click on the applet and select 'move' then drag it where I want, it still snaps back to where it was......

I guess you're referring to a free placement - leave it where you put it? I don't believe that option exists. You'll have to make liberal use of the separators to get it as close as possible.

---

### Post by buster2209 on 2011-05-06
> **Toz said:**
> Right click the "Window Buttons" section and select Properties. Uncheck the "Show button labels" option.

Thanks, that worked a treat!

> **Toz said:**
> I guess you're referring to a free placement - leave it where you put it? I don't believe that option exists. You'll have to make liberal use of the separators to get it as close as possible.

Is there not an option to centre or align left/right?

---

### Post by Toz on 2011-05-06
If you want to align right, put an expanding separator to the left of the icon - this will force it to the right. To align left, put an expanding separator to the right. Put an expanding separator on either side to centre it. Keep adding expanding separators to move the icons left or right. 

I know, its clumsy.

---

### Post by buster2209 on 2011-05-06
> **Toz said:**
> If you want to align right, put an expanding separator to the left of the icon - this will force it to the right. To align left, put an expanding separator to the right. Put an expanding separator on either side to centre it. Keep adding expanding separators to move the icons left or right. 

I know, its clumsy.

Haha, yes it is but it works!

Is there any way of getting a windows preview when hovering over an icon?

Also, XFCE remembers what was last running and loads it when I reboot.  How can I turn this off?

And one final one; how can I get a newly opened window to be centered on the screen?

---

### Post by Toz on 2011-05-06
> **buster2209 said:**
> Haha, yes it is but it works!

Is there any way of getting a windows preview when hovering over an icon?
Not that I am aware of with built-in XFCE functionality. The closest you can get is to draw the frames of the windows when you hover. Have a look that Window Buttons properties screen again and select the "Draw window frame when hovering a button" option. I believe awn lets you do that. Have a look at: [http://www.webupd8.org/2010/12/avant-window-navigator-gets-live-window.html](http://www.webupd8.org/2010/12/avant-window-navigator-gets-live-window.html)

> Also, XFCE remembers what was last running and loads it when I reboot.  How can I turn this off?
Go to Settings->Settings Manager and select the "Session and Startup" icon. On the General tab there is an option to "Automatically save session on logout".

> And one final one; how can I get a newly opened window to be centered on the screen?
Settings->Settings Manager->Window Manager Tweaks. Look at the Placement tab.

---

### Post by buster2209 on 2011-05-06
Thanks for all your help.  I've just moved from Ubuntu to Xubuntu (as Unity and Gnome3 just weren't for me) so your help is appreciated.

---

### Post by Toz on 2011-05-06
No worries. Enjoy xubuntu.

---

