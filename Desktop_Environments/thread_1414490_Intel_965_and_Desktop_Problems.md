---
title: "Intel 965 and Desktop Problems"
date: 2010-02-23
forum: Desktop Environments
---

### Post by seanbw on 2010-02-23
My integrated graphics card is blacklsted by Compiz and therefore can't use it. I  have tried the skip_checks=yes option and the sudo gdm stop and start commands but it doesnt seem to work. In fact today marks the second week I have spent on trying to resolve the issue with no success. I gave up on compiz yesterday and reinstalled ubuntu for the third time and  then downloaded cairo dock to replace compiz (this is after I removed compiz) 
same problem happened though which is why I am now asking foe assistance, I am beat and need help.
My problem is a bit simple but total. Each time I installed Cairo Dock or awn applet (and I  have installed each once and had to reinstall ubuntu each time)  and I reboot, I get a blank screen and ctrl+Alt+F1 or ctrl+Alt+F2 or even ctrl+Alt+F6 does nothing for the screen. I don't get a terminal I can enter any commands into neither does entering Alt+F7 help . In fact it seems as if my window can't be drawn on the screen and I effectively had to reinstall ubuntu for the sixth and final time today.
So it appears that because I am on Acer 5720 which is using the GMA 965 chip, I cant use the Xorg server,
When I still had a screen each time I ran compiz in a terminal, all it complained about was not being able to  draw pixmaps and having glx something version 1.2 instead of 1.3
I would like to install cairo dock but since the general result is a blank screen after reboot, I would appreciate if anyone can help me with key combinations that will get me out of the blank screen and a command sequence that will unload the Cairo dock and force the laptop to use a simple windows manager that works.
To test this, I  intend to install another partition with ubuntu so that if I cant sort it out, I wont lose all the work I've already done on my existing installation.
Please can anyone help? Thanks

---

### Post by seanbw on 2010-02-24
bump! anybody? helpppp.....

---

### Post by andrea000 on 2010-02-24
Ok compiz can still work have you installed ccsm and any 
hardware drivers for your card if so in the terminal type
> sudo gedit /usr/bin/compiz
You will need to edit this file. Look for the lines
> # blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2a02 " # Intel GM965
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T
Don't forget to back up the original file before
you begin now take the pound sign out of the lines
pertaining to your particular video card and save
the file.

---

### Post by seanbw on 2010-02-25
Andrea - many thanks for coming to my aid. I was beginning to despair. My video chip is mentioned on two lines and I have unset both. See lines underlined, blue and made bold . Question is - should I have?
```
# Driver whitelist
WHITELIST="nvidia intel ati radeon radeonhd i810 fglrx"

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2[COLOR=Blue]_ **8086:2a0**2_[/COLOR] 8086:2a12"  # intel 965
T="$T **[COLOR=Blue]_8086:2a02_[/COLOR]** " # Intel GM965
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T
```
Also I ran compiz-check to identify the video chip version and it did a strange thing-it reported that my configuration is fine!!! What is going on?
The compiz-check output was as below:
```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...                 [ OK ]
 Checking for FBConfig...                                  [ OK ]
 Checking for hardware/setup problems...         _**[COLOR=Blue] [ OK ] :confused:[/COLOR]**_
```
It used to report:
```
Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...          **_[COLOR=Blue] [WARN][/COLOR]_**

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y
```

Andrea - I have not configured compiz since I reinstalled ubuntu yeterday and although my system have all the compiz applications including the compiz settings manager but that was because another application I needed downloaded them.
I would appreciate your assistance in following this through but I need to identify the commands I can enter to get my  screen redrawn because as I said each time I run the openGL features, my laptop freezes and forces me to restart.
When I restart, all I get is  a blank screen and Ctrl-Alt-F1 or any combination of keys does not do anything and I have to reinstall.
What key combination do you think I can enter that will result in a default ubuntu screen thatb will enable me to correct problem?
I am glad you chipped in. I really need assistance.
Thanks. Sean

---

### Post by claracc on 2010-02-25
You always can boot in the recovery mode from grub and try to recover your original xorg file and the default settings for the graphics. Any way, I think it is not a good idea to remove your blacklisted card from the file, if it is there is for some reason.

Any case I have a laptop hp compaq 6720s with  VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
and i can run compiz with normal effects (no extra ) however some errors occurs in certain windows.

Now I use metacity and I am happy with it, no visual effects, but I don't need. To replace compiz for metacity you have to write in a xterm:  metacity --replace. In order to do it through GUI I recommend you to install compiz fusion (it is in repositories). With compiz fusion you can select what windows manager you want to use.

