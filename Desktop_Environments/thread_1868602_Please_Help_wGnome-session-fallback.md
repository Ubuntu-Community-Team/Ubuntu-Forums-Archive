---
title: "Please Help w/Gnome-session-fallback"
date: 2011-10-24
forum: Desktop Environments
---

### Post by crjackson on 2011-10-24
After serious difficulty I managed to install 11.10 on my wife's HP G6 i5 laptop.

She hates Unity and is sticking with Win7 until I can make this install look and work like 10.10. I installed gnome-session-fallback and it's a decent start, but I have one problem that should be minor but isn't to her.

She wants only ONE panel and it has to be on the bottom...

Now, I have reduced her to one panel, and moved it to the bottom, but it leaves the Unity top panel still in place (menu icon, file, edit, places, etc..) on the top. I can't find a way to remove it.

I would love to install 11.10 just to make things simpler for her (read me) but it doesn't support her wireless card, and I can't find the driver, and don't know how to compile one anyway.

11.04 has really poor wireless performance, but the 10.10 wireless support for her card works really well.  So I thought it would probably be easier for me to remove the upper panel that's left over.

Please help me resolve this. We both hate Win7, but she hates Unity more than Win7.

Thanks

---

### Post by Flymo on 2011-10-24
May I suggest trying Lucid Lynx - 10.04 LTS?  The Long Term Support is very stable and (IMO) better for 
day-to-day use than the latest releases.
It has  a standard Gnome 2 installation that just works....  But you would need to move all the bits from the top bar to the bottom bar, then delete the top bar to meet her needs.

Or perhaps adding the XFCE4 metapackage in Synaptic?  
That has worked well for us in Lucid.

In Lucid XFCE4 comes with a single bar, just put it wherever you wish.

Push comes to shove, a reinstall using Xubuntu would get you there.  

But do try just adding XFCE4 first, then do a reboot and you should then get a choice of desktop at the login screen.

---

### Post by crjackson on 2011-10-24
> **Flymo said:**
> May I suggest trying Lucid Lynx - 10.04 LTS?  The Long Term Support is very stable and (IMO) better for 
day-to-day use than the latest releases.
It has  a standard Gnome 2 installation that just works....  But you would need to move all the bits from the top bar to the bottom bar, then delete the top bar to meet her needs.

Or perhaps adding the XFCE4 metapackage in Synaptic?  
That has worked well for us in Lucid.

In Lucid XFCE4 comes with a single bar, just put it wherever you wish.

Push comes to shove, a reinstall using Xubuntu would get you there.  

But do try just adding XFCE4 first, then do a reboot and you should then get a choice of desktop at the login screen.

Thanks Flymo, but Lucid fails to support her wireless, function keys, and touchpad.

11.04 is the 1st version that supports everything and I can configure it easily, but wireless support is very low performance.

11.10 took an arm and leg to get installed because no one in the Forums would help, but I finally got help on a Fedora form.

If I can just remove that top bar (not the regular gnome panel, but the one that pops up in unity with file, edit...) 11.10 is doable.

It's not hard to manipulate the standard panels with the alt+right click, but I can't remove that command bar.

Once the command bar is gone, the interface will be fine.

Thanks again...

---

### Post by ajgreeny on 2011-10-24
Here is the info that may help you, courtesy of **bob-linux-user**, a forum member.  I have used these recommendations on my test installation of 11.10, but changed a few of the theme choices, and it is as near as I can get to the old classic-gnome desktop.
> The Gnome that is available on Ubuntu 11.10 is I find a good alternative to Unity and as far as I can see it looks and feels like classic gnome. The instructions below let you use a panel, get rid of the diabolical overlay scrollbars and put the window controls back at top right.This is what I did:

Install ubuntu 11.10 in normal way
In a terminal type
sudo apt-get install synaptic
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.2-0
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0
sudo apt-get install gnome-session-fallback
sudo apt-get install gconf-editor
sudo apt-get install gnome-tweak-tool
log out and log back in gnome classic
In a terminal type
gksudo gconf-editor
Browse to apps/metacity/general. Double click on button_layout and gconf-editor and set value to
:minimize,maximize,close
Alt right click on panel at top.
-Set orientation to bottom and size to 36
Alt right click on time and move to extreme right
Alt right click on panel and add
-Main Menu
-Window List
Alt right click on "Applications Places" menu and remove
Alt right click on the "speech bubble" at bottom right and remove
Remove the slim top panel by alt right clicking and deleting
Alt right click on panel and add
-Show desktop icon
On a general area of desktop right click and change the background to what you want ( I chose Jardin Polar)
in a terminal type
sudo apt-get install ubuntustudio-theme
sudo apt-get install ubuntustudio-icon-theme
sudo apt-get install human-theme
sudo gnome-tweak-tool
Set Theme:Icon theme to Ubuntu Studio
Set GTK+ theme to Raleigh
Set window theme to human
I hope it helps, and thanks again to bob-linux-user.

