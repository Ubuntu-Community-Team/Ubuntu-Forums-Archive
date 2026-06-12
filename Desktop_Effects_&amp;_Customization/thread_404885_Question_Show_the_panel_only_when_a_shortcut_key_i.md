---
title: "Question: Show the panel only when a shortcut key is pressed?"
date: 2007-04-09
forum: Desktop Effects &amp; Customization
---

### Post by dzv on 2007-04-09
I would like to have a completely clean, uncluttered OS interface, and one of the things I would like is to have no panels, taskbars, etc on the screen until I want them to appear.  The idea being that all my commonly used apps would be on a kiba-dock, or all with keyboard shortcuts.  But there are some times when I want to see the whole panel to access other apps, settings, etc.

I know there is the autohide option, but I don't know of any keyboard shortcut to make the panels unhide without mousing to the edge of the screen.  I also don't really want the panel to appear with mouse-over, anywa.

I think it would be cool to have a desktop that people can't figure out how to use, so they can't mess up my stuff while I'm not looking :)  Without a panel or any kind of menu bar, they wouldn't be able to run any apps, or change any settings, etc.

---

### Post by raja on 2007-04-09
It is an interesting idea, sure. I can see how that can be done. I wrote a shell script to toggle the autohide property from true to false and vice versa. Then I can bind a shortcut key to this script to do exactly what you wanted. Did you want this to work for one panel or for the top and bottom panels ?
I will check things again and then show you the script.

---

### Post by GSF1200S on 2007-04-09
> **raja said:**
> It is an interesting idea, sure. I can see how that can be done. I wrote a shell script to toggle the autohide property from true to false and vice versa. Then I can bind a shortcut key to this script to do exactly what you wanted. Did you want this to work for one panel or for the top and bottom panels ?
I will check things again and then show you the script.

Ha.. I was thinking this would be a good idea, except doing so with a panel on the desktop. I cant figure out for the life of me how to get a panel on the desktop where I can get wifi info, a system monitor etc, to be attached to the desktop...

Apparantly, you guys already know how to do that. Would it be too much trouble to point to a reference that helps me with this?

---

### Post by raja on 2007-04-09
> **GSF1200S said:**
>  I cant figure out for the life of me how to get a panel on the desktop where I can get wifi info, a system monitor etc, to be attached to the desktop...


Are you using gnome or KDE? Setting up system monitor and any other information you want on the panel is very straightforward. In gnome, you can right click on the panel, select "add to panel" and choose one of the available applets.

---

### Post by gaspar on 2007-04-09
dzv, I got this from *[The Gnome Acessibility Project]("http://developer.gnome.org/projects/gap/keynav/panelnav.html")*:
Additionally, Ctrl+F10 (or some other suitable shortcut) gives focus to the menu panel.[...]

When a panel has focus:
- the panel is unhidden, if it was hidden when it received focus[...]

Is that what you´re looking for?

---

### Post by raja on 2007-04-09
Hi Gaspar,
The page you have linked to is a proposal from 2001. Do you know of any such shortcut is implemented actually?

---

### Post by GSF1200S on 2007-04-09
> **raja said:**
> Are you using gnome or KDE? Setting up system monitor and any other information you want on the panel is very straightforward. In gnome, you can right click on the panel, select "add to panel" and choose one of the available applets.

Oh yeah, I know how to customize the taskbar. I was referring to the actual desktop space with my wallpaper, etc. I can manage conky, but its not written to the desktop layer. Its its own transparent window, but if I put a shortcut on it, it dissapears...

I use GNOME. I would much rather use XFCE, but I cant. Ive tried posting on these forums like 3 times, but know one apparantly knows how to fix XFCE problems. I cant get my connections to work...

While were on GUI subject, you guys have any lightweight, fast, sleek GUI's I could consider? Ive heard XFCE is good, but Ive also been told that its a waste running a lightweight GUI on my system because its pretty powerful (listed in sig).. Any ideas??

---

### Post by raja on 2007-04-09
> **GSF1200S said:**
> I was referring to the actual desktop space with my wallpaper, etc. I can manage conky, but its not written to the desktop layer. Its its own transparent window, but if I put a shortcut on it, it dissapears...

I use GNOME. I would much rather use XFCE, but I cant. Ive tried posting on these forums like 3 times, but know one apparantly knows how to fix XFCE problems. I cant get my connections to work...

I am not sure I still understand exactly what you want. But if you mean a panel on the desktop where you can put shortcuts for applications, you can try the launcher applet in gdesklets. 
> 
While were on GUI subject, you guys have any lightweight, fast, sleek GUI's I could consider? Ive heard XFCE is good, but Ive also been told that its a waste running a lightweight GUI on my system because its pretty powerful (listed in sig).. Any ideas??

The good thing is that it easy to try out the different desktops. I have tried openbox, fluxbox and xfce. You just have them as separate sessions and remove them if you dont like it. Also worth giving a try is E17 (enlightenment).

---

