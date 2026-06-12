---
title: "fluxbox windows size"
date: 2007-03-04
forum: Desktop Environments
---

### Post by soloslinger on 2007-03-04
Hey all.

I am running a reasonably new install of fluxbuntu.  The problem I am running into is when I go to maximize a window, there seems to be a cap on how big the window can be, leaving part of the desktop exposed.  In other words, if I open Firefox, I cannot stretch the window size to all 4 borders of the screen.  This happens for other programs as well, such as Eterm.  I can move the windows themselves anywhere I want on the screen, they just don't seem to "maximize". 

I imagine it is possible that this is an issue with X but I have taken a peek at the xorg.config file and there doesn't seem to be anything to suggest a limit on window size.  

I can't imagine why this would be restricted though, and it makes using apps like firefox a pain because of the x-axis scroll bar.

any ideas would be appreciated
soloslinger

---

### Post by kerry_s on 2007-03-04
Sounds like you need to adjust your monitor settings. That's the buttons on the monitor itself.

---

### Post by soloslinger on 2007-03-04
hehe.  
Though I am new to ubuntu, I know enough to adjust the monitor.  Unfortunately for me though I do not know enough about how to take screenies(never was really necessary, most of my *nix system work is done from a prompt), nor does it seem I can accurately describe this.  