---

### Post by crjackson on 2011-10-24
Actually, I did use most of his tweaks, but right now, I just want to get rid of that top command bar that resides on an empty desktop.

---

### Post by crdlb on 2011-10-24
> **crjackson said:**
> Actually, I did use most of his tweaks, but right now, I just want to get rid of that top command bar that resides on an empty desktop.

Do you mean the top gnome panel? Does Alt + right click not work?

Or do you mean the nautilus menubar? If so, that's a bug in Ubuntu's global menu stuff. You can work around it by removing the appmenu-gtk3 package and restarting nautilus.

---

### Post by crjackson on 2011-10-24
Actually I think it was a nautilus menu bar, but I figured it out. gnome-tewak-tool has a setting that let me turn it off.

It's good for now. If I could just figure out how to move the close, mix, max, window buttons back to the right side that would be great. gconf-editor and gnome-tweek-tool has a setting for this but it's having no effect. I'm close to being able to make this thread solved.

---

### Post by ajgreeny on 2011-10-24
> **crjackson said:**
> Actually I think it was a nautilus menu bar, but I figured it out. gnome-tewak-tool has a setting that let me turn it off.

It's good for now. If I could just figure out how to move the close, mix, max, window buttons back to the right side that would be great. gconf-editor and gnome-tweek-tool has a setting for this but it's having no effect. I'm close to being able to make this thread solved.
I used gconf-editor to do the window management button move in my 11.10 without a problem, so I do not know why it is not working in yours.

I presume you have not missed out the colon that comes at the front of the button list entry, ie  **:minimize,maximize,close** or  **:minimize,maximize,spacer,close** for an even better look.

---

### Post by crjackson on 2011-10-24
Maybe I need to reboot or something...  I'll try that. It is set the way you listed already.

EDIT: Rebooting the system fixed the buttons.

---

### Post by crjackson on 2011-10-24
I know I marked this thread as solved, but I have 3 more things I need help with.

1 - I want to show mounted volumes on desktop - setting for that in tweak tool but it's not working when changed

2 - I want to create folders or place folders on desktop. No matter what I do it wont let me.