### Post by raja on 2007-04-09
> **dzv said:**
> 
I know there is the autohide option, but I don't know of any keyboard shortcut to make the panels unhide without mousing to the edge of the screen.  I also don't really want the panel to appear with mouse-over, anywa.

I think it would be cool to have a desktop that people can't figure out how to use, so they can't mess up my stuff while I'm not looking :)  Without a panel or any kind of menu bar, they wouldn't be able to run any apps, or change any settings, etc.

Hi dzv, 
This seemed like a very good idea to me. I have it working on my laptop now. I have put up a [post]("http://reachbeyondgrasp.blogspot.com/2007/04/hide-and-show-panels-with-keyboard.html") detailing how I did this. You can have a look and try it out.

---

### Post by GSF1200S on 2007-04-09
> **raja said:**
> I am not sure I still understand exactly what you want. But if you mean a panel on the desktop where you can put shortcuts for applications, you can try the launcher applet in gdesklets. 


The good thing is that it easy to try out the different desktops. I have tried openbox, fluxbox and xfce. You just have them as separate sessions and remove them if you dont like it. Also worth giving a try is E17 (enlightenment).

Sorry, I wasnt to clear. I have Conky currently on my desktop (right corner under the taskbar). I had to create a script to get it running upon bootup. Everything is cool.. but I have a gripe. When I had Conky write itself to the root desktop, it would black out all my desktop icons. I then in turn had Conky startup in its own window, but completely transparent so it APPEARED as if it were part of the desktop, rather than a window. The only problem is, if I drag a desktop icon over to where Conky is, the icon disappears underneath Conky. The only way I can use the desktop icon again is to launch the system monitor and kill Conky. This isnt a dealbreaker, but it is annoying. As I understand it, Nautilus has this problem when double buffering, which is necessary to avoid Conky blinking. Is there any way for me to resolve all of this, or as this post's title suggests, press a hotkey to have Conky temporarily disappear while I do work beneath it? Hopefully this is more clear.

I agree with you about different GUI's. I actually like the feel of XFCE better than I do GNOME. The bigges problem is, I cant get XFCE up on the internet. I can be connected fine with GNOME, Ctrl Alt Backspace onto XFCE, and bam, im not connected to the internet. It doesnt even show any icons. I would really like to try the 3 you listed, especially Ice and E17, as Ive heard good things, but I should figure out this internet problem with other themes before I venture away from XFCE. Ive posted 3 different threads. One was in Networking and Wireless and 2 were in Absolute Beginner Forum... Ive searched google and the forums and I havent found any solutions.. Any ideas?

---

### Post by dzv on 2007-04-10
> **raja said:**
> Hi dzv, 
This seemed like a very good idea to me. I have it working on my laptop now. I have put up a [post]("http://reachbeyondgrasp.blogspot.com/2007/04/hide-and-show-panels-with-keyboard.html") detailing how I did this. You can have a look and try it out.

Hi Raja,

Thank you very much for your efforts on this!  The script works very well.  I've tweaked it a little, too.  Here's what I've done:

```

#!/bin/bash

#find the current state of the panels
state=`gconftool-2 --get "/apps/panel/toplevels/top_panel_screen0/auto_hide"`

#if autohide on, turn it off (SHOW THE PANELS)
if [ $state = "true" ]; then
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/unhide_delay" --type integer "0"
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/auto_hide" --type bool "false"
gconftool-2 --set "/apps/panel/toplevels/panel_1/unhide_delay" --type integer "0"
gconftool-2 --set "/apps/panel/toplevels/panel_1/auto_hide" --type bool "false"
fi

#if autohide off, turn it on (HIDE THE PANELS)
if [ $state = "false" ]; then
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/unhide_delay" --type integer "100000"
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/auto_hide" --type bool "true"
gconftool-2 --set "/apps/panel/toplevels/panel_1/unhide_delay" --type integer "100000"
gconftool-2 --set "/apps/panel/toplevels/panel_1/auto_hide" --type bool "true"
fi

```

Now, the only minor gripe I have is that even with the panels hidden and size set at 0, I can still activate the menu items with the mouse at the edge of the screen.  And the tooltips also show when the mouse hovers over the menu items, etc.  Any way we could get rid of that?  :)

---

### Post by raja on 2007-04-10
Thanks dzv,
I dont think "unhide delay" is any more valid when you have set "autohide"  disabled. So I am not sure why you have that in the script. Setting the unhide delay to a large number when you have unhide delay is a good idea. I cant see what else you can do to prevent it coming out with mouse over.

---

### Post by dzv on 2007-04-10
The reason I set the unhide_delay back to 0 when I set autohide to off, is because if I leave it at a high number, that's how long it takes for the panel to appear (unhide) when I run the script.  So by changing the unhide_delay to 0 before unhiding the panel, it comes out instantly :)

And as for my minor gripe about the tooltips showing when the mouse it moved to the edge of the screen...  I found out how to disable the tooltips in gconf-editor: /apps/panel/global/tooltips_enabled

Unfortunately, it's still possible to activate an item on the panel with a mouse click, even when the panel is hidden.  But I'm happy with it for now :)

