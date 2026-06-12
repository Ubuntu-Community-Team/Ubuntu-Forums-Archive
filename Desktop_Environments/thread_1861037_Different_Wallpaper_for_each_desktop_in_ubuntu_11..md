---
title: "Different Wallpaper for each desktop in ubuntu 11.10"
date: 2011-10-15
forum: Desktop Environments
---

### Post by Pampanga on 2011-10-15
I recently upgraded to ubuntu 11.10 Onieric Ocelot and really loving the vast improvement over the previous version. However, there's one minor issue i can't seem to find an answer for: Compiz's multiple wallpapers.

I followed this post for ubuntu 11.04:

[http://ubuntuguide.net/ubuntu-11-04-unity-enable-different-wallpapers-in-each-workspaces](http://ubuntuguide.net/ubuntu-11-04-unity-enable-different-wallpapers-in-each-workspaces), 

but when i got to /apps/nautilus/preferences, show_desktop entry doesnt exist. I searched for it and found a few entries already unchecked. 

How do you get multiple wallpapers to work in Oneiric? Cause the old ways of doing it doesnt work anymore. :confused:

---

### Post by card_ace on 2011-10-15
I'm working on the same problem.  I had it update overnight and when I came back this morning my wallpapers were gone (only had a black wallpaper and the icons are back).  After playing with the settings I got it to work at one point, but I lost my desktop bar and Unity.  I don't remember how I did it though.  Still experimenting, no luck yet.

---

### Post by jgrocha on 2011-10-15
Same here. Unable to set one wallpaper for each desktop. And I really had problems trying to revert after enabled the Wallpaper in ccsm.

---

### Post by card_ace on 2011-10-15
i just noticed that when I'm in gconf-editor and I'm looking at the "show_desktop" it tells me "This key has no schema".  further looking shows that everything under the "nautilus" grouping has the same message except for the "desktop-metadata" as it just doesn't open.
So 1: everybody getting the same results?
and 2: any suggestions?

---

### Post by SushiR on 2011-10-15
As for the "show desktop" entry in gconf-editor... it may be deprecated. Please try the following (just an idea, didn't try it myself yet): Install "gnome-tweak-tool" if you haven't already. On the left side look for an entry like "workspace" or something (don't know how it's called, I use german system language), and uncheck "Have file manager handle the desktop". Then go on to ccsm... I hope it works - let me know!

---

### Post by Pampanga on 2011-10-15
> **SushiR said:**
> As for the "show desktop" entry in gconf-editor... it may be deprecated. Please try the following (just an idea, didn't try it myself yet): Install "gnome-tweak-tool" if you haven't already. On the left side look for an entry like "workspace" or something (don't know how it's called, I use german system language), and uncheck "Have file manager handle the desktop". Then go on to ccsm... I hope it works - let me know!


I think you're right, it may have been deprecated. 

'Gnome Tweak Tool' is now called 'Advanced Setting' when you search for it in Ubuntu Software Centre. Once installed, Run it and look for 'Desktop' and Turn 'Have file manager handle the desktop' to OFF. 

VOILA!!! Works Like A Charm! :guitar:):P
THANK YOU THANK YOU THANK YOU!!

CHEERS!

---

### Post by SushiR on 2011-10-15
> **Pampanga said:**
> I think you're right, it may have been deprecated. 

'Gnome Tweak Tool' is now called 'Advanced Setting' when you search for it in Ubuntu Software Centre. Once installed, Run it and look for 'Desktop' and Turn 'Have file manager handle the desktop' to OFF. 

VOILA!!! Works Like A Charm! :guitar:):P
THANK YOU THANK YOU THANK YOU!!

CHEERS!I'm glad I could be of some help. You're welcome!

---

### Post by card_ace on 2011-10-15
took a bit of playing around with the different compiz tweaks, but its working great now.  thanks a ton!

---

### Post by Pioka on 2011-10-15
Can you please explain how you've successfully managed to do it?
I did turn off the "Handle..." in Advanced Tweaks, but whenever I press Enable this Plugin in
CCMS -> Wallpaper

nothing happens :(

---

### Post by Larkspur on 2011-10-15
> **Pioka said:**
> Can you please explain how you've successfully managed to do it?
I did turn off the "Handle..." in Advanced Tweaks, but whenever I press Enable this Plugin in
CCMS -> Wallpaper

nothing happens :(

As well as switching on the Wallpaper plugin, you have to switch on the .jpg plugin, then log out and log back in again.

---

### Post by jgrocha on 2011-10-15
Great!
It's working.
i) gnome-tweak-tool
Have file manager handle the desktop: Off
ii) ccsm
Wallpaper, and set the wallpapers...
Activate it (and also activate de JPG plugin)

At that's it! Not necessary to logout and login again.

Thank you all.

---

### Post by jammaj on 2011-10-16
Sorry, I know this thread is meant to be solved.

But...

After doing all of these things, I managed to get 4 different backgrounds, which is great.

However, things become unstable, even after logging in and out again.  For example, when I minimize a window, everything kind of freezes up. And there is also no right-click menu.

The original post makes reference to this guide:

[http://ubuntuguide.net/ubuntu-11-04-unity-enable-different-wallpapers-in-each-workspaces](http://ubuntuguide.net/ubuntu-11-04-unity-enable-different-wallpapers-in-each-workspaces)

The guide states that you need to deselect 'show_desktop' in gconf-editor. This setting is not present in 11.10, although you can do the same thing by installing Advanced Settings and turning off 'Have file manager handle the desktop'. 

The guide then says that you should install a new launcher, such as GLX-Dock. Is this essential, or is there a way that you can use the Unity launcher with the Wallpaper function in Compiz without everything going awry?

---

### Post by cracgor on 2011-10-21
I do not think this is solved.

I have tried all of the above steps:
1) Installed ccsm/extra plugins and advanced settings.
2) Changed advanced settings to not manage the desktop
3) Updated the wallpaper to have the exact same number of .jpg images as desktops and then activated the wallpaper setting.

