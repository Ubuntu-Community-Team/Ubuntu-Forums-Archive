---
title: "Cinnamon Problems"
date: 2012-06-12
forum: Desktop Environments
---

### Post by Shadius on 2012-06-12
Hey everybody! :)

I've just installed the Cinnamon Desktop Environment using this guide: [Cinnamon]("http://www.linuxbsdos.com/2012/04/26/install-the-latest-and-greatest-cinnamon-desktop-on-ubuntu-12-04/"). However, after logging into the Cinnamon session, it looks nothing like how it's supposed to look by default. I cannot see anything within the windows, the background is blue, and when I hover over things such as the "Menu" it seems like the graphic is scrambling. 

To clarify on some things:

Here's what I mean when I say I cannot see anything within the windows. I right click on an empty space on the desktop and just get an outline of the right-click context menu. I can click on "Menu" from the panel, but if I select something like "Appearances" the window outline will come up with nothing visible within the window. I had to guess where the "Log Out" button was in the dialog box after selecting "Log Out" from the "Menu". 

So what is the problem here and how do I fix it?

---

### Post by wilee-nilee on 2012-06-12
Have you run a update and upgrade in the terminal and then rebooted to the cinnamon desktop.

```
sudo apt-get update && sudo apt-get upgrade
```I have never installed cinamon, but I wonder if there are packages that may need updating.

---

### Post by Shadius on 2012-06-12
> **wilee-nilee said:**
> Have you run a update and upgrade in the terminal and then rebooted to the cinnamon desktop.

```
sudo apt-get update && sudo apt-get upgrade
```

I have never installed cinamon, bu I wonder if there are packages that may need updating.

Hello again wilee-nilee! 

I've run
```
sudo apt-get update
```
after I added the PPA, but haven't ran 
```
sudo apt-get upgrade
```

I will try it now. Wait, from which environment am I supposed to run it from since I can't see any window contents from Cinnamon? I'm currently on GNOME Classic (No effects). Can I run it from this session?

---

### Post by wilee-nilee on 2012-06-12
> **Shadius said:**
> Hello again wilee-nilee! 

I've run
```
sudo apt-get update
```after I added the PPA, but haven't ran 
```
sudo apt-get upgrade
```I will try it now. Wait, from which environment am I supposed to run it from since I can't see any window contents from Cinnamon? I'm currently on GNOME Classic (No effects). Can I run it from this session?

I would run the command as I posted it just to be sure, or at least a update and upgrade.

I always run them in conjunction I'm lazy. :)

---

