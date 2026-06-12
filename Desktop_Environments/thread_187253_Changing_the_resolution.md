---
title: "Changing the resolution"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Curlydave on 2006-06-02
How do I change the resolution? I somehow made it through the installation process with an install window twice the size of the default and unchangable resolution by moving the window around alot. 

I installed it and booted up and I still can't change to a usable resolution. It won't let me change it in the "change resolution" menu option. How do I fix this?

---

### Post by BaffledMollusc on 2006-06-02
[QUOTE=Curlydave]How do I change the resolution? I somehow made it through the installation process with an install window twice the size of the default and unchangable resolution by moving the window around alot. 

I installed it and booted up and I still can't change to a usable resolution. It won't let me change it in the "change resolution" menu option. How do I fix this?[/QUOTE]
I had the same problem. There is a standard way to fix it (which didn't work for me) and a more involved way (which fixed the resolution error for me, but introduced another bug that means my PC hangs when I try to shut down).

The obvious thing to try is to look at your /etc/X11/xorg.conf configuration and see if you have all the resolutions you want to use. If you don't, add them, and the next time you boot up you should have the options of the resolutions you want in the menu option.

If that fails, what worked for me was to install the proprietory binary driver for my video card (an ATI X800Pro) using synaptic, although as I said, that seems to have introduced another bug.

If you're new to linux, the above stuff might not make sense, so if it doesn't here's a step by step instruction list of what you need to do to accomplish the first solution.

1. Open a terminal window by going to the menu Applications->Accessories->Terminal

2. In this terminal type "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup" This makes a backup of the file you're about to change.

3. In the terminal type "sudo gedit /etc/X11/xorg.conf" This will open a text editor with the file you need to change.

4. Go the part in the file where it says Section "Screen". There should be a number of subsections called "display". I've posted the section of my file at the end of this post so you can compare.

5. Each of the subsections correspond to a colour depth and resolutions you can choose at that colour depth. Add the resolutions you want to each section, i.e. "1024x768" as in my example file at the end. If the resolutions you want are already there, then this is not the problem, unfortunately.

6. Click on "Save" in the text editor, and reboot. You should now be able to choose the resolution you want. If you can't, you have my problem, and like I said, installing the proprietory driver for my video card kind of solved the problem.



Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by tha_rainman on 2006-06-02
1. Make a backup of /etc/X11/xorg.conf.

2. **$ sudo /etc/init.d/gdm stop** This will stop GDM

3. **$ sudo dpkg-reconfigure xserver-xorg** Reconfigure Xorg, this will auto detect everything and you will be able to select the resolutions you wish to use. Its a wizard interface which is pretty straightforward. In the driver selection screen you should choose the right driver (I'm not sure about ATI but for nvidia users we are told to choose 'nvidia' and not 'nv'.

4.  **$ sudo /etc/init.d/gdm start** This will restart your GDM using the new settings.

---

### Post by Christopher on 2006-06-03
I type sudo gedit /etc/X11/xorg.conf into console and i get this "sudo: timestamp too far in the future: Jun  3 02:57:17 2006"  Any ideas? Thank you in advace.

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=Christopher]I type sudo gedit /etc/X11/xorg.conf into console and i get this "sudo: timestamp too far in the future: Jun  3 02:57:17 2006"  Any ideas? Thank you in advace.[/QUOTE]
Does Ubuntu have the correct date and time (top right of screen)?

Edit: You can use the solution posted above rather than my one of editing the xorg.conf file if you like. I just found the "dpkg-reconfigure xserver-xorg" wizard even less intuitive than editing the conf file. It asked me a large number of incomprehensible questions about my mouse, for example, questions that I had no idea how to answer.

---

### Post by Christopher on 2006-06-03
[QUOTE=BaffledMollusc]Does Ubuntu have the correct date and time (top right of screen)?

Edit: You can use the solution posted above rather than my one of editing the xorg.conf file if you like. I just found the "dpkg-reconfigure xserver-xorg" wizard even less intuitive than editing the conf file. It asked me a large number of incomprehensible questions about my mouse, for example, questions that I had no idea how to answer.[/QUOTE]

Ok , i synced the time with the internet server, then i proceeded to change my resolution like you explained and saved then rebooted and got an error about xserver not being set up properly so i did a sudo dpkg-reconfigure xserver-xorg and its telling my xserver-org isnt installed..hehe?

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=Christopher]Yep, I have the correct date and time.[/QUOTE]
Well, it was worth a shot. I'm afraid I have no clue.

