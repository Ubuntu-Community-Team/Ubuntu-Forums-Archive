---
title: "default display frequency not supported by monitor"
date: 2007-12-13
forum: Desktop Environments
---

### Post by MartijnBuijs on 2007-12-13
Every time I boot into Xubuntu by screen is scrambled and unreadable.

I have to:

1) disconnect the old monitor
2) connect a new one that supports 70Hz
3) pick a resolution @ 60Hz
4) unplug the monitor
5) plug in the first one again.

I have to do this every time I boot into Xubuntu.

Why isn't the display frequency not remembered at startup? How do I fix this? Editing xorg.conf did not have a positive effect. I suspect a different monitor is detected (because I switch them) and a default refresh rate of 70Hz is picked.

---

### Post by MartijnBuijs on 2007-12-15
I managed to boot into a valid resolution-refresh rate now:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-40
	VertRefresh	50-60
EndSection
```

I do not understand it though, it is back as it originally was. The only difference is that the default resolution is now 640x480. This also causes the login screen to be displayed improperly, the window is to small for the buttons, and the buttons to small for the text+icon.

Additionally, I can now no longer select 1024x768 or higher, anyone has an idea how to get that back working? Various configuration windows also do not fit on the screen, this is a real bugger.

Fixed:
*BTW, vi was giving me hell by corrupting the xorg.conf as I was typing, it kept inserting long strings of characters after pressing the Insert-key. I can delete these again, but a few times vi hung on it and I was forced to power down and start all over (missing string NULL terminator?). Could this have to do with the keyboard settings? Can someone give me some hints where to find a solution (google doesn't return good results)?*

I fixed this by going to Start > Settings > Keyboard Settings > Layouts Tab, then select "Generic 104-key PC". It was set to "Generic 105-key PC" before. Hope this may help someone. :)

The other problem persists tho.

---

### Post by MartijnBuijs on 2007-12-24
Please disregard the above fix for the vi problem, it is still broken. Since my terminal crashes back to login screen, it had to edit the xorg.conf file through the desktop environment. You need write privileges for this, try this:

1) Press Alt-F2
2) type gksu mousepad /etc/X11/xorg.conf

Then save the file, reboot.

-------------------

I managed to find the cause of the display trouble. Ironically Plug-n-Play is the bugger here, the trick was to switch to disable the Plug 'n' Play feature by selecting a monitor manually. This requires no file editing at all.

1) Go to Applications > Settings > Screen and Graphics
2) On the screens tab, click on "Model"
3) Select the "Monitor <resolution you want>" from the "Generic" list (or anything that does not contain the phrase "Plug 'n' Play"
4) Log out, and back in.

You may need to alter the display settings if the desktop is to large and moving the cursor around scrolls the screen:

1) Applications > Settings > Display Settings
2) There, select the same resolution you chose on the "Screen and Graphics" dialog

-------------------

One minor glitch however may cause the text on buttons and elsewhere in the desktop environment to become very small (or big) after the above change. To fix this, you need to set the virtual desktop resolution the same as the monitor resolution:

1) Press Alt-F2
2) type gksu mousepad /etc/X11/xorg.conf
3) scroll to the "Screen" section
3) change the "Virtual" setting to the current monitor resolution, e.g.
```
Virtual	1024	768
```
4) Save file, then reboot (logging out, then in may not always work).


I'll have to credit myself for this helpful monologue. ;)

To quote myself:
> I think the lesson learned here (for the CLI savvy) is not to direct users with problems to a vague command, config file editing (with all risks involved) when there is a single click solution in the desktop environment!

---