### Post by Shadius on 2012-06-12
Okay, I ran the code both separately and in conjunction. Nothing needed to be upgraded. :(

---

### Post by wilee-nilee on 2012-06-12
> **Shadius said:**
> Okay, I ran the code both separately and in conjunction. Nothing needed to be upgraded. :(

Have you done a reboot, that is all I can really think of not having used cinnamon.

I would install it if I had a complete package list to wipe it with, to test it.

---

### Post by Shadius on 2012-06-12
> **wilee-nilee said:**
> Have you done a reboot, that is all I can really think of not having used cinnamon.

Yupp, tried that too. Could it have to do anything with my customizations in my GNOME Classic (No effects) session? I did install a theme and I'm using conky. Could that have anything to do with it?

---

### Post by wilee-nilee on 2012-06-12
> **Shadius said:**
> Yupp, tried that too. Could it have to do anything with my customizations in my GNOME Classic (No effects) session? I did install a theme and I'm using conky. Could that have anything to do with it?

Conky shouldn't have any effect and I would think the classic would not either as cinnamon is its own desktop.

One never knows though as desktops will use other desktops apps, and stuff.

You might try the freenode ##linuxmint channel on the IRC as well, only 26 users right now but you never know.

Others on this forum use cinnamon so maybe some one post and enlighten all of us, lol.

---

### Post by Shadius on 2012-06-12
> **wilee-nilee said:**
> Conky shouldn't have any effect and I would think the classic would not either as cinnamon is its own desktop.

One never knows though as desktops will use other desktops apps, and stuff.

You might try the freenode ##linuxmint channel on the IRC as well, only 26 users right now but you never know.

Others on this forum use cinnamon so maybe some one post and enlighten all of us, lol.

The reason I asked if that would affect my Cinnamon environment is because when I logged into the Cinnamon environment, I saw that the icon theme (ACYL) that I'm using in GNOME Classic (No effects) is being used by Cinnamon also and I haven't done anything to customize Cinnamon. I see the icons in the panel for Firefox, a folder icon (which I'm guessing is Home) and another icon. These three icons are themed with the ACYL icon theme and are not the default environment's icons. Hope I was clear there, I can get a bit confusing at times. :) I will try the IRC!

---

### Post by wilee-nilee on 2012-06-12
I did discover that the manager of cinnamon is muffin, a fork of mutter which is the gnome 3 manager.

Gnome 3 has a nice restart option, I can't find one for cinnamon though or a command to make sure muffin is running, I suspect that the problem is in the manager, a theory only though.

The gnome 3 restart is alt-f2 then the letter r as a general reference.

If you run it I doubt it will fix it but bring up gnome 3 or who knows what. 

Just thought it worth mentioning as a refrence to look for a restart for cinnamon or the window manager muffin info.

---

### Post by wilee-nilee on 2012-06-12
> **Shadius said:**
> The reason I asked if that would affect my Cinnamon environment is because when I logged into the Cinnamon environment, I saw that the icon theme (ACYL) that I'm using in GNOME Classic (No effects) is being used by Cinnamon also and I haven't done anything to customize Cinnamon. I see the icons in the panel for Firefox, a folder icon (which I'm guessing is Home) and another icon. These three icons are themed with the ACYL icon theme and are not the default environment's icons. Hope I was clear there, I can get a bit confusing at times. :) I will try the IRC!

I think you're on the right track here the cross use of apps and set ups can get real interesting, especially when you use a customized set up. ;)

If it were me I would try setting the classic stock, and all other desktops that way as well, as far as extra tweaks.

---

### Post by Shadius on 2012-06-12
> **wilee-nilee said:**
> I did discover that the manager of cinnamon is muffin, a fork of mutter which is the gnome 3 manager.

Gnome 3 has a nice restart option, I can't find one for cinnamon though or a command to make sure muffin is running, I suspect that the problem is in the manager, a theory only though.

The gnome 3 restart is alt-f2 then the letter r as a general reference.

If you run it I doubt it will fix it but bring up gnome 3 or who knows what. 

Just thought it worth mentioning as a refrence to look for a restart for cinnamon or the window manager muffin info.

I wouldn't even know if I'm running that command because even if I press **ALT**+**F2** **r**, I wouldn't see what I'm typing because all that comes up is an outline of the window with the background color, blue. I cannot see any contents of the windows that I can open. The only thing I can see are the options available to me from the "Menu", but clicking on them just brings up a blank outline of a window.

---

### Post by Shadius on 2012-06-12
I even tried the keyboard shortcut for Terminal (**Ctrl+Alt+T**) and that just brought up a blank outline of a window also. It's just a box. :lolflag: I really don't understand what's going on here.

---

### Post by wilee-nilee on 2012-06-12
So out of curiosity I used that PPA and installed cinnamon, its the rage you know, lol.

What I noticed in my precise set up with the gnome-shell already installed only these packages were installed to have it run as advertised.

caribou cinnamon gir1.2-muffin-3.0 libmuffin0 muffin-common

The muffin parts here are the window manager I would think make sure you have these installed.

So it looks like it is quite attached to packages already installed to run.

I suspect the customization of the classic is where the problem lies. There was a cinnamon restart button in the bottom panel as well I was not able to figure out the actual command but I did not try that hard.

The no effects and the icon theme (ACYL) set up may be the keys here.

Personally I would not run 3rd party stuff outside of a PPA at worse, but that is just me.

---

### Post by Shadius on 2012-06-12
> **wilee-nilee said:**
> So out of curiosity I used that PPA and installed cinnamon, its the rage you know, lol.

What I noticed in my precise set up with the gnome-shell already installed only these packages were installed to have it run as advertised.

caribou cinnamon gir1.2-muffin-3.0 libmuffin0 muffin-common

The muffin parts here are the window manager I would think make sure you have these installed.

So it looks like it is quite attached to packages already installed to run.

I suspect the customization of the classic is where the problem lies. There was a cinnamon restart button in the bottom panel as well I was not able to figure out the actual command but I did not try that hard.

The no effects and the icon theme (ACYL) set up may be the keys here.

Personally I would not run 3rd party stuff outside of a PPA at worse, but that is just me.

Okay, I checked in Synaptic Package Manager to make sure I have those packages installed as well and I do. Since we both suspect it might have to do with the customization in my GNOME Classic (No effects) environment being used by Cinnamon (somehow), I'll try returning GNOME Classic (No effects) to its default settings. I don't know how to do this though. I used GNOME Tweak Tool to apply the themes, icons etc. How do I revert back to its defaults?

---

### Post by wilee-nilee on 2012-06-12
> **Shadius said:**
> Okay, I checked in Synaptic Package Manager to make sure I have those packages installed as well and I do. Since we both suspect it might have to do with the customization in my GNOME Classic (No effects) environment being used by Cinnamon (somehow), I'll try returning GNOME Classic (No effects) to its default settings. I don't know how to do this though. I used GNOME Tweak Tool to apply the themes, icons etc. How do I revert back to its defaults?

To be honest not sure on the no effect settings, I have not used the classic it may become more apparent though if you think it was done in the gnome tweak tool. I wonder if in the first option desktop-have file manager handle the desktop may be the key I have mine on.

It seems possibly attached to the  icon theme (ACYL) install maybe since you describe that as apparent in cinnamon, just a hypothesis though. If you could disable that or choose the stock settings that may be the key as well, really just guessing here as well, if this or any of what I suspect is correct.

Here is a screen shot of my theme setup in the tool, not really sure as well if this tool all in all has much effect in the classic. I say this as unity which is a plugin in compiz which is all on top of gnome 3 is not incontrol of gnome 3 which uses mutter, so if the classic is a mutter window manager then the gnome tweak may have control.
[ATTACH]219590[/ATTACH]

---

### Post by Shadius on 2012-06-12
Going on thinking that my customizations in my GNOME Classic (No effects) is causing Cinnamon to not work properly, and going on thinking that if I were to revert to the default GNOME Classic (No effects), Cinnamon would work properly. However, not really knowing what the default settings of GNOME Classic (No effects) were and there's no option like "Revert to Default" in GNOME Tweak Tool to go back to the GNOME Classic (No effects) default settings, I decided to try using my brother's user account since his desktop environments all have their default settings. So I logged into Cinnamon from his user account and it's the same thing again. I've taken a picture of it with my cell phone so you can see. 

In the screenshot, I was able to select "Log Out" from "Menu" in the panel, and that is how the window shows up. You can see now that I had to guess where the "Log Out" button was within the "Log Out" dialog box. Hope that makes things clearer.

---

### Post by pete04 on 2012-06-12
Hi shadius,

I too have gnome shell and cinnamon installed, and I've found that then settings for both -- cinnamon settings and gnome tweak tool  (advanced settings) don't really overlap. Theme settings and other things in one don't have any effect on others. Gnome shell and unity both seem to have more in common with settings, etc. 

You might try uninstalling cinnamon and try again. Or maybe try dumping gnome shell to see if it's removal fixes cinnamon. That might be a little desperate, but might work.

Other thing that comes to mind is that you can launch the cinnamon settings application from gnome shell or unity and you mightnbe able to jigger something to work. You might, for example, try turning the cinnamon effects off.

Finally, I'm really liking cinnamon, but I've found it to be a bit buggy with a few lockbox when moving menu or panel items around. I tried mint 13 on a laptop that ran precise perfectly ( gnome shell included) and mint was locking up a bunch. I suspect cinnamon. 

I'll be eager to hear if you find a solution.

---

### Post by Shadius on 2012-06-12
> **pete04 said:**
> Hi shadius,

I too have gnome shell and cinnamon installed, and I've found that then settings for both -- cinnamon settings and gnome tweak tool  (advanced settings) don't really overlap. Theme settings and other things in one don't have any effect on others. Gnome shell and unity both seem to have more in common with settings, etc. 

You might try uninstalling cinnamon and try again. Or maybe try dumping gnome shell to see if it's removal fixes cinnamon. That might be a little desperate, but might work.

Other thing that comes to mind is that you can launch the cinnamon settings application from gnome shell or unity and you mightnbe able to jigger something to work. You might, for example, try turning the cinnamon effects off.

Finally, I'm really liking cinnamon, but I've found it to be a bit buggy with a few lockbox when moving menu or panel items around. I tried mint 13 on a laptop that ran precise perfectly ( gnome shell included) and mint was locking up a bunch. I suspect cinnamon. 

I'll be eager to hear if you find a solution.

Hey pete04,

Thank you for your suggestions. I was wondering if desktop environments could interfere with other desktop environments. It didn't make sense to me as to why or how that would happen. Just to be clear, because I do tend to get confused being new to Ubuntu Linux and all, to know if GNOME Shell is installed on my Ubuntu I would see the "GNOME" option from the login screen, correct? I don't use GNOME Shell or Unity since I've switched to GNOME Classic (No effects). I will try your suggestion of turning off Cinnamon effects from my GNOME Classic (No effects) environment. Also, the regular GNOME Classic works fine. Off I go with your suggestions. Thank you all for your suggestions! Hope I find a solution! Wish me luck!

---

### Post by Shadius on 2012-06-13
Here's something peculiar. While using **Cinnamon Settings** from my GNOME Classic (No effects) environment, I went into the **Themes** selection, and out of curiosity went into the **Other settings** tab and noticed that it basically had my GNOME Classic (No effects) settings in the **Cinnamon Settings**. Is this how it's supposed to be or does this signify that some settings from GNOME Classic (No effects) got mixed up into Cinnamon? I've attached screenshots.

Look at the icons in the panel. One shows the ACYL icon theme and the other the "default" theme. Whatever setting I change in Cinnamon Settings is changing in my current GNOME Classic (No effects) environment. Is this right or is something mixed up?

---

### Post by pete04 on 2012-06-13
The icon themes are universal in my experience. But other things are not.  Changing icons will influence your run of DEs. I'm curious about your gnome fallback session... I thought that was part of the GNOME shell package. It was for me. My fresh 12.04 install had only unity and unity 2D. I wonder if that GNOME fallback mode relieson some packages that clash with cinnamon... You should be running on a gnome 3.4  base.I'm not sure what the conflict would be, but it's gotta be something.

---

### Post by Shadius on 2012-06-13
> **pete04 said:**
> The icon themes are universal in my experience. But other things are not.  Changing icons will influence your run of DEs. I'm curious about your gnome fallback session... I thought that was part of the GNOME shell package. It was for me. My fresh 12.04 install had only unity and unity 2D. I wonder if that GNOME fallback mode relieson some packages that clash with cinnamon... You should be running on a gnome 3.4  base.I'm not sure what the conflict would be, but it's gotta be something.

I think you're right about the GNOME Shell package. When I wanted to get GNOME Classic, I followed a guide that said to install GNOME Tweak Tool and then I was presented with the options of GNOME, GNOME Classic and GNOME Classic (No effects) from the login screen to choose from. I upgraded from 11.10 (Oneiric Ocelot) to 12.04 (Precise Pangolin) and I recall just having Unity and Unity 2D. 

```
shadius@shadius-5410US:~$ gnome-shell --version
GNOME Shell 3.4.1
shadius@shadius-5410US:~$ 
```

You are right about running on a GNOME 3.4 base.

---

### Post by Shadius on 2012-06-13
> **pete04 said:**
> The icon themes are universal in my experience. But other things are not.  Changing icons will influence your run of DEs. 

I'm guessing you mean the icon themes are universal in being that they can work with any desktop environment? 

The thing that puzzles me is that the Cinnamon Settings did not have the default settings under the **Other settings** tab. Instead, it had my themes and icons that I was using in my GNOME Classic (No effects) environment. I thought that Cinnamon would have it's own default settings. It seems like it's pulling my customized settings from my GNOME Classic (No effects) environment. Furthermore, if I change a setting in Cinnamon Settings, it changes in my GNOME Classic (No effects). I don't understand that. How is Cinnamon Settings able to change something like my icon theme in my GNOME Classic (No effects) environment? Shouldn't Cinnamon Settings only pertain to Cinnamon and not any other desktop environment, in my case, GNOME Classic (No effects)?

---

### Post by pete04 on 2012-06-13
OK... 
First: you do have the gnome shell package installed. That's what is presenting you with those choices of gnome, classic, etc. Gnome is the gnome 3.4 environment.

Second: There is no default icon theme. Cinnamon uses whatever icon theme you have selected and making any change to icons will hold true across all the DEs you have installed. That's normal.

The thing is, cinnamon uses a totally different windows manager than gnome, so it shouldn't matter whatnyou have set inn gnome. Something must be wrong with the cinnamon packages you installed, maybe one is corrupt (thinking maybe the muffin win manager. 

You could try to purge / remove cinnamon altogether. Or you could use synaptic package manager ( you can get that from the software center) to check cinnamons packages and see If any are marked upgradeable. You would do that by simply searching cinnamon in the search field in synaptic and looking at the list of packaged it returns to be sure they're all marked with green. Wide nilee listed the few packages cinnamon imports.

I suppose there is a chance, too, that muffin isn't compatible with your graphics card. I'd say it's an outside chance, but a chance nontheless. I wouldn't reach that conclusion  until you've tried removing and reinstalling.

EDIT: Further thinking here along hardware lines: Why ar you using gnome classic, no effects? Is it becaue of harware limitations? Cinnamon does need hardware acceleration and that could be why your session is all messed up. Can you boot into GNOME (the first choice in your list) and run that? If your system has trouble running unity 3d or Gnome 3.4, you'll likely have trouble with Cinnmon.

---

### Post by kurt18947 on 2012-06-13
Here is my experience installing Cinnamon on a stock 12.04 install with gnome-shell installed.  I recall reading ..... somewhere ..... :oops:  that muffin could be a problem child. When I installed Cinnamon, I recall getting the choice to install Cinnamon & Muffin separately.  I chose to install Cinnamon but not Muffin.  Here is a screen shot of Synaptic:

[ATTACH]219613[/ATTACH]

As you can see, some Muffin components were still installed but not the whole Muffin package.  Again, I have an otherwise vanilla installation but Cinnamon works and is stable for me.

---

### Post by Shadius on 2012-06-13
> **pete04 said:**
> OK... 
First: you do have the gnome shell package installed. That's what is presenting you with those choices of gnome, classic, etc. Gnome is the gnome 3.4 environment.

Second: There is no default icon theme. Cinnamon uses whatever icon theme you have selected and making any change to icons will hold true across all the DEs you have installed. That's normal.

The thing is, cinnamon uses a totally different windows manager than gnome, so it shouldn't matter whatnyou have set inn gnome. Something must be wrong with the cinnamon packages you installed, maybe one is corrupt (thinking maybe the muffin win manager. 

You could try to purge / remove cinnamon altogether. Or you could use synaptic package manager ( you can get that from the software center) to check cinnamons packages and see If any are marked upgradeable. You would do that by simply searching cinnamon in the search field in synaptic and looking at the list of packaged it returns to be sure they're all marked with green. Wide nilee listed the few packages cinnamon imports.

I suppose there is a chance, too, that muffin isn't compatible with your graphics card. I'd say it's an outside chance, but a chance nontheless. I wouldn't reach that conclusion  until you've tried removing and reinstalling.

EDIT: Further thinking here along hardware lines: Why ar you using gnome classic, no effects? Is it becaue of harware limitations? Cinnamon does need hardware acceleration and that could be why your session is all messed up. Can you boot into GNOME (the first choice in your list) and run that? If your system has trouble running unity 3d or Gnome 3.4, you'll likely have trouble with Cinnmon.

I can boot into GNOME (first option from login). I chose to use GNOME Classic (No effects) because I found Unity to be a bit slow on my system and I prefer the GNOME 2 look. Sometimes I use the regular GNOME Classic, with effects, I suppose you can call it. My system does not support Unity 3D, but runs Unity 2D, but a bit slow. Here's some information from the Unity support test. 

```
shadius@shadius-5410US:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 (RV250 4966) x86/MMX/SSE TCL DRI2
OpenGL version string:  1.3 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no
shadius@shadius-5410US:~$ 
```

I also tried uninstalling Cinnamon via the Ubuntu Software Center since I'm not familiar with doing uninstallations using the Terminal. I do have Synaptic Package Manager and after I uninstalled Cinnamon, I checked in Synaptic Package Manager to make sure it was gone and it was. Then I reinstalled, but I got the same problem again. Stumped. :confused:

---

### Post by vasa1 on 2012-06-13
Cinnamon may go better with Mint since it has been developed by the Mint developer. If you feel the need to run Cinnamon and have trouble doing so with Ubuntu, you could consider trying Mint.

---

### Post by wilee-nilee on 2012-06-13
> **Shadius said:**
> I can boot into GNOME (first option from login). I chose to use GNOME Classic (No effects) because I found Unity to be a bit slow on my system and I prefer the GNOME 2 look. Sometimes I use the regular GNOME Classic, with effects, I suppose you can call it. My system does not support Unity 3D, but runs Unity 2D, but a bit slow. Here's some information from the Unity support test. 

```
shadius@shadius-5410US:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 (RV250 4966) x86/MMX/SSE TCL DRI2
OpenGL version string:  1.3 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no
shadius@shadius-5410US:~$ 
```I also tried uninstalling Cinnamon via the Ubuntu Software Center since I'm not familiar with doing uninstallations using the Terminal. I do have Synaptic Package Manager and after I uninstalled Cinnamon, I checked in Synaptic Package Manager to make sure it was gone and it was. Then I reinstalled, but I got the same problem again. Stumped. :confused:

If you are unable to get the unity 3d the graphics may be the problem what is the card.
  	 	 	 	 	 	   ```
lspci | grep VGA 
```


There are PPA's for cards not in the repos.

---

### Post by Shadius on 2012-06-13
> **wilee-nilee said:**
> If you are unable to get the unity 3d the graphics may be the problem what is the card.
  	 	 	 	 	 	   ```
lspci | grep VGA 
```


There are PPA's for cards not in the repos.

Here ya go wilee,
```
shadius@shadius-5410US:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI R250 If [Radeon 9000] (rev 01)
shadius@shadius-5410US:~$ 

```

---

### Post by Shadius on 2012-06-13
Some interesting news!

Seems that Cinnamon now has Cinnamon 2D for people like me. :) 

[Cinnamon 2D]("http://www.webupd8.org/2012/06/cinnamon-to-get-2d-session-more-new.html")

Now if I could only get Cinnamon to work..:lolflag:

---

### Post by wilee-nilee on 2012-06-13
Use at your own risk, notice the warning at the top, and notice the xswat link as well.

These radeon cards or some anyway are older but I have had them myself and have had success with the xswat ppa.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by pete04 on 2012-06-13
Yeah it looks like a graphics card problem (it's always graphics hardware). And Mint won't run any better. Maybe Mate would, but I have no idea. I think you're out of luck with Cinnamon until that 2d version goes mainstream (read that, too on webup8 a earlier today). 

I have no experience with the xswat. Let us know if it works.

---

### Post by wilee-nilee on 2012-06-13
Hey I also wanted to share some info on how to keep a record of what you have installed, and how to save this info and reload it if needed if you reinstall.

So all package upgrades run in synaptic are in the history in the drop down, you can save each one individually if needed to a gedit.

You can also keep a lists of what you have installed and reload these and install with that list.

This just requires that you install dselect.

I found out how to do this recently and thought it might be helpful to some people. To output this information to a file in your home directory you would use,

This saves the packages installed to home in a gedit.

Code:
dpkg --get-selections > installed-software   

And if you wanted to use the list to reinstall this software on a fresh Ubuntu set up,

This loads that saved list.

Code:
sudo dpkg --set-selections < installed-software

followed by
Code:
sudo dselect

One of the best ways I have found to reinstalling efficiently and having lists of the installed packages is using this easy method.

I also save the /etc/apt/sources.list and the /etc/apt/sources.list.d as well;

The /etc/apt/sources.list.d is where loaded PPA go and others that you may load.

A deselect dialogue opens in the terminal with multiple options including a install from the loaded list.

The key before running the list install is having the sources lists the same, and any keys loaded that night be missing first. If you run a update and upgrade in the terminal after loading the lists again and see a missing key use this command to load it, this would be mainly with PPA's most likely.
                                  ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys "your missing key here"
```

---

### Post by Shadius on 2012-06-13
Thank you wilee! That's very helpful. 

I've attached a screenshot of my Synaptic Package Manager, if that would help in any way.

---

### Post by Shadius on 2012-06-13
> **wilee-nilee said:**
> Use at your own risk, notice the warning at the top, and notice the xswat link as well.

These radeon cards or some anyway are older but I have had them myself and have had success with the xswat ppa.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

I'm going to try this and I will report back.

---

### Post by Shadius on 2012-06-14
Okay so I added that PPA and it seems to have broken things. :( After adding the PPA, I ran the Update Manager, it updated about 83 packages. I tried opening up programs such as Firefox, Chrome, Terminal and none opened. It would just show "Starting Firefox Web Browser" in the panel, but nothing would open. I tried logging out, and nothing. Tried shutting down, nothing. I can only switch users by clicking on my user name, selecting my user name from the drop-down menu and selecting "Switch User" or selecting "Switch User Account" from the drop-down menu. I tried logging into the Cinnamon desktop environment from my user account and it just logged me back into my GNOME Classic (No effects) session. Maybe because I'm still logged into that session. So I thought I'd see if my brother's user account would load Cinnamon, the screenshot shows what I got. So now, I tried shutting down from the login screen, it does nothing! So now I can't shut down my computer or log out of my user account. How do I proceed from here? 

I am posting this from my Mac since no programs will load on my Ubuntu.

---

### Post by wilee-nilee on 2012-06-14
Which PPA the one posted or xswat, and did you do this from synaptic so you have a list of what was installed?

Ideally you would have made that list before you rebooted, you could then remove everything installed.

Here is a link it looks like you would need to run this from a command line from the recovery partition.
[http://askubuntu.com/questions/93534/how-to-remove-a-repository-and-all-its-installed-programs](http://askubuntu.com/questions/93534/how-to-remove-a-repository-and-all-its-installed-programs)

Worse case we can chroot to the OS then run the purge.

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> Which PPA the one posted or xswat, and did you do this from synaptic so you have a list of what was installed?

Ideally you would have made that list before you rebooted, you could then remove everything installed.

I added "deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main", without quotes, to Software Sources via Ubuntu Software Center.

---

### Post by Shadius on 2012-06-14
Unfortunately, I did not make that list. However, Synaptic Package Manager is loading fine. Other problems like the ones I mentioned before aren't loading.

---

### Post by wilee-nilee on 2012-06-14
> **Shadius said:**
> Unfortunately, I did not make that list. However, Synaptic Package Manager is loading fine. Other problems like the ones I mentioned before aren't loading.

Look in the file-history and see if this install was saved. I'm not sure if you use the update manager that it is.

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> Look in the file-history and see if this install was saved. I'm not sure if you use the update manager that it is.

The History is only showing April 2012 and March 2012.

---

### Post by wilee-nilee on 2012-06-14
Try ctrl-alt-t to get a terminal, not sure if the terminal will show true even if you do.

This is why I said at your own risk, and mentioned the xswat, and how to know what was installed and how to have a list of what was installed. ;)

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> Try ctrl-alt-t to get a terminal, not sure if the terminal will show true even if you do.

This is why I said at your own risk, and mentioned the xswat, and how to know what was installed and how to have a list of what was installed. ;)

**Ctrl+Alt+T** was the first thing I tried to get the Terminal. Didn't work. Yupp, I see the risk now. :lolflag: I should've did that list.

---

### Post by wilee-nilee on 2012-06-14
I'm working on a fix, do you have a live ubuntu cd?

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> I'm working on a fix, do you have a live ubuntu cd?

I do, but it's 11.10. Would I be able to make that list now, even though I've already done the install? I'm thinking it would show the packages installed from that PPA and I could remove them?

---

### Post by wilee-nilee on 2012-06-14
**So boot the live cd, open gparted and find the partition that ubuntu is on** and in the first command sub the XX with the letter and number of that partition, then run each command with a copy and paste except for the chroot unmount and the reboot. The 11.10 disc is fine you wil be in the root of the install.

 Notice that some of the commands have no sudo run them as is.

So if the partition is sda5 then the first command should be this as an example. sudo mount /dev/sda5 /mnt

```
sudo mount /dev/sdXX /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
ppa-purge ppa:xorg-edgers/ppa
``````
apt-get update && apt-get upgrade
```Say yes to any upgrades here```
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> **So boot the live cd, open gparted and find the partition that ubuntu is on** and in the first command sub the XX with the letter and number of that partition, then run each command with a copy and paste except for the chroot unmount and the reboot. The 11.10 disc is fine you wil be in the root of the install.

 Notice that some of the commands have no sudo run them as is.

So if the partition is sda5 then the first command should be this as an example. sudo mount /dev/sda5 /mnt

```
sudo mount /dev/sdXX /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
ppa-purge ppa:xorg-edgers/ppa
``````
apt-get update && apt-get upgrade
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```

Should I just reboot by pressing the power button on my computer since it's not bringing up the dialog for me when I select "Shut Down"? Also, I have my Ubuntu on a separate HDD, I know it's sdb, so for the first command, it would be...
```
sudo mount /dev/sdb1/ mnt
```

Correct?

---

### Post by wilee-nilee on 2012-06-14
I forgot one thing you need to install the ppa-purge first before the commands, so when you have the cd booted open the ubuntu software center-edit-software sources, untick the cd and close the center.

Then in the terminal run
```
sudo apt-get update && sudo apt-get install ppa-purge
```Then start at the beginning of my last post.

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> I forgot one thing you need to install the ppa-purge first before the commands, so when you have the cd booted open the ubuntu software center-edit-software sources, untick the cd and close the center.

Then in the terminal run
```
sudo apt-get update && sudo apt-get install ppa-purge
```Then start at the beginning of my last post.

Please advise me on how you would like me to boot into the LiveCD since I can't restart by selecting the option within Ubuntu. Should I just push the power button?

---

### Post by wilee-nilee on 2012-06-14
> **Shadius said:**
> Should I just reboot by pressing the power button on my computer since it's not bringing up the dialog for me when I select "Shut Down"? Also, I have my Ubuntu on a separate HDD, I know it's sdb, so for the first command, it would be...
```
sudo mount /dev/sdb1/ mnt
```Correct?

You can shutdown that way or use a soft reboot, and make sure that is what the partition still is from the live cd, sometimes the HD and a boot media like a disc or thumb get reversed.

Notice my last post on install the ppa purge as well, ask questions if you at all do not understand.

Here is the soft reboot link.

[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)

---

### Post by Shadius on 2012-06-14
Okay wilee, I've done the soft reboot and booted into the LiveCD. I'm getting an "E: Unable to locate package ppa-purge" message. 

Here's my output of the code:
```
ubuntu@ubuntu:~$ sudo apt-get update && sudo apt-get install ppa-purge
Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric-updates InRelease
Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]
Get:2 http://archive.ubuntu.com oneiric Release.gpg [198 B]
Get:3 http://security.ubuntu.com oneiric-security Release [40.8 kB]
Get:4 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Get:5 http://archive.ubuntu.com oneiric Release [40.8 kB]
Get:6 http://archive.ubuntu.com oneiric-updates Release [40.8 kB]  
Get:7 http://security.ubuntu.com oneiric-security/main i386 Packages [127 kB]  
Get:8 http://archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]          
Get:9 http://security.ubuntu.com oneiric-security/restricted i386 Packages [3,939 B]
Get:10 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:11 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [71 B]
Get:12 http://security.ubuntu.com oneiric-security/main Translation-en [59.8 kB]
Get:13 http://security.ubuntu.com oneiric-security/restricted Translation-en [978 B]
Get:14 http://archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]
Get:15 http://archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]
Get:16 http://archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]
Get:17 http://archive.ubuntu.com oneiric-updates/main i386 Packages [358 kB]
Get:18 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [6,631 B]
Get:19 http://archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:20 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [72 B]
Hit http://archive.ubuntu.com oneiric/main Translation-en   
Hit http://archive.ubuntu.com oneiric/restricted Translation-en
Get:21 http://archive.ubuntu.com oneiric-updates/main Translation-en [162 kB]
Get:22 http://archive.ubuntu.com oneiric-updates/restricted Translation-en [1,547 B]
Fetched 2,083 kB in 7s (278 kB/s)                                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ppa-purge
ubuntu@ubuntu:~$ 

```

---

### Post by wilee-nilee on 2012-06-14
Actually I was not correct but I think I am this time DOH, the ppa-purge needs to be installed in the ubuntu install. So confirm the HD partition with gparted, and sub the XX, and here is the correct command set.

```
sudo mount /dev/sdXX /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
apt-get install ppa-purge
``````
ppa-purge ppa:xorg-edgers/ppa
``````
apt-get autoremove && apt-get autoclean && apt-get clean
``````
apt-get update && apt-get upgrade
```Say yes to any upgrades here```
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```I hope this works as much as you do

---

### Post by Shadius on 2012-06-14
:lolflag: Okay so should I re-check the box in Ubuntu Software Center that you previously said to uncheck, or leave it as it is? Also, I've attached a screenshot of GParted just so that we're both sure that my it's "sdb1" so my code would be:
```
sudo mount /dev/sdb1 mnt
```

Correct me if I'm wrong.

Oops, forgot the screenshot.

---

### Post by wilee-nilee on 2012-06-14
> **Shadius said:**
> :lolflag: Okay so should I re-check the box in Ubuntu Software Center that you previously said to uncheck, or leave it as it is? Also, I've attached a screenshot of GParted just so that we're both sure that my it's "sdb1" so my code would be:
```
sudo mount /dev/sdb1 mnt
```Correct me if I'm wrong.

You just need the cd to chroot into the Ubuntu so you can leave as is.

yes sub the sudo mount /dev/sdb1 mnt, or just the b1 for the XX

The gparted does not show but if you are sure it is sdb1 carry on.

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> You just need the cd to chroot into the Ubuntu so you can leave as is.

yes sub the sudo mount /dev/sdb1 mnt, or just the b1 for the XX

The gparted does not show but if you are sure it is sdb1 carry on.

Sorry wilee, I forgot the screenshot. Here it is again. Confirm that my code is right before I move on. :)

---

### Post by wilee-nilee on 2012-06-14
> **Shadius said:**
> Sorry wilee, I forgot the screenshot. Here it is again. Confirm that my code is right before I move on. :)

