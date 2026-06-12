---
title: "Bouncing Icons?"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by 4l13n666 on 2008-03-03
Hi,

I have installed CumpizConfig and got the 3D cube rotation working. Now i have seen some videos on Youtube where you can have bouncing icons. The video shows the user dragging his icons across the screen and when he releases the mouse button, the icons fall down to the bottom of the screen and bounce around.

My question is quite simple. How do i get these icons and how do i make them bounce? I have tried installing the "Dock" but there was an error so i could not use the program. The dock i am talking about can be found on the community docks tab on [http://help.ubuntu.com](http://help.ubuntu.com) and then navigate to the "Eye Candy" section.

Is there a terminal command to get this feature? I really want to have this feature! :)

---

### Post by erginemr on 2008-03-03
Hi Erik,

If this is what you are referring to:
[http://www.youtube.com/watch?v=bYsxaMyFV2Y](http://www.youtube.com/watch?v=bYsxaMyFV2Y)

then the name of he app is "kiba-dock". Google is your friend.

---

### Post by 4l13n666 on 2008-03-03
Hello again mate!

I have found a guide for something called WMA. What is WMA? And is the "Kiba-dock" avaliable for Gutsy?

x--EDIT! 

This "Kiba-dock" you are referring to, will it provide me with all the features on screen that the video showed or would i need to install further programs?

---

### Post by 4l13n666 on 2008-03-03
Another thing i forgot to mention was this.
This link: [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127) shows a detailed guide to set up the kiba dock, but he mentioned something about compiling. I don't know jack about compiling. Not even the definition of the word :P So should i just follow this guide step by step and copy paste the commands that he posted one by one and it will work?

And finally, what is XGL? Is it an addon for lets say CompizConfig to make it simple because thats what i use, with even more features?

---

### Post by dark_harmonics on 2008-03-03
YEa just copy/paste them. I've had this work for me a few times but I had problems with the 64 bit version. Compiling isnt that hard. Most times its some sort of configure, make and make install commands that are completely automated. If you copy/paste for that guide, you should be fine though. 

I personally prefer the cairo-dock over kiba-dock but i use both (on different computers). Cairo doesnt do the cool bouncy icons but it does the parabolic zoom (like on a mac) and i just love the weather applet that comes with it. 

Dont forget that for either dock to work properly you will need to have a compositing manager like compiz running.

---

### Post by 4l13n666 on 2008-03-03
Alright i'm downloading everything now. After the part where the following code ( sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev ) is, he mentions something about making a directory. Is this something i have to perform manually or will the code after that solve this issue?

---

### Post by 4l13n666 on 2008-03-03
Alright now kiba dock is installed and i got the following error at startup:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Failed to connect to socket /tmp/dbus-z7iU56nRly: Connection refused

GNOME will still try to restart the Settings Daemon next time you log in.

Don't know if this has anything to do with kiba dock. Also where do i open the kiba dock? Its installed but i can't find the dock itself!

---

### Post by erginemr on 2008-03-03
This is a Gnome bug haunting Gutsy users from time to time. All you need to do is open Nautilus and delete what is inside /tmp folder and re-login.

---

### Post by erginemr on 2008-03-03
Sure kiba-dock has fancy effects, yet I find it excessively fancy for a workable docking application. I would suggest you to try AWN, Avant Window Navigator too. Maybe this is the same WMA that you are referring to.

What's more, it is already in the repositories so you don't have to mess with compiling. All you need to do is enable multiverse, universe, etc. From &#8220;Software Resources&#8221; and install &#8220;avant-window-navigator&#8221; and &#8220;awn-manager&#8221; from Synaptic.

---

### Post by 4l13n666 on 2008-03-03
> **erginemr said:**
> This is a Gnome bug haunting Gutsy users from time to time. All you need to do is open Nautilus and delete what is inside /tmp folder and re-login.

What is Nautilus? I can't seem to find it. Also, now when i relogged, the new theme i had when i first restarted my system, is gone. So i can't open Kiba-dock because there is no icon or anything. And i don't know what Nautilus is!

x-EDIT!

Never mind! I searched for nautilus in the file search and it came up with tons of results. Which one is the right one to open?

x-EDIT!

Alright, i have now opened up my file browser and found a folder called "tmp" and inside it there are some files. Some are folders and some are single files and documents. Should i delete EVERYTHING inside this tmp folder?

---

### Post by 4l13n666 on 2008-03-03
Alright, all TMP files are now deleted but i still dont know how to run the kiba dock.
Sorry for bugging you so much but i want this to work now that i'm halfway there! :)

x-EDIT!

Kiba doesn't load at all. I tried opening the kiba settings in the terminal using the following command: kiba-settings

The output of this command is as follows:

 erik@erik-laptop:~$ kiba-settings
bash: kiba-settings: command not found
erik@erik-laptop:~$ 

I also added the kiba-dock to the startup sessions but nothing happened.

x-EDIT!

And to top it all off, one more problem! The files i deleted from the TMP file come back every time i log on my system!

---

### Post by erginemr on 2008-03-03
Nautilus is your standard file manager.

Yes, go for it and delete what is inside the /tmp folder.

---

### Post by 4l13n666 on 2008-03-03
> **erginemr said:**
> Nautilus is your standard file manager.

Yes, go for it and delete what is inside the /tmp folder.

When i delete the files. The come back when i reboot or relog. In the same folder and exactly the same files.

---

### Post by erginemr on 2008-03-03
> **4l13n666 said:**
> ...

And to top it all off, one more problem! The files i deleted from the TMP file come back every time i log on my system!

No problem with that. What we do here is to delete the residual temporary files from a session, which has not been terminated normally and force it to reset itself. It is normal that temporary files will be created again by the running programs.

Unfortunately, this also is a "temporary" (note the pun ;)) workaround. It will come back once in a while. For a full fledged explanation of this problem, you may refer to:

