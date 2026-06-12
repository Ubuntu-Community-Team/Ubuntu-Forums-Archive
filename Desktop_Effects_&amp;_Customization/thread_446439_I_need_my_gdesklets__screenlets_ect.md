---
title: "I need my gdesklets / screenlets ect"
date: 2007-05-16
forum: Desktop Effects &amp; Customization
---

### Post by sefs on 2007-05-16
I have beryl installed, and everytime it starts up the gdesklets disappear.  I read these were incompatible with bery that i should use screenlets instead but same thing is happening.  When beryl starts i loose the desklets.

How can i set this up.

Thanks.

---

### Post by xarmian on 2007-05-17
If gdesklets is running when beryl starts, it makes gdesklets disappear.. you can bring it back by running the following command (Alt-F2 or open a shell window):

> 
gdesklets restart


The way I got around the issue when booting, is to make gdesklets start 5 seconds after beryl by doing this:

1. Create a file and place it in a location where you wont forget about it, but it's not in the way.. for example I placed mine in ~/.gnome2 and named it startgdesk.sh .. If you're not using gnome, then obviously this isn't the optimum location, but just pick a spot that works for you and adjust the commands accordingly.

gedit ~/.gnome2/startgdesk.sh

> 
#!/bin/bash
sleep 5
gdesklets


2. Change the permissions of the startgdesk.sh file to make it executable

> 
chmod 755 ~/.gnome2/startgdesk.sh


3. Make beryl start automatically with your computer by creating an autostart to execute "beryl-manager" in your System->Preferences->sessions->Startup

4. If you have an autostart to start gdesklets, edit it.  if you dont, create a new one ("New" in the same place as step 3) to execue the gdesklets start script.  Use for the command:

> 
~/.gnome2/startgdesk.sh


Now when you start your computer, beryl will start first, then a few seconds later gdesklets will start and your desklets will appear.. if you restart beryl, your gdesklets will disappear and you'll have to restart it using the command above..

One thing I haven't looked into is incorporating a "gdesklets restart" execution into the beryl-manager launcher.. which will automate this process a little more.

Hopefully this works for you.. Good luck.

-Dave

---

### Post by xarmian on 2007-05-17
just a side note.. your post prompted me to try out screenlets again, which has changed quite a bit since i last tried to use it.. it's absolutely amazing, and beats gdesklets into the ground.. and although I haven't tried it yet, there's a beryl plugin which will likely resolve most issues, if not i would think the method i mentioned in my previous post would work similarly

-Dave

---

### Post by Ateo on 2007-05-17
Superkaramba works perfect with beryl. But you need kdelibs.

---

### Post by Izobalax on 2007-05-17
Is it possible to use Superkaramba in GNOME?

/izo

---

### Post by sefs on 2007-05-17
I tried the sleep 5, sleep 7 and sleep 15, methods, but sometimes it works and sometimes it does not ... I realize though the the bigger X is in sleep x, the better chance i get of beryl starting.  Another thing is that now some of the gdesklets are loading with a taskbar in the window list.  and not as windowless gdesklets.  I even saw one some of them loading with actual windows borders complete with minimize buttons ect.

Is it just that gdesklets with beryl do not mix?

Thanks.

---

### Post by toasterofirony on 2007-05-17
> **Izobalax said:**
> Is it possible to use Superkaramba in GNOME?

/izo

Yes, but if my experience is anything to go by you will have problems (CPU usgage/ memory leaks). I'd stick to gDesklets of Screenlets if I were you.

---

### Post by Izobalax on 2007-05-17
> **toasterofirony said:**
> Yes, but if my experience is anything to go by you will have problems (CPU usgage/ memory leaks). I'd stick to gDesklets of Screenlets if I were you.

Hmmm.... interesting. I'll have to test Superkaramba tonight then. :grin:

My screenlets doesn't work anymore. I've started a thread about it in this forum, but no reply. :(

And gDesklets is Okaaay.... but a very limited amount of good-looking desklets, in my opinion. Let's face it, Superkaramba has a ***huge*** amount of widgets at one's disposal.

/izo

---

### Post by xarmian on 2007-05-17
I did have some problems where gdesklets showed up in the taskbar, but I never used it for much (maybe one or two desklets) and the ones I used didn't have that problem.. so i never looked too far into it..

I have screenlets working flawlessly now, using the widget layer plugin for beryl.. it is definitely a little buggy but once it's running right it seems to be stable..  I noticed you can't use the right-click "Window" option to adjust the settings, you have to right click, select preferences, and edit the settings there or they'll get messed up.  I have every widget set to "Stick to desktop, treat as a widget, keep above" and they accurately display no matter what side of the cube i'm on, and i can switch sides of the cube while looking at the widget layer.

Earlier I didn't have them set to "stick to desktop" and if I brought up the widget layer (dashboard-like view, from the beryl widget plugin) and I switched sides of the cube, and then i exited the widget layer, the screenlets disappeared completely and i had to restart screenletsd to get them back.

I haven't tried superkaramba yet, but I might..the number of widgets available is immense, but I'd rather not let the eye candy detract from functionality, and if it has a memory leak in gnome then it's probably not worth it for my use.  we will see.

-Dave

---

### Post by sefs on 2007-05-21
@xarmian

How do i get the screentlets to stop minimizing when i click on the show desktop button.  Only opened apps should minimize and not the screenlets, but my screenlets are being minimized also.. I want them to show always, like what gdesklets did.

---

### Post by xarmian on 2007-05-21
> **sefs said:**
> @xarmian

How do i get the screentlets to stop minimizing when i click on the show desktop button.  Only opened apps should minimize and not the screenlets, but my screenlets are being minimized also.. I want them to show always, like what gdesklets did.

Try right-clicking the screenlet, select "Properties" and make sure the following settings are as described:

Stick to desktop: checked
Treat as Widget: unchecked
Keep above: unchecked
Keep below: checked

This will make your screenlet display on all desktops, and when you "show desktop" the screenlet should stay on the desktop without minimizing or moving..  I tested this briefly with Feisty and Beryl and it seemed to work.

Remember, do not use the Right-click "Window" option to adjust these properties, it simply does not work.

-Dave

---

### Post by sefs on 2007-05-21
Thats not working for me... the most it does is to display the screenlets on all desktops of the rotating cube.

But as soon as i click the show desktop button the sreenlets get hidden until i reveal them again by toggling the show desktop button again.

Maybe there is a setting somewhere i am missing?

Maybe i need that beryl widget layer plugin?

---

### Post by sefs on 2007-05-21
Just adding a picture to show what i had checked from your instructions....

---

### Post by FurryNemesis on 2007-05-22
Widget layer plugin? Is that in the unsupported plugins in 0.2.0?

---

### Post by xarmian on 2007-05-22
I had a hard time finding it too.. Download and install the .deb from here (beryl-widget-plugin_0.1-2_i386.deb) for Feisty:

[http://syzygy42.tuxfamily.org/dists/feisty/all/](http://syzygy42.tuxfamily.org/dists/feisty/all/)

Then you'll be able to find the plugin under extras in Beryl.. enable it, and voila.

-Dave

---

### Post by Jalke on 2007-05-23
I tried the solution offered.  However, I can't seem to be able to run the .sh script file.  I think it has to do with the fact that the Startup Programs manager doesn't like running an .sh file with a double command in it (sleep + executing a program).  I'm fairly new to Linux so am not sure about this, but I recall someone posting this somewhere.  Previously I also tried to delay programs from starting up immediately using the sleep command.  However, this also failed. 

Any idea why and how to get around this??

Thanks,
Jalke

p.s. I thought the script was meant to use a semi-colon, that is: 

                                sleep 5; gdesklets  

Or is either way ok?

---

### Post by xarmian on 2007-05-23
> **Jalke said:**
> I tried the solution offered.  However, I can't seem to be able to run the .sh script file.  I think it has to do with the fact that the Startup Programs manager doesn't like running an .sh file with a double command in it (sleep + executing a program).  I'm fairly new to Linux so am not sure about this, but I recall someone posting this somewhere.  Previously I also tried to delay programs from starting up immediately using the sleep command.  However, this also failed. 

Any idea why and how to get around this??

Thanks,
Jalke

p.s. I thought the script was meant to use a semi-colon, that is: 

                                sleep 5; gdesklets  

Or is either way ok?

Either way would be ok, the semi-colon is equivalent to a new line in this case, they basically end the first command and execute a second command.. so:

sleep 5
gdesklets

is equivalent to:

sleep 5; gdesklets

If you're still having problems, try increasing the sleep amount (instead of 5, make it 10).. also, try running the gdesklets command from the command-line and see if that works normally after your computer started.. If it doesn't do anything, then the problem is somewhere else.  Also make sure you don't have gdesklets set to autostart somewhere else..

If you are using screenlets, then do not use the script work-around mentioned earlier.  Screenlets generally work well with beryl, but there's a bug that causes them to go off-screen when beryl restarts.. for a work-around see my other thread, here:

[http://ubuntuforums.org/showthread.php?t=447475](http://ubuntuforums.org/showthread.php?t=447475)

I've abandoned gdesklets for screenlets because screenlets are more advanced and look nicer.. they are very buggy though so use with caution..

-Dave

---

### Post by Jalke on 2007-05-23
Thanks for your response.  
I've increased the sleep time and tried to manually run it after the computer had started.  This worked.  However, it won't autostart after startup.  Any more ideas?

Jalke

---

### Post by xarmian on 2007-05-23
> **Jalke said:**
> Thanks for your response.  
I've increased the sleep time and tried to manually run it after the computer had started.  This worked.  However, it won't autostart after startup.  Any more ideas?

Jalke

Unfortunately I'm out, but if I think of something I'll let you know.

---

### Post by LastHylian on 2007-05-27
Surprisingly, I found if you set them to act as a widget and then un-check the widget box, they will stop disappearing when you click the show desktop button

---

### Post by havchr on 2008-01-01
this worked for me:

[http://forum.compiz-fusion.org/showpost.php?p=32134&postcount=6](http://forum.compiz-fusion.org/showpost.php?p=32134&postcount=6)

---

### Post by viciouslime on 2008-01-22
Adding "class=Screenlet" (note the capital S!) to the "Non minimisable windows" rule in the window rules plugin (installed by default) fixed the minimising problem for me :)

---

### Post by eldersoares on 2008-02-03
sorry for my ignorance.... 
how do i get to this place where i should add this line¡?¡?¡?
using gutsy
thanks

---