Looks good it is a ext4 if you know that is the ubuntu partition proceed.

You know about the dropdown in the right top corner that will show all HD's I assume.

This supposedly works, but I do see people that complain it didn't for them, but here is a link on using it for the exact same thing, different release is all.
[http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/](http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/)

I will do a few hail marries for you. lol

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> Looks good it is a ext4 if you know that is the ubuntu partition proceed.

You know about the dropdown in the right top corner that will show all HD's I assume.

This supposedly works, but I do see people that complain it didn't for them, but here is a link on using it for the exact same thing, different release is all.
[http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/](http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/)

I will do a few hail marries for you. lol

:lolflag: Got some errors here. 

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get install ppa-purge
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following package was automatically installed and is no longer required:
  libllvm3.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-parser-perl libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl ppa-purge
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,931 kB of archives.
After this operation, 9,169 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libboost-iostreams1.46.1 i386 1.46.1-7ubuntu3
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libcwidget3 i386 0.5.16-3.1ubuntu1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main aptitude i386 0.6.6-1ubuntu1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libsub-name-perl i386 0.05-1build2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libclass-accessor-perl all 0.34-1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libio-string-perl all 1.08-2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libtimedate-perl all 1.2000-1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe ppa-purge all 0.2.8+bzr56
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/boost1.46/libboost-iostreams1.46.1_1.46.1-7ubuntu3_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cwidget/libcwidget3_0.5.16-3.1ubuntu1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptitude/aptitude_0.6.6-1ubuntu1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsub-name-perl/libsub-name-perl_0.05-1build2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libclass-accessor-perl/libclass-accessor-perl_0.34-1_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libio-string-perl/libio-string-perl_1.08-2_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtimedate-perl/libtimedate-perl_1.2000-1_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libparse-debianchangelog-perl/libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/ppa-purge/ppa-purge_0.2.8+bzr56_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/# 