The wallpaper turns to a solid black color for all workspaces. I of course have the .jpg support activated in ccsm. I've edited the number of desktops trying this with from 1 to 9 desktops under "general settings" in ccsm, adjusted the number of workspaces from 4 to 9, manually turned off desktop control in gconf-editor desktop-->gnome-->draw desktop, tried every different cube setting, and tried every desktop wall setting. The best I can do is the black screens. If I turn back on desktop control I get one workspace background that was defined using the normal "change desktop wallpaper" method of right clicking the desktop.

---

### Post by rakesh.swapna on 2011-11-07
I Have tried but nothing happened 
1. Installed Advanced Setting
--> 'Desktop' and Turn 'Have file manager handle the desktop' to OFF.
2.  CCSM --> Utilities --> Wallpaper --> Added 4 wallpapers --> Enabled -- Closed
3.  Logged off and logged in


Nothing happened, Please guide

---

### Post by card_ace on 2011-11-07
Alright I know its been a while since this was answered so I'll do my best, I'm by no definition an expert on this.

@jammaj: we talked about the "show_desktop" on the first page of this thread, its depreciated and no longer has an effect on the OS.  The right click issue you're having is because of the fact that there is physically no desktop there anymore, just the image.  The next best thing you can do is create a launcher icon directed at your desktop folder to access anything you have there easily.  Also, I have it working with Unity, there is no need to install another desktop manager.

@cracgor: I have the "draw_background" enabled in gconf-editor, not sure if that's your problem or not.

now onto what my configuration is:
1. not sure if this would affect anything, but I do have "show_desktop" disabled in gconf-editor.  I know its not supposed to, but better safe than sorry.
2. In Gnome-Tweak-Tools, now called "Advanced Settings" under the "Desktop" option I have every option turned off.
3. In CCSM I have:
     a. Both JPEG and Png enabled in the "Image Loading" section
     b. Desktop Wall enabled, NOT Desktop Cube under the "Desktop" section
     c. Ubuntu Unity Plugin enabled, though I believe I had to manually enable it after applying the other compiz settings.
     d. Also under "Desktop" I have Viewport Switcher and Expo enabled.
     e. Inside the Desktop Wall plugin, under the tab Viewport Switching, in the Non Sliding Windows option, I have "type=dock | type=Desktop | state=Sticky

Not sure if this will help anybody else struggling, I'm on a Dell Inspiron and I've got it working fine.  will keep trying to assist if I can.

---

### Post by Kapitän Rotbart on 2011-11-14
Unfortunately this trick won't work with EasyStroke AFAIK. It was annoying enough to have to whitelist EasyStroke in the notification area in the Dconf Editor to get EasyStroke working in the first place, I had to disable the Compiz Wallpaper so that I could have my EasyStroke working properly again. Anyone know of a workaround?

---

### Post by acarlstein on 2012-02-16
[-X  THIS IS NOT SOLVED!!!  [-X

We need a clean solution, not something that seems like fixed with duck tape.

            -----------------------------

By the way, please stop forcing the users to be your beta testers.

It would be nice to have in consideration that they had set up their computer in one way before changing everything.

We cannot have our computer stop working and spend hours or days to fix them every time there is a new version to update.

---

### Post by card_ace on 2012-02-17
Hey now, I've fixed a lot of things with duct tape; my phone, knife sheath, computer case, my truck . . .

anyways, I've definitely got it working, as do several other people.  I don't remember the order of the steps that I did to get it to this point, but once you get it you don't gotta mess with it anymore.  Basically just keep playing with settings and restarting the system, eventually you'll get it.  Everything you need is throughout this thread, just don't give up on it

---

### Post by teez on 2012-07-11
i used sudo gnome-tweak-tool

under Desktop, set have file manager handle the desktop to off. Then use Wallpapers in CCSM to choose your wallpapers.

Just move them up or down to change the desktops u want them on.

---

