---
title: "Beryl sort of works, but my window borders are missing.  Can't drag/minimize/close"
date: 2007-03-19
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2007-03-19
I followed the stickied tutorial in this forum and managed to get beryl installed and working partialy.

The problem is that, my windows borders are missing.  I can't drag, resize, minimize, maximize or close without using the few keyboard shortcuts I know, the only one being Alt-F4 to close a window.  And to get the borders back, I have to close the session and log back in.

I am, however, able to get the 3D cube thing spining using the mouse, but that's the only thing that works:  the cube.

I tried messing with the Emerald theme manager, to see if I could pick a theme that would replace my missing borders and title bars, but it didn't work.

I am running Ubuntu Ultimate 1.3, which came with the Beryl repositories already installed, but I re-installed them again when I did the tutorial.  I also used Envy to install my video drivers.

Edit:  More info about the computer:

It's a HP ZD7000 laptop (I think, just bought the thing).
2.8 gig Pentium 4
Geforce 5600 Go 128mb vram
512 mb ram
60gig hd

---

### Post by simonn on 2007-03-19
There is a setting in beryl manager which allows you to turn off windows decorations etc. Can't remember where it is or what it is called exactly (away from my linux box at the mo).

---

### Post by snoozzzer on 2007-03-19
In the beryl settings manager, there's an option for window manager? (I'm not exactly sure as my system is broken and I haven't gotten around to fixing it) It may be for window manager or decorations, but there's an option for that, just type in "emerald" w/o the quotation marks and it should work

---

### Post by old_geekster on 2007-03-20
I suggest that you install "Automatix Bleeder".  It doesn't have many programs to install, but one of them is Beryl 0.2.0.  This is the first stable version of Beryl since 0.1.0.

Add this repos to your /etc/apt/sources.list:

#AUTOMATIX BLEEDER REPOS START
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
#AUTOMATIX BLEEDER REPOS END

I tried installing Beryl several times with apt-get and Synaptic, with no success.  I used "AB" and it worked perfectly the first time..

---

### Post by konungursvia on 2007-03-20
Also, if your session saves beryl-manager, and you restart, and start beryl-manager again, I fnd its sometimes running twice at the same time, and that right-clicking the ruby, and closing it, restores it to working well.

---

### Post by diablo75 on 2007-03-20
No luck so far.  Here's what I've tried:

I used Automatix Bleeder to attempt to install, then uninstall, and then re-install beryl.  And there's no difference between the two installs.  Same problem of the window borders not being there.

I then opened up the Beryl manager.

When people say in here, "Beryl settings manager", I can't tell if they're talking about the drop down menu, or the actual settings manager frontend gui.  But I can't find a place where I can type in "emerald"... I can force it to restart the window decorator (which doesn't solve the problem) and also the Window Manager.  Resetting both doesn't solve the problem, and it appears that "emerald" is already the selected window decerator, and beryl is the window manager.  But there's no place for me to go in and manually add a line.

Perhaps there's a command line that would allow me to do this.  But I'm still new to linux, so don't know what to do next...

Keep the help commin' guys.  I really want to get this working right so I can show it to people and go, "THIS is linux.  You should try it!"

---

### Post by Joco_Ultimate on 2007-03-20
I have the same problem and I can't find a solution either. Help would be great!

---

### Post by TimJBart on 2007-03-20
> **hustle7 said:**
> I'm having problems with my emerald theme manager in beryl. I try to select a theme but no changes would occur. My windows have no un-minimize, minimize, and close buttons when using beryl. Would you please be so kind to help me solve this dilemma? Thank You!


I had the exact same problems.

a) There were no maximize and minimize buttons/titlebars.
b) Clicking on a new theme in Emerald Manager did nothing.

I asked on the forums and someone posted this response and it WORKED!!!


> 
If you have a nvidia card and if you are using the non-opensource drivers, run this command.
Code:

```
sudo nvidia-xconfig --add-argb-glx-visuals
```

Then hit <CTRL><ALT><Backspace> and log back in again. That should fix your problem.