```

How should I proceed?

---

### Post by wilee-nilee on 2012-06-14
Not sure to be honest the apt-get install ppa-purge should just install that, is that all the commands used in this error list you have posted?

Try again and choose no, you just want the ppa-purge installed.

The only yes to a upgrade would be after the update & upgrade later in the command list

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> Not sure to be honest the apt-get install ppa-purge should just install that, is that all the commands used in this error list you have posted?

Try again and choose no, you just want the ppa-purge installed.

The only yes to a upgrade would be after the update & upgrade later in the command list

Yupp, that was the only command I've run so far. Will try again with the "n" option.

---

### Post by Shadius on 2012-06-14
When I choose "n", it just aborts. Gives "Abort."

```
root@ubuntu:/# apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libllvm3.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-parser-perl libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl ppa-purge
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,931 kB of archives.
After this operation, 9,169 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
root@ubuntu:/# 

```

---

### Post by Elfy on 2012-06-14
offtopic posts removed - please keep ontopic

---

### Post by Shadius on 2012-06-14
Wilee, could it have something to do with the repositories? 

Take a look at the screenshot.

---

### Post by wilee-nilee on 2012-06-14
I'm not really sure from here, I don't know other then to try the ```
apt-get autoremove && apt-get autoclean && apt-get clean 
```before the install ppa-purge. then follow the list from the ppa-purge install.

---

### Post by wilee-nilee on 2012-06-14
> **Shadius said:**
> Wilee, could it have something to do with the repositories? 

Take a look at the screenshot.

should not be you are actually in the ubuntu install at the point you see the root #

---

### Post by Shadius on 2012-06-14
Oh okay. I will try what you said before.

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> I'm not really sure from here, I don't know other then to try the ```
apt-get autoremove && apt-get autoclean && apt-get clean 
```before the install ppa-purge. then follow the list from the ppa-purge install.

Okay, after I chose the "n" option I did:
```
apt-get update
``` 
and that seemed to give errors as well, then I exited out of the Terminal. 

Now here is my output now:
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libllvm3.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-parser-perl libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl ppa-purge
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,931 kB of archives.
After this operation, 9,169 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libboost-iostreams1.46.1 libcwidget3 aptitude libsub-name-perl
  libclass-accessor-perl libio-string-perl libtimedate-perl
  libparse-debianchangelog-perl ppa-purge
Install these packages without verification [y/N]? 

```