3 - LightDM when to an all black background (don't know why). I want the standard purple one back.

Thanks for you help

---

### Post by merlinus on 2011-10-24
Set file manager to manage the desktop in the gnome tweak tool.

---

### Post by crjackson on 2011-10-24
That worked but brings back the nautilus menu bar on the desktop. Is there no way to do this without having the menu bar on the desktop?

---

### Post by merlinus on 2011-10-24
I do not have a nautilus menubar on the desktop with this setting.  Can you post a screenshot?

---

### Post by crjackson on 2011-10-24
I hate the menu bar being there...

---

### Post by crdlb on 2011-10-24
> **crjackson said:**
> That worked but brings back the nautilus menu bar on the desktop. Is there no way to do this without having the menu bar on the desktop?

Did you remove appmenu-gtk3 and restart nautilus?

---

### Post by merlinus on 2011-10-24
Yeah, I see what you mean.  I run a panel at the top of the screen, so maybe that is why it does not appear on my desktop.

---

### Post by crjackson on 2011-10-24
> **crdlb said:**
> Did you remove appmenu-gtk3 and restart nautilus?

No I didn't, are you saying I should try that?

---

### Post by crjackson on 2011-10-24
> **merlinus said:**
> Yeah, I see what you mean.  I run a panel at the top of the screen, so maybe that is why it does not appear on my desktop.

Move the top panel to the bottom and see if you have the same issue if you don't mind...

---

### Post by merlinus on 2011-10-24
Yes, when I move my top panel to the bottom, that *&^%(! menubar appears.  Yucko!!  

I went through the settings in both g-conf and d-conf, and did not find anything related to that bar.

---

### Post by crjackson on 2011-10-24
> **crdlb said:**
> Did you remove appmenu-gtk3 and restart nautilus?

Okay, I tried that and restarted.  It didn't help.

---

### Post by crjackson on 2011-10-24
> **merlinus said:**
> Yes, when I move my top panel to the bottom, that *&^%(! menubar appears.  Yucko!!  

I went through the settings in both g-conf and d-conf, and did not find anything related to that bar.

If I had full hardware support on 10.10 with this laptop, I'd do it quick, fast, and in a hurry. That's what the wife wants, but 10.10 doesn't give the hardware support 11.10 does.

---

### Post by crjackson on 2011-10-24
LightGDM also now has a black background screen, does anyone know how to get that back to the defaults.

---

### Post by Brandel Valico on 2011-10-24
Not at my laptop right now but when I get home later tonight. I should be able to help you with that bar. I had the same issue when I switched to Xfce with unity installed. Of that bar showing up. The command I used to get rid of it. Should be in my terminal log still and should work on straight unity also with the tweaks mentioned here. Will be around 10 hours. To give me time to test it when I get home in 9 hours. Will let you know.

---

### Post by robert shearer on 2011-10-24
If you haven't found the fix for media mounts showing on the desktop it is here...
[http://ubuntuforums.org/showthread.php?t=1859386](http://ubuntuforums.org/showthread.php?t=1859386)

---

### Post by Brandel Valico on 2011-10-24
Not postive until I get home to confirm but I belive this was the command. 

>  sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt 

---

### Post by crjackson on 2011-10-24
> **robert shearer said:**
> If you haven't found the fix for media mounts showing on the desktop it is here...
[http://ubuntuforums.org/showthread.php?t=1859386](http://ubuntuforums.org/showthread.php?t=1859386)

Okay, thanks. Great information. Before all this information was provided, I also discovered that using a root nautilus the missing items were present in the root desktop folder, but not the user's desktop.

Some serious bugs I think...

---

### Post by crjackson on 2011-10-24
> **Brandel Valico said:**
> Not postive until I get home to confirm but I belive this was the command.

I'll wait until you get home and post exactly what you have. I don't want to jack anything up...

Anyone know about the LightDM color issue?

---

### Post by merlinus on 2011-10-24
If file manager is set to manage the desktop in the gnome tweak tool, then the mounts appear on my desktop.

Despite running all of the workarounds, the mounts still do not show up unless the above is activated.

And if that is so, then compiz is not managing my windows, etc.

---

### Post by Brandel Valico on 2011-10-25
On standard Unity now and the above command did get rid of the menu. Mind you I have also removed the unity launcher. I'm running a Cairo dock at the bottom and top of the screen normally they are set to auto-hide. I set them to be visible here to show them to you and to show that damn bar at the top isn't there.

Remember also you can always simply re-install them by typing the same command with install instead of remove.

Still here is my current desktop 

[http://home.comcast.net/~BrandelValico/Images/Screenshot.png]("http://home.comcast.net/~BrandelValico/Images/Screenshot.png")

The moon and system bar on the right are just screenlets.

---

### Post by crjackson on 2011-10-25
> **Brandel Valico said:**
> On standard Unity now and the above command did get rid of the menu. Mind you I have also removed the unity launcher. I'm running a Cairo dock at the bottom and top of the screen normally they are set to auto-hide. I set them to be visible here to show them to you and to show that damn bar at the top isn't there.

Remember also you can always simply re-install them by typing the same command with install instead of remove.

Still here is my current desktop 

[http://home.comcast.net/~BrandelValico/Images/Screenshot.png]("http://home.comcast.net/~BrandelValico/Images/Screenshot.png")

The moon and system bar on the right are just screenlets.

Thanks Brandel, that seems to have cleared up my issues. I can also log into a regular Unity session and it seems to be working fine. It did throw a systry error when loading but everything seemed to work fine (including the menu panel at the top).

Finally, back to where it should be... Thanks everyone...

---

### Post by Brandel Valico on 2011-10-25
Great now we just need someone to help with the Lightdm color issue.

I have no clue on that.

---

### Post by crjackson on 2011-10-25
Would you suggest a new thread for that issue?

---

### Post by Brandel Valico on 2011-10-25
Generally speaking your better off with a thread for each unique issue.

---

### Post by crjackson on 2011-10-28
> **Brandel Valico said:**
> Great now we just need someone to help with the Lightdm color issue.

I have no clue on that.

I finally figured it out. On a clean install the /user/share/backgrounds directory contained a warty-final.png 

I don't know how it happened but that background got deleted in all my tinkerings...  I installed simple-lightdm-manager (great little tool) and after copying the file from another of my machines, I used the tool to reassign the image as the background.

It works great. I guess I'm done with it but I fear I've lost my wife to the dark side. She's been using Win7 for her needs and now she won't even boot back into ubuntu. Thanks a lot Unity...

---