About the keys to run a xterm, perhaps you don't have activated in system --> preferences --> key combinations, the run in a xterm action, check it, and define a key combination for this action.

Regards

---

### Post by seanbw on 2010-02-25
> You always can boot in the recovery mode from grub and try to recover  your original xorg file and the default settings for the graphics. 

Please let me understand this properly.I go into recovery and replace my existing xorg.conf with the original igenerated. Will this return me to the original state where compiz was not drawing cubes etc on my screen? Should I also apt-get remove cairo dock at this stage? What command tells openGL to also shut down? This is because Cairo Dock also  gives me this same problem.

> To replace compiz for metacity you have to write in a xterm: metacity --replace.

You mean xorg.conf? what is xterm? Sorry I only got into ubuntu about two weeks ago so I am really struggling. I have installed fusion before and it replaces my windows manager on the fly but if i reboot, I get the same blank screen and no access to virtual console although your suggestion above is a step I havent taken b4.
Is it possible to use only metacity and cairo-dock? Its only the dock effect i want. .I can live without the cube effect. 

> About the keys to run a xterm, perhaps you don't have activated in system --> preferences --> key combinations, the run in a xterm action, check it, and define a key combination for this action.

Yes this was another error I made. I have just defined the ctrl-alt-bkspace combination to turn compiz off but i havent tried it. 
Thinking this whole debacle over, it seems that the problem is with openGL because i have the same problems with cairo-dock, awn applets and compiz. If I am right, what commands can i issue to reset openGL? None of the blogs including Forlong or even the compiz site mentions it.
When I get through this maybe I will write a how to for GMA 965 computers. It is both frustrating and challenging but not in equal parts.
Claracc I am grateful for your assistance. If my questions sound daft, it is because I have never used anything but windows before. Thanks for all your assistance.

---

### Post by claracc on 2010-02-25
To boot in recovery mode, you turn on your computer and when grub is loaded it shows a display with various options, so  you select in this screen instead of your current kernel:

Ubuntu 9.10 Kernel x.x.xx-xx generic (recovery mode)

In the next display you have some options, you select xfix Try to fix xserver. You try to repair first your graphics system coming back to default settings, then reboot and login as normal (not recovery) and see if problem persists.
When you boot in recovery mode, also with the option dpkg repair broken packages perhaps you could repair compiz or cairo dock.

I think you can run cairo dock with metacity, you don't need compiz.

Xterm is the terminal (console), command line.

---

### Post by seanbw on 2010-02-25
Thank you. I'll get there.
I will try this tomorrow and come back but I have a related issue that I think will affect the outcome. I have mapped Ctrl+Alt+ Bkspace to resetting Xserver but I seem to lose the mapping each time I reboot. It just started happening after installing moblock but can't be sure.
I am thinking of using ```
 gnome-keyboard-properties 
``` with generic UK layout but the help-all option was not very helpful.
I'll post the outcome 2morrow. Many thanks for your time. Cheers

---

### Post by fabounet on 2010-02-26
you can activate the composite of Metacity and then use it with Cairo-Dock
the command to launch it without opengl is "cairo-dock -c"
but most Intel cards now have good drivers enougth to run the opengl version, so maybe you should try installing the latest drivers if it's not already done.

---

### Post by seanbw on 2010-03-02
Thanks I have tried all above but not in my main desktop. I installed a second ubuntu and installed the same applications so it is the same. THe problem returned but I have not reinstalled a I think its a problem with my laptop.
I have not installed drivers for the graphics card becaiuse frankly I am a little busy right now and I know how extensive drivers can mess up my system. However I need assistance in breaking the blank screen I've got now. When I log into recovery mode, I try repair the server and it tries to fix broken packages and etc and eventually grinds to a halt and says fine.
I then boot back into the generic mode and meet my blank screen.
What sequence of commands can I issue in a logical order that will achieve the following:

[LIST=1]
[*] reset the graphics package that draws the screen so it goes back to the original state of not using compiz/cairo dock but the gnome windows manager
[*]tell the system to redraw my screen using just gnome windows manager
[/LIST]
1 and 2 might actually be the same but excuse my ignorance. I am new to ubuntu but I don't think I'll be going back to windows any time soon.
Thank you

---

### Post by andrea000 on 2010-03-02
I am not sure if opengl would have anything to do with
the problem your having or not i think the line in bold
is the one your looking for but i would just leave it the
way it is as for opengl i would just use compiz or opengl
and not both.I don't know alot about what opengl and compiz
together would do sorry
> [T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
**T="$T 8086:2a02 " # Intel GM965**
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)

as to this error i believe compiz is just complaining about
your video card
> Checking for hardware/setup problems...          [ OK ] :confused:

---