---

### Post by wilee-nilee on 2012-06-14
So use the unmount command.
```
Exit chroot: CTRL-D on keyboard
```And lets be really safe lets reboot the cd, just for chuckles, then try again but just adding the ```
apt-get autoremove && apt-get autoclean && apt-get clean 
``` Before the ppa-purge install, and run the rest of the commands as they are.

There is another way to chroot in but I don't think that is the problem.

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> So use the unmount command.
```
Exit chroot: CTRL-D on keyboard
```And lets be really safe lets reboot the cd, just for chuckles, then try again but just adding the ```
apt-get autoremove && apt-get autoclean && apt-get clean 
``` Before the ppa-purge install, and run the rest of the commands as they are.

There is another way to chroot in but I don't think that is the problem.

Okay, let's start over. My head is circling with codes. Can you post the entire code back onto this page so I don't have to go back pages? Thanks. I'm rebooting now. Give me 5 minutes!

---

### Post by Shadius on 2012-06-14
Okay, I'm back and ready to start again!

---

### Post by Shadius on 2012-06-14
> **wilee-nilee said:**
> Actually I was not correct but I think I am this time DOH, the ppa-purge needs to be installed in the ubuntu install. So confirm the HD partition with gparted, and sub the XX, and here is the correct command set.

```
sudo mount /dev/sdXX /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
apt-get install ppa-purge
``````
ppa-purge ppa:xorg-edgers/ppa
``````
apt-get autoremove && apt-get autoclean && apt-get clean
``````
apt-get update && apt-get upgrade
```Say yes to any upgrades here```
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```I hope this works as much as you do