The background image extends well past the boundries of (for example) the firefox window.  It seems that in fluxbox, when the maximize button is used, it widens the windows as far as it can without overlapping the task bar and the 4 different window panes.(heck I don't remember what they are called -- desktops?)  So the boundries created by the top edge of the taskbar, and the left edge of the panes seems to be the limiting factors.

::EDIT:: Fluxbox calls them workspaces

Though I would rather not start fooling around with styles yet, perhaps that is the only way unless I can find a way to resize those so maximized windows want to extend the total distance horizontally.  Any help with this would be appreciated.


thanks to anyone in advance (if I made any sense at all)
soloslinger

---

### Post by kerry_s on 2007-03-04
Screen shots are easy and should be even easier since your familiar with the prompt.

Lets get what you need, in terminal->
sudo apt-get update
sudo apt-get install scrot

To use, in terminal>

scrot %T.jpg  <-screenshot of the whole screen
scrot -s -b %T.jpg  <-lets you select what to shot, you can just click on a window or hold the left click and drag to get a square section.
scrot -d 5 %T.jpg <-waits 5 seconds and then takes a screen shot, you can adjust the time to your needs.

Here's my menu setup entry's, if you just want to point and click->

```
[submenu] (ScreenShots)
 [exec] (Snap) {scrot %T.jpg}
 [exec] (Select) {scrot -s -b %T.jpg}
 [exec] (Wait 5) {scrot -d 5 %T.jpg}
[end]
```

I would put some screen shots of my fluxbox but that drive is acting up, you'll have to wait till i fix it. :)

---

### Post by soloslinger on 2007-03-04
Actually I figured it out.  What was happening is that the windows wouldn't maximize over the slit.  My ~/.fluxbox/init file is fairly basic, so I didn't know how or what to add the directive(?) list contained in it.  But after a couple hours of google searches I found the line to add to the init file:

session.screen0.slit.maxOver: True

..and that did the trick.  I think if I could run my comp at a higher resolution, it wouldn't have been such a problem; there would have been enough space on the screen for firefox to render pages better.  ...oh well...

I appreciate the help kerry_s, and I will use that screenshot program anyway, that looks neat!  Anyone possibly reading this know where I can obtain a complete list of things I can add to the init file so on my next encounter I don't have to dig too far?

hope this helps someone else
soloslinger

---

### Post by Up2Late on 2007-03-04
Don't you love Fluxbox.  I just installed it myself, over a bare Ubuntu server install.  Everything I want made for just a one gig install.  And transparency is sweet...


But I digress, I believe I have the answer to your problem.

Right click on the "desktop" section of the taskbar, then select "Maximize Over"


PS - While your reading this, you wouldn't happen to know of a good lightweight file manager that works well with Samba shares?  I mean Konqueror is great and all, but man does it install a lot of crap with it

---

### Post by Up2Late on 2007-03-04
OK, I was just a little late on my post... and you're solution is a more permanent one.  Personally, I prefer it not to cover the taskbar, but the init file is your friend.

No, I don't know of any one particular place to find an init guide to customization, but now that you've figured that out, it should be much easier to google anything you wish to alter.

---

### Post by soloslinger on 2007-03-04
(btw, that scrot package doesn't seem to exist - even after the update)

---

### Post by kerry_s on 2007-03-04
> **Up2Late said:**
> 
PS - While your reading this, you wouldn't happen to know of a good lightweight file manager that works well with Samba shares?  I mean Konqueror is great and all, but man does it install a lot of crap with it

Have you looked at " smb2www " , it says->

```
A Windows Network client that is accessible through a web browser
With this package you will be able to browse a Windows Network using a
standard web browser.  It is based upon the samba package.
```

---

### Post by kerry_s on 2007-03-04
> **soloslinger said:**
> (btw, that scrot package doesn't seem to exist - even after the update)

Have you turned all your repos on, it's in universe.

sudo youreditor /etc/apt/sources.list
uncomment the deb lines

---

### Post by Up2Late on 2007-03-04
Hey thanks, I will try that samba alternate tomorrow.

---

### Post by soloslinger on 2007-03-04
oops!  yeah that did it and scrot is installing as I type.

The more and more I toy with fluxbox the more and more I like it.  I do need the slit to be permnantly though, as my screen size is small, so I am okay with that.

thanks for all the help
soloslinger

---

### Post by yabbadabbadont on 2007-03-04
I use imagemagick to grab screenshots with fluxbox.  I have it setup in my ~/.fluxbox/keys file so that I can just hit the "Print Screen" button to grab the whole screen and Alt-PrintScreen (Alt-SysRq actually) to be able to select a window.  You could do something similar with scrot too.

```
Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
None Print :Execute import -window root ~/screenshots/screen-`date +%Y%m%d%H%M%S`.png
Mod1 Sys_Req :Execute import ~/screenshots/window-`date +%Y%m%d%H%M%S`.png
Mod1 F11 :Execute wallpaper-set-random
Mod1 F12 :Execute xmessage -center -default okay -file ~/.current-wallpaper-name
Mod4 t :Execute uxterm -fg gray75 -bg gray15 -fn "-xos4-terminus-medium-r-normal-*-14-*-*-*-*-*-iso10646-1" -g 125x50+0+0 -sl 1500
Mod4 r :Execute fbrun
Control Escape :RootMenu
Control Mod1 q :Quit

```

---

### Post by RedSquirrel on 2007-03-04
> **soloslinger said:**
> The more and more I toy with fluxbox the more and more I like it.


Glad to hear you're enjoying Fluxbox. I use it all the time. There are some links in my sig that you might find useful.

Cheers. :)

---

### Post by kerry_s on 2007-03-04
> **soloslinger said:**
> oops!  yeah that did it and scrot is installing as I type.

The more and more I toy with fluxbox the more and more I like it.  I do need the slit to be permnantly though, as my screen size is small, so I am okay with that.

thanks for all the help
soloslinger

You know you can put the slit on auto hide right? check your right click on a slit app or was it the slit itself. :confused:  That way you get the whole screen till you move to the right edge than the slit will pop out.

---

### Post by RedSquirrel on 2007-03-05
> **kerry_s said:**
> You know you can put the slit on auto hide right? check your right click on a slit app or was it the slit itself. :confused:  That way you get the whole screen till you move to the right edge than the slit will pop out.


The slit can be configured from the main Fluxbox menu:

**fluxbox menu -> Configuration -> Slit -> Auto hide**

and 

**fluxbox menu -> Configuration -> Slit -> Maximize Over**

for the issue soloslinger was dealing with earlier, i.e., the empty slit taking up the width of a few pixels on the right-hand side of the screen (or on whatever edge the slit is placed on).

There's even an option for "full maximization" meaning Firefox (or whatever app) will take up the entire screen when maximized:

**fluxbox menu -> Configuration -> Full Maximization**


To soloslinger:

In some cases there is no need to edit the init file itself since there are options right in the fluxbox menu. Of course, there's nothing wrong with editing the init file; whatever is easiest for you. So many options... :)

---

### Post by kerry_s on 2007-03-05
Yeah, i just put fluxbox back on last night. I think the drive i keep installing it on is about to go bad. Anyways i'm still picking my apps and setting up. So not much to look at. :)

---

