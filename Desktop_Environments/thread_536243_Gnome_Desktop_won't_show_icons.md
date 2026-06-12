---
title: "Gnome Desktop won't show icons"
date: 2007-08-27
forum: Desktop Environments
---

### Post by idheath on 2007-08-27
I've just booted up my ubuntu workstation (7.04 feisty) and I can't see any icons on my desktop.

Everything else is fine and if I look in my Desktop folder everything is there as usual but I just can see any of them on the actual desktop.

Any ideas?

---

### Post by Lord Illidan on 2007-08-27
Perhaps a problem with nautilus?

---

### Post by EvergreyNY on 2007-08-27
ive only ever had that problem once or twice and after logging out and logging in again, it was fixed each time.

---

### Post by idheath on 2007-08-27
Logout/login doesn't fix it, neither does a reboot.

Also it's only affecting my user-id (my wife's is fine!).

---

### Post by sicofante on 2007-08-27
I'm installing at my customer's place and I'm having exactly the same issue. I've followed this howto (just making sure I was doing the right thing) but the desktop is empty.

---

### Post by idheath on 2007-08-28
Hi,

What howto are you referring to?

---

### Post by Tabenx on 2007-08-28
This happened to me before, i fixed it by taking out all the files in the Desktop folder then putting them on the desktop individually again (not the folder). Afterwards i found out it was a resolution problem and the reason i couldn't see it was because it was off the screen.

---

### Post by idheath on 2007-08-28
The plot thickens.........

I can't paste anything onto my (blank) desktop.

Also if I right-click on the desktop I don't get the normal pop-up menu (I get nothing).

---

### Post by jim_p on 2007-08-28
Because I can't describe it properly where to go, I made a screenshot.
This is a gconf-editor window, simply follow the path shown on the botton left corner
and see if the highlited option is "ticked"

The explanationon the bottom right side means (in greek) :
"Short description: Use nautilus to draw the desktop
Long description: If set to true then nautilus will show icons on your desktop"

Hope this solves your problem

---

### Post by idheath on 2007-08-28
Hi,

Thanks for the suggestion but this option is already ticked.

Cheers Ian

---

### Post by Tabenx on 2007-08-30
Hmmm, thats very odd indeed. This may sound stupid but its worth a shot, switch back to the Ubuntu Human Theme for a sec and see if the problem clears up, unless you use that as your main theme. I don't know if it will do anything but its worth a try.

---

### Post by idheath on 2007-08-31
I'm already running the ubuntu Human theme.

---

### Post by sicofante on 2007-08-31
> **idheath said:**
> What howto are you referring to?

Sorry, I forgot the links. It's in the [Desktop Tricks]("https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html") doc:

> **Show the Computer, Home, and Trash desktop icons in GNOME**[LIST=1]
[*]               Open the **Configuration Editor**, by running the program gconf-editor (see [the section called &#8220;Start a Program Manually&#8221;]("https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html#run-application")).
[*]               Choose                             apps->nautilus->desktop.
[*]               Tick the box beside *computer_icon_visible*, *home_icon_visible*, and *trash_icon_visible*. The changes take effect immediately.[/LIST]But that, as many said already, doesn't work. Maybe I've had a resolution problem too, I don't know. What I did (and worked) is the following:[LIST=1]
[*] Open the Places menu.
[*] Drag the icons you need into the top bar.
[*] Once the icons are in the bar, drag them to the desktop.[/LIST]Steps 2 and 3 are required because you can't drag the icons directly to the desktop (you should, but I guess that's one for Gnome's usability group).

I was afraid the icons would be shown with the infamous shortcut (alias) arrow, but no, they're clean and nice.

Hope this helps others.

---