> **wilee-nilee said:**
> So use the unmount command.
```
Exit chroot: CTRL-D on keyboard
```And lets be really safe lets reboot the cd, just for chuckles, then try again but just adding the ```
apt-get autoremove && apt-get autoclean && apt-get clean 
``` Before the ppa-purge install, and run the rest of the commands as they are.

There is another way to chroot in but I don't think that is the problem.

So this should be the code with all the adjustments....
```
sudo mount /dev/sdb1 /mnt
```
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
```
```
sudo chroot /mnt
```
```
apt-get autoremove && apt-get autoclean && apt-get clean
```
```
apt-get install ppa-purge
```
```
ppa-purge ppa:xorg-edgers/ppa
```
```
apt-get update && apt-get upgrade
```
Say yes to any upgrades here

Exit chroot: **Ctrl+D** on keyboard
```
sudo reboot
```

Correct?

---

### Post by wilee-nilee on 2012-06-14
> **Shadius said:**
> So this should be the code with all the adjustments....
```
sudo mount /dev/sdb1 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
apt-get autoremove && apt-get autoclean && apt-get clean
``````
apt-get install ppa-purge
``````
ppa-purge ppa:xorg-edgers/ppa
``````
apt-get update && apt-get upgrade
```Say yes to any upgrades here

Exit chroot: **Ctrl+D** on keyboard
```
sudo reboot
```Correct?
Looks good.

---

### Post by Shadius on 2012-06-14
Tried again and still got errors. :( 

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get autoremove && apt-get autoclean && apt-get clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libllvm3.0
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 20.3 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 294840 files and directories currently installed.)
Removing libllvm3.0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@ubuntu:/# apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-parser-perl libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl ppa-purge
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,931 kB of archives.
After this operation, 9,169 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libboost-iostreams1.46.1 i386 1.46.1-7ubuntu3
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libcwidget3 i386 0.5.16-3.1ubuntu1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main aptitude i386 0.6.6-1ubuntu1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libsub-name-perl i386 0.05-1build2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libclass-accessor-perl all 0.34-1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libio-string-perl all 1.08-2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libtimedate-perl all 1.2000-1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe ppa-purge all 0.2.8+bzr56
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/boost1.46/libboost-iostreams1.46.1_1.46.1-7ubuntu3_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cwidget/libcwidget3_0.5.16-3.1ubuntu1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptitude/aptitude_0.6.6-1ubuntu1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsub-name-perl/libsub-name-perl_0.05-1build2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libclass-accessor-perl/libclass-accessor-perl_0.34-1_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libio-string-perl/libio-string-perl_1.08-2_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtimedate-perl/libtimedate-perl_1.2000-1_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libparse-debianchangelog-perl/libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/ppa-purge/ppa-purge_0.2.8+bzr56_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/# 

```