Hope this fixes your problem.  If not, there are some other suggestions in the thread: [http://ubuntuforums.org/showthread.php?t=367850](http://ubuntuforums.org/showthread.php?t=367850)

---

### Post by Joco_Ultimate on 2007-03-20
It wooorks!!!! Thank you! One problem lesser!

---

### Post by diablo75 on 2007-03-20
I tried the sudo nvidia-xconfig --add-argb-glx-visuals command in terminal, and restarted, but the same problem still exists.

I'll take a look at the other thread you linked to, but if anybody has any other ideas, let me know please.

Thanks again!

---

### Post by zanyspydude on 2007-03-20
this is the same as that i'm sure, but it worked for me

i added 
```
Option "AddARGBGLXVisuals" "True"
```.

to my xorg.conf file in the Section "Device" area

---

### Post by old_geekster on 2007-03-20
> **diablo75 said:**
> I tried the sudo nvidia-xconfig --add-argb-glx-visuals command in terminal, and restarted, but the same problem still exists.

I'll take a look at the other thread you linked to, but if anybody has any other ideas, let me know please.

Thanks again!
Do you have the "Red Emerald" (I thought emeralds are green) in the Panel?  If so, this is Beryl Manager.  Right click on it.  

You should see several options.  Click on "Emerald Theme Manager".  Choose "Slatehorn_Red".  This is one of Beryl's official themes.  This theme actually has four buttons in the top left-hand corner.  The one on the far left is for creating a window shade effect.  It rolls the window up to the top of the screen.

If you don't get the buttons with this theme, try "Ctrl / Alt Return (Enter).  This enables/disables full screen.  In full screen you don't have the buttons.

Good luck!

---

### Post by michael95060 on 2007-03-20
open the Beryl Settings Manager, go to General Options, select Shortcuts and you will find the keyboard/mouse combos that do the movement stuff you might be looking for.  Also right clicking the  window indicator on the lower panel will display some other grow and move options.  Even without window borders these are all working for me....hope you have the same luck.
cheers.

---

### Post by diablo75 on 2007-03-21
I added the Option "AddARGBGLXVisuals" "True" to my xorg.conf file, but it didn't do anything.

I also attempted to select the theme from the theme manager mentioned above, and that didn't work.  None of those themes have ever worked....

---

### Post by elizleisndahizle on 2007-03-21
I am having the same exact problem on an HP DV9000z laptop with a Geforce 7600 in it.  I tried those things and it didn't help.  It is running fine on my desktop and I set it up the same way.

---

### Post by elizleisndahizle on 2007-03-21
Another thing, I am running 64 bit ubuntu could that be a problem?

---

### Post by diablo75 on 2007-03-21
I noticed my update manager had an update for Automatix today.  I think their server was a bit overwhelmed, because I couldn't download it last night, and today it went slow, but it went through none the less.  I haven't had a chance to check it out, but maybe there's something wrong with the way automatix is installing either the nvidia drivers, or beryl?

In the mean time, other than the suggestions that I've gotten in here, I've tried to uninstall and reinstall the nvidia drivers as well as beryl to see if it would change anything.  After doing this last night, Beryl settings manager will loads, but the cube thing didn't work anymore...didn't seem like Beryl was actually running at all.

Also, on the side, Google Earth won't work.  It did at one time, but now says it can't recognize my video card.  The OS does (you can see it working on screensavers that need Open GL running to look good, and they still work).

Anyway, I'm going to try to uninstall and reinstall beryl and nvidia again tonight and see what happens.

---

### Post by zixxer on 2007-03-22
im having this same problem if i install beryl via the method on beryl-project.org. upon activating beryl the themes do not work at all and the default theme (maybe) makes all the buttons dissapear from the windows...and if you open up gnome-term it is blank white and doesnt work, but xterm works fine but still no buttons. this is with the latest nvidia drivers and a 7600gt. my rez is 1680x1050 on 6.10. any ideas as why this happens? could it be the nvidia drivers, as they recently released new ones?
ill work more on this when i get to my box at home, but its a slightly big bump in the road.

p.s. ive had this working on the same box with the last Nvdia driver, and the previous beryl version....worked as it should. this software setup does not.:confused:

---

### Post by WiFi Ed on 2007-03-22
I don't know if this has been posted, but I had the same symptoms until last night. I followed the "Prerequisites" section of this guide:

[http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html]("http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html")

and my title bars and window borders became visible and windows could be manipulated normally. Emerald still takes a long time to load, and I did manage to lock up the pc while fiddling with some of the themes in Emerald after following this guide, but it did make everything show up.

I'm using Ubuntu 6.10 on a Dell E520 with an NVIDIA 7600GS 256 mb pci-e video card. I'm sorry, I don't know which nvidia drivers are installed or other critical information...

---

### Post by diablo75 on 2007-03-22
I'll take a look at that link sometime tomorrow.  Today is my last day at work, and I broke up with my girlfriend...so I plan on getting pretty wasted tonight, heh heh.

At least I'm not the only one having this problem with beryl.

A little update, though:

I got Google earth to work just fine after uninstalling nvidia and google earth, and then reinstalling them again, all via Automatix and Automatix Bleeder.  I've noticed that the Automatix web server has been shot to hell by so many people downloading their updates.

Beryl, on the other hand, doesn't work at all, now.  No 3d effects, not even menus fading in and out.  The red diamond/jewel thing appears in the upper right hand corner, but it has some other windows manager other than beryl selected.  When I try to select it, it doesn't work; just reverts back to the same manager that was already selected.

Oh well... I'm hangin' in there.:guitar:

---

### Post by zixxer on 2007-03-23
> **WiFi Ed said:**
> I don't know if this has been posted, but I had the same symptoms until last night. I followed the "Prerequisites" section of this guide:

[http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html]("http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html")

and my title bars and window borders became visible and windows could be manipulated normally. Emerald still takes a long time to load, and I did manage to lock up the pc while fiddling with some of the themes in Emerald after following this guide, but it did make everything show up.

I'm using Ubuntu 6.10 on a Dell E520 with an NVIDIA 7600GS 256 mb pci-e video card. I'm sorry, I don't know which nvidia drivers are installed or other critical information...

that guide worked perfectly for me on feisty! and i know its something in there because with the  latest nvidia drivers and latest beryl, it still did the no buttons thing until i did what was in the guide, now it works great!

---

### Post by julie_lebou on 2007-03-23
Go there! Fixed the problem after trying everything in this forum

[http://nlindblad.org/2007/01/28/no-w...-nvidia-aiglx/](http://nlindblad.org/2007/01/28/no-w...-nvidia-aiglx/)

---

### Post by elizleisndahizle on 2007-03-23
It didn't fix my problem.  I noticed zixxer is also running a 7600 and at 1680x1050.  Maybe part of the problem is related to that.

---

### Post by diablo75 on 2007-03-24
This link solved my problem:

[http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html](http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html)

Thanks!

I noticed one of the lines it asks you to add had something to do with tripple buffering.  Is this line required, and if I went into my xorg.conf file and removed it, would I see an improvement in performance?

Edit:  Fixed link above

---

### Post by mthaddon on 2007-03-25
Link got truncated. That's [http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html](http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html)

---

### Post by elizleisndahizle on 2007-03-25
That still didn't fix it...
It makes me mad because it works just fine on my desktop, except for the fact that this has a better video card.  This should run circles around my desktop but for some reason beryl won't work right.  I know it works because it started without a problem in Sabayon linux.  I guess I need to just either redownload that or find my old disk and just compare my xorg.conf files.  I will try that and see if it work... eventually.

---

### Post by elizleisndahizle on 2007-03-25
OK, so I uninstalled and reinstalled it.  Still I have the same problem.  But I ran it in a terminal instead of with alt+F2 and it repeats Framebuffer attach failed.  What could be causing that?

---

### Post by elizleisndahizle on 2007-03-25
I figured it out!!! Make sure your default color depth is 24 bit.  That fixed it for me.

---

### Post by evil bender on 2007-05-03
> **TimJBart said:**
> I had the exact same problems.

a) There were no maximize and minimize buttons/titlebars.
b) Clicking on a new theme in Emerald Manager did nothing.

I asked on the forums and someone posted this response and it WORKED!!!

Hope this fixes your problem.  If not, there are some other suggestions in the thread: [http://ubuntuforums.org/showthread.php?t=367850](http://ubuntuforums.org/showthread.php?t=367850)


i had the same problem - couldn't move the window, etc..

that fixed it. thanks!

---

