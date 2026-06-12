---
title: "Is there gnome-alike &quot;notification area&quot; in Cairo-dock?"
date: 2009-07-25
forum: Desktop Environments
---

### Post by vickoxy on 2009-07-25
Hi, i try to replace gnome panels with conky and cairo-dock. Is there some  gnome-alike "notification area" for Cairo-dock?
Thanks

---

### Post by balaknair on 2009-07-25
Right click Cairo-dock> Configure> Categories--> Desktop> Systray

You will have to remove the regular Gnome-panel system tray though(just right click on the left corner of the system tray> remove from panel), since I doubt if both will run properly together.

---

### Post by vickoxy on 2009-07-25
> **balaknair said:**
> Right click Cairo-dock> Configure> Categories--> Desktop> Systray

You will have to remove the regular Gnome-panel system tray though(just right click on the left corner of the system tray> remove from panel), since I doubt if both will run properly together.

Thanks, i tried, but i can not delete this last panel. When i choose systray it popups empty with message "try to steel icons" or something like that. After that, there is bluetooth, batery and wifi applet on this little systray but i can not delete panel...

---

### Post by balaknair on 2009-07-25
I don't use Cairo dock myself, I prefer the two-panel layout, but I just tried deleting the Gnome-panel systray and running the cairo-dock one.
It seems to work OK, except that by default the systray seems to be detached from the dock. Use Alt+Left click to move it to where you want it to be.

So what I suggest is first removing the gnome-panel notification area, then enabling the cairo-dock systray.

---

### Post by vickoxy on 2009-07-25
Thanks i did, it, but i wan to completely remove panels-so i would need this notification area (where are listed all open apps-i do not how it is called english/Fensterliste 2.26.0/ windows list area...), and to put some applets that aren´t in cairo-dock. Is something like that possible?

And still,  i can not remove this last panel...?

---

### Post by balaknair on 2009-07-25
If you mean the Window-list applet in the Gnome-panel, it's called the taskbar in Cairo-dock.
Cairo-dock> Configure> Behaviour> Taskbar

Removing the panel: You ought to be able to delete it, maybe there are some locked items on the panel stopping you?

---

### Post by vickoxy on 2009-07-25
> **balaknair said:**
> If you mean the Window-list applet in the Gnome-panel, it's called the taskbar in Cairo-dock.
Cairo-dock> Configure> Behaviour> Taskbar

Removing the panel: You ought to be able to delete it, maybe there are some locked items on the panel stopping you?

Thanks for answers. Well, taskbar is activated, but i see no such window full of app/places. Is this taskbar to see somewhere on dock as independent icon?

---

### Post by balaknair on 2009-07-25
The taskbar will just show up as a group of icons(repesenting open windows) or thumbnails on the dock. There won't be any text description visible till you mouse over. 
See the screenshots for a better idea.
The arrows in the first image point to the windows I have open, and the second image shows the window title that pops up when you mouse over the icons

---

### Post by vickoxy on 2009-07-28
Systray:

anyway to change background and to move away popup icons window (once activated it want hide itself)?

---

### Post by balaknair on 2009-07-28
I'm afraid I couldn't figure out a way to change background, though I don't seem to have a problem with the pop-up, it appears on mouseover and disappears when I move the cursor away.

---

### Post by vickoxy on 2009-07-28
> **balaknair said:**
> I'm afraid I couldn't figure out a way to change background, though I don't seem to have a problem with the pop-up, it appears on mouseover and disappears when I move the cursor away.

Thanks for answers. Can i ask what setups do you have (normal, layer...), and is it detached or attached (i want to have it on dock)? :D

---

### Post by balaknair on 2009-07-28
I'm not too sure about what you mean by normal/layer- are you referring to Widget layer?
I'm just used it as a normal desklet(not on the widget layer), and had it attached to the dock(in this mode the systray app icons were hidden except when the pop-up appears on mouse-over).

---

### Post by vickoxy on 2009-07-28
Yes, something like that. Well if i click on systray it will open that little window with bt, network and battery icons (sse picture i uploaded), but then it won´t go away-no metter where or what i click. ....:confused:

---

### Post by balaknair on 2009-07-28
I'm not on Ubuntu right now, browsing from my phone, but I'll give it another look when I get home. I just used the default settings except for attaching it to the dock.
I'll have a look at the basic dock settings too.

---

### Post by thelaughingbuddha on 2009-07-28
> **vickoxy said:**
> 
And still,  i can not remove this last panel...?

*"Run gconf-editor, edit the key /desktop/gnome/session/required_components_list, and erase its content("panel"). Restart your session."*

This suggestion among others are available by right clicking on Cairo dock and selecting :**Cairo-Dock -> Configure -> Behavior -> Help**

It worked for me. Sure hope it works for u :D

---

### Post by fabounet on 2009-07-29
+1
and reading the "about" dialogs of applets is useful too, you would see that right-click shows the systray and middle-click hides it. ;-)

---

### Post by vickoxy on 2009-07-29
:oops:

Well as i said many times-i am really newbie to ubuntu-i use it just for 3-4 (linux for 7 months) months, so i do not know how/where to find some adjustment options (because, almost everything is adjustable-i used before only MacOS-there is nothing like these options in Linux). Sometimes is very hard for me to see some things, that are for Linux users just normal (gconf-editor..., terminal...). 

So, i apologize for me to be so ignorant and boring-but, eventually, i will learn to use linux...

Thanks for help

---

### Post by vickoxy on 2009-07-30
Another question-is it possible to change text size in Keyboard Plug-in? I changed background picture and want to have smaller font size that fits into the background picture. I tried to change size in applet settings, but nothing...

---

### Post by vickoxy on 2009-07-30
Panel options missing-does anyone knows what should stay in original output for "panel" there to bring back gnome panel?

Thanks

---

### Post by vickoxy on 2009-07-30
Something is odd-if i type gnome-panel in terminal i got two original panels back, but after i close terminal they dissapeared. Output is here:

anone knows what is this, and why the panels could not stay there?

---

### Post by fabounet on 2009-07-30
the text in the keyboard-indicator applet is enlarged to fit the icon.
so sorry there is no way to make it fit your image; this could be a new feature to add to this applet.

---

### Post by kutalion on 2010-08-01
> **vickoxy said:**
> Something is odd-if i type gnome-panel in terminal i got two original panels back, but after i close terminal they dissapeared. Output is here:

anone knows what is this, and why the panels could not stay there?

It's not odd. This app runs in terminal as you commanded it that way. Try Alt+F2 and make sure you don't hit the "run in terminal tick" (

---