---

### Post by Shadius on 2012-06-14
Tried doing ```
apt-get update
``` 
Got this:

```
Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main Sources                                                   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted Sources                                             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main i386 Packages       
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted i386 Packages   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe i386 Packages     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse i386 Packages   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main Translation-en_US     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main Translation-en        
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe Translation-en_US                                     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe Translation-en                                        
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/main i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/restricted i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/main i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/main i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/jconti/gnome3/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/vincent-c/conky/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en_US  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/jconti/gnome3/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/jconti/gnome3/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/jconti/gnome3/ubuntu/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/jconti/gnome3/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/vincent-c/conky/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/vincent-c/conky/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/vincent-c/conky/ubuntu/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/vincent-c/conky/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:/# 

```

---

### Post by Shadius on 2012-06-15
Don't know if this is relevant, but I thought I'd just show it.

---

### Post by wilee-nilee on 2012-06-15
Since you are in a chroot the disc is not relevant other then as a transport there, you are in the root of the install 

Do you have the ethernet plugged in now not sure if it may be needed in the install root you are chrooted into, that may be the error.

If that is not the case reboot to the install to see what&#8217;s up after exiting the chroot.

If you can't get in then use the recovery and the fix packages choice and have the ethernet plugged in.

I don't think anything has changed you will need somebody better at this if it can be done I think.