---

### Post by Christopher on 2006-06-03
[QUOTE=BaffledMollusc]Well, it was worth a shot. I'm afraid I have no clue.[/QUOTE]


Ok , i synced the time with the internet server, then i proceeded to change my resolution like you explained and saved then rebooted and got an error about xserver not being set up properly so i did a sudo dpkg-reconfigure xserver-xorg and its telling my xserver-org isnt installed..hehe?

---

### Post by Christopher on 2006-06-03
Whats the command to backup my xorg.conf?

---

### Post by Christopher on 2006-06-03
Is there a way to get my xserver-org back?

---

### Post by chameleon_789 on 2006-06-03
To backup your xorg.conf, type *sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup*, then if things mess up you can type *sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf* to get it back. 

If you can't be arsed with all the sudos in front of everything, type *sudo -s -H* and you'll be magically transformed into a super user, just type *exit* to change back to the default user (you might want to do that before restarting gdm).

Can you not change the resolution in System / Preferences / Screen Resolution ? (Is your X server even working?)

---

### Post by Christopher on 2006-06-03
its telling my xserver-org isnt installed..hehe?

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=Christopher]its telling my xserver-org isnt installed..hehe?[/QUOTE]
When does it tell you this, and what is the exact message? 

You mean you get this message when you type "dpkg-reconfigure xserver-xorg" in a terminal? Or when you reboot? Do you even have a graphical desktop when you reboot?

---

### Post by Christopher on 2006-06-03
[QUOTE=BaffledMollusc]When does it tell you this, and what is the exact message? 

You mean you get this message when you type "dpkg-reconfigure xserver-xorg" in a terminal? Or when you reboot? Do you even have a graphical desktop when you reboot?[/QUOTE]

When i rebooted i had no GUI, so i typed my username & password and proceeded to type dpkg-reconfigure xserver-xorg and that when it told me i had no xserver-xorg installed.:confused:  This is weird I have done a gedit before to my xorg.conf and never had any issues.

---

### Post by chameleon_789 on 2006-06-03
I have a feeling you might have accidently uninstalled something which xserver-org depended on, in which case typing **sudo apt-get install xserver-xorg** will reinstall it.

---

### Post by Christopher on 2006-06-03
[QUOTE=chameleon_789]I have a feeling you might have accidently uninstalled something which xserver-org depended on, in which case typing **sudo apt-get install xserver-xorg** will reinstall it.[/QUOTE]

Ok i did a **sudo apt-get install xserver-xorg** and it says i already have the newest version so i again tried to run dpkg-reconfigure and its telling me its not installed again...lol?](*,)

---

### Post by Christopher on 2006-06-03
[QUOTE=Christopher]Ok i did a **sudo apt-get install xserver-xorg** and it says i already have the newest version so i again tried to run dpkg-reconfigure and its telling me its not installed again...lol?](*,)[/QUOTE]

Im just gonna do a fresh install again, see what happens. Thank you very much for your time.

---

### Post by chameleon_789 on 2006-06-03
Haha... np... that's what I did :)

---

### Post by heffo_j on 2006-06-03
I had a similar problem but rather than a complete reinstall I did a apt-get dist-update and that seemed to do the trick. I also mucked about with the dpkg-reconfig xserver-xorg and just okayed all the default suggestions. Look at this thread for help [http://www.ubuntuforums.org/showthread.php?t=186219](http://www.ubuntuforums.org/showthread.php?t=186219)

Regards
John

---

### Post by Christopher on 2006-06-03
I figured out the problem, I wasnt typing it like this sudo dpkg-reconfigure xserver-xorg, I was typing it xserver-org. all is fixed now thanks to help of tseliot here  [http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)   .

---