Thanks again Raja!

---

### Post by raja on 2007-04-10
> **dzv said:**
> The reason I set the unhide_delay back to 0 when I set autohide to off, is because if I leave it at a high number, that's how long it takes for the panel to appear (unhide) when I run the script.  So by changing the unhide_delay to 0 before unhiding the panel, it comes out instantly :)


I think that was an excellent modification. I incorporated it into the script. But why are you still activating items with a mouseclick ? Dont you have the size of the hidden panel set to '0' ?

---

### Post by dzv on 2007-04-11
> **raja said:**
> I think that was an excellent modification. I incorporated it into the script. But why are you still activating items with a mouseclick ? Dont you have the size of the hidden panel set to '0' ?

Yes, I do have the auto_hide_size set to 0.  But for some reason, I can still activate the menu items with the mouseclick.  For example, by putting the mouse to the top right corner of my screen...  If I click, I get the "Log off" window, because that's where the "Log off" button is positioned on my top panel (even though I can't see it).  And the panel also unhides itself when I click on a (hidden) panel item.  Does this not also happen for you?  Is it only me? :(

---

### Post by dzv on 2007-04-16
> **raja said:**
> I think that was an excellent modification. I incorporated it into the script. But why are you still activating items with a mouseclick ? Dont you have the size of the hidden panel set to '0' ?

Just thought I'd mention that the problem went away (sort of)...  I did a fresh install of Feisty a couple of days ago (not for this reason), and now it works exactly as I wanted it to.   I can no longer click on any of the buttons on the hidden panel :)

Thanks again, Raja, for your help.  I've now taken the concept much further and created 3 'operating environments' on my laptop:

Regular mode - No panel, just an Avant Window Navigator dock with my most common app launchers, and set to auto-hide.

Admin mode - With panel for access to everything.

Guest mode - Similar to regular mode, but with fewer launchers on the AWN dock, several functions disabled, and pretty much all keyboard shortcuts disabled, so my friends pretty much can't do anything except browse the web :)

I find this easier than setting up different users and having to switch users and worry about files in different user folders, etc.  I can just switch access modes with keyboard shortcuts.

---

### Post by raja on 2007-04-16
> **dzv said:**
> 
I find this easier than setting up different users and having to switch users and worry about files in different user folders, etc.  I can just switch access modes with keyboard shortcuts.

How exactly did you do that? Sounds interesting.

---

### Post by dzv on 2007-04-16
> **raja said:**
> How exactly did you do that? Sounds interesting.

Actually, I'm still in the process of making the scripts.  I've created 3 different script files, and mapped different keys to each one.  A portion of my 'guest mode' script is:

```

#!/bin/bash

gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/unhide_delay" --type integer "100000"
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/auto_hide" --type bool "true"
gconftool-2 --set "/desktop/gnome/lockdown/disable_command_line" --type bool "true"
killall avant-window-navigator
gconftool-2 -s /apps/avant-window-navigator/window_manager/launchers -t list --list-type=string '[~/AWN-Launchers/firefox.desktop,~/AWN-Launchers/gedit.desktop]'
avant-window-navigator

```

I'm basically going through my gconf and looking for as many settings as I can to turn on/off depending on which mode I run in.  The scripts will be quite long by the time I'm done :)

---

### Post by MeanderingCode on 2007-05-11
dvz,

Great thinking!! i'm a very "mode-oriented" user.  I am only recently moving into playing with XFCE on my laptop from my standard of customizing the heck out of Fluxbox (which i enjoy so very much), and i'm exploring XFCE to see if there really is any benefit to be had for me...

At any rate, this thread is a treasure for me and i was just wondering if the past three weeks has brought any progress to your scripts (and any other goodies you feel like sharing!! :)

I'd love to see what you've come up with.

Best Regards,
Sean

---

### Post by chochem on 2008-02-13
I tried this solution but the panel is still peeking 1 px above the bottom of the screen despite autohide size being set to zero?

---

### Post by raequin on 2008-05-08
Man, this is a sweet thread.  Thanks to the user who posted the instructions and the script.

After using gconf-editor the panels totally disappear.

Now, if I could only get some hotkeys for disabling my touchpad; stinkin' touchpad taps.

---

### Post by MeanderingCode on 2008-05-09
> **raequin said:**
> Man, this is a sweet thread.  Thanks to the user who posted the instructions and the script.

After using gconf-editor the panels totally disappear.

Now, if I could only get some hotkeys for disabling my touchpad; stinkin' touchpad taps.

[Here's a lead.]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60#Enable.2FDisable_Touchpad")
[Syndaemon]("http://www.debuntu.org/2006/06/25/70-how-to-disabling-your-touchpad-while-typing") is another lead.
> syndaemon  - a program that monitors keyboard activity and disables the
touchpad when the keyboard is being used.

Also, you can thank people by clicking the small medal icon in the lower right corner of their post while you're logged in.

Good luck!

---

### Post by offbrand on 2008-06-05
What is the chance we can make this make the panels slide right like when you use panel hide buttons.

---