---

### Post by Shadius on 2012-06-15
> **wilee-nilee said:**
> Since you are in a chroot the disc is not relevant other then as a transport there, you are in the root of the install 

Do you have the ethernet plugged in now not sure if it may be needed in the install root you are chrooted into, that may be the error.

If that is not the case reboot to the install to see what’s up after exiting the chroot.

If you can't get in then use the recovery and the fix packages choice and have the ethernet plugged in.

I don't think anything has changed you will need somebody better at this if it can be done I think.

Yeah, the ethernet is always plugged in. I don't know why it's failing to fetch the packages. I don't know why it's saying "No address associated with host name" either.

---

### Post by Shadius on 2012-06-15
Good news! I've successfully purged the PPA by using the 12.04 LiveCD instead of the 11.10 LiveCD. I guess the versions had to be the same. I've recovered my Ubuntu. I'm reluctant to try that xswat PPA now after going through this mess. Maybe I'll try setting up the dselect and then try with the xswat PPA. Thanks wilee-nilee for the help and sticking it out with me. Much appreciated.

---

### Post by pete04 on 2012-06-15
Wow. I'm bookmarking this thread for future reference. Good work Shadius and Wilee Nilee.

Shadius, If it makes you feel maybe a little bit better, I thought I'd relay my Cinnamon experiences after a week:

Long story short, I love the idea and a lot of the implementation, but it's just not a stable desktop environment yet. I continued to gett hard graphical lockups (used wilee-nilee's soft reboot once -- thanks!) and there are some panel bugs that are just plain annoying -- the worst of which is that the windows list begins to drift to the left of the screen as windows are added (for me it was four and more) and it begins to crowd and then cover the launcher and menu. There's a lame workaround: put the windows list to the left of everything, but why bother...

I'm going to keep my eyes on Cinnamon, because, if the bugs get fixed (version 1.5?) I'll gladly give it another spin.

Right now, though, I'd be hard pressed to recommend it to anyone, even though I had recommended it here and elsewhere.

---

### Post by wilee-nilee on 2012-06-15
> **Shadius said:**
> Good news! I've successfully purged the PPA by using the 12.04 LiveCD instead of the 11.10 LiveCD. I guess the versions had to be the same. I've recovered my Ubuntu. I'm reluctant to try that xswat PPA now after going through this mess. Maybe I'll try setting up the dselect and then try with the xswat PPA. Thanks wilee-nilee for the help and sticking it out with me. Much appreciated.

That is great news. ;)

---

### Post by Shadius on 2012-06-15
> **pete04 said:**
> Wow. I'm bookmarking this thread for future reference. Good work Shadius and Wilee Nilee.

Shadius, If it makes you feel maybe a little bit better, I thought I'd relay my Cinnamon experiences after a week:

Long story short, I love the idea and a lot of the implementation, but it's just not a stable desktop environment yet. I continued to gett hard graphical lockups (used wilee-nilee's soft reboot once -- thanks!) and there are some panel bugs that are just plain annoying -- the worst of which is that the windows list begins to drift to the left of the screen as windows are added (for me it was four and more) and it begins to crowd and then cover the launcher and menu. There's a lame workaround: put the windows list to the left of everything, but why bother...

I'm going to keep my eyes on Cinnamon, because, if the bugs get fixed (version 1.5?) I'll gladly give it another spin.

Right now, though, I'd be hard pressed to recommend it to anyone, even though I had recommended it here and elsewhere.

Pete04, I really appreciate you telling me your experience with Cinnamon. :) To me, Cinnamon is a desktop environment that I have been waiting for! I think it combines the best of the GNOME Classic and GNOME Shell environments. Cinnamon seems very promising so I'll be keeping a watch on it as well. As for now, I think I'll agree with you in saying that some bugs need to be addressed. I'm especially excited about Cinnamon 2D! Maybe then it'll work on my computer. Thanks for sharing. :)

---