[http://ubuntuforums.org/showthread.php?t=710934](http://ubuntuforums.org/showthread.php?t=710934)

---

### Post by 4l13n666 on 2008-03-03
> **erginemr said:**
> No problem with that. What we do here is to delete the residual temporary files from a session, which has not been terminated normally and force it to reset itself. It is normal that temporary files will be created again by the running programs.

Unfortunately, this also is a "temporary" (note the pun ;)) workaround. It will come back once in a while. For a full fledged explanation of this problem, you may refer to:

[http://ubuntuforums.org/showthread.php?t=710934](http://ubuntuforums.org/showthread.php?t=710934)

Even though the files are deleted, i can still not open kiba dock. There is no icon, no commands, only a file in my file handler saying kiba dock with a couple of files in. Kiba dock  nearly loaded the first time i rebooted the system, actually only the theme changed, but no dock.

---

### Post by erginemr on 2008-03-03
There is a wiki on their site:
[http://www.kiba-dock.org/](http://www.kiba-dock.org/)

which will presumably give some information on kiba-dock's usage.

O the other hand, I still recommend you to try AWN, which is a more down-to-earth Gnome dock IMHO.

---

### Post by 4l13n666 on 2008-03-03
> **erginemr said:**
> There is a wiki on their site:
[http://www.kiba-dock.org/](http://www.kiba-dock.org/)

which will presumably give some information on kiba-dock's usage.

O the other hand, I still recommend you to try AWN, which is a more down-to-earth Gnome dock IMHO.

Alright, you have a link to a working AWM code?

---

### Post by 4l13n666 on 2008-03-03
Alright nevermind. I got the AWM working properly. Sure would like to through  my icons around though :) Thanks for the help!

---

### Post by erginemr on 2008-03-03
OK. Great!

Granted *"De gustibus et coloribus non disputandum"* but I'd say, stay away from useless eyecandy which, besides, will have a negative impact on the performance of your hardware.

By the way, you can remove kiba-dock now and reclaim a lot of hard disk space if you want by uninstalling those dev libraries, because all those development you have installed while compiling kiba--dock are unnecessary now (unless you want to keep them in check).

---

