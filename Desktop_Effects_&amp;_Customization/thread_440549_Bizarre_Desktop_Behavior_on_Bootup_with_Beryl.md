---
title: "Bizarre Desktop Behavior on Bootup with Beryl"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by flowingfire on 2007-05-11
Hi Everybody!  

I've newly switched over from Windows to Ubuntu and I love it-- especially Beryl.  Beryl is what sold me on Linux over Vista.  Unfortunately, my desktop displays VERY bizarre behavior during bootup.  I'd love some help correcting this situation if possible.

First, a number of my system tray icons will appear in the upper left corner of my KDE desktop, in the middle of nowhere.  There is no panel there, just a stray tray icon.  Icons such as the "Adept Update Manager" will show up and have a stretchable frame around it that when stretched reveals screen-garbage.  This has also happened with the wireless manager and the klipper icons.  Most of the time I can right click on the strangely mis-placed icons and close them.  No big deal.

But sometimes, perhaps, the klipper and the wireless manager and the adept updater will not only appear in the wrong place, but they'll want to have a permanent place on my open windows taskbar.  I can't get rid of them; I just have to reboot and hope they go away next time.

Also, Beryl can't seem to decide whether or not to actually use itself as the display manager on startup.  Randomly, it simply won't load itself and I'll have to right click the red gem icon in the tray and "select window manager" -- "beryl." 

I thought it couldn't get worse than that, but then I installed SuperKaramba.  SuperKaramba and Beryl choose to get along when they feel like it.  Once in a while, I'll boot and they'll both show up beautifully.  Most of the time, however, SuperKaramba loads... Then Beryl loads... Then SuperKarmamba disappears... Then Beryl crashes.  Nice.

Also, as for some strange reason Beryl Manager doesn't want to show up in the tray unless I put a symbolic link in the KDE autostart folder.  Okay... Sometimes I get one red gem icon on startup... And sometimes I get two!  Of course, this isn't a problem-- I just close the redundant one... But you can see how this gets obnoxious.  Is there a way I can get it to start up without randomly deciding to start two instances sometimes? 

My desktop experience, obviously, is far from seamless.  Please help me make it a beautiful and liquid experience I can enjoy and be proud of my Ubuntu friends!  Help! (Even if you can't help me with the whole sordid slew of problems, if you could perhaps help me fix one of them I would really appreciate it... These might be separate issues or one in the same.  I don't know.)

Further information: 
Installed Ubuntu Version: Kubuntu, Feisty 7.04
Computer: HP Pavilion m7560n 
Ram: 2 gigs
Video Card: NVidia GeForce 6100 LE
Processor: AMD Athlon 4400+
Display driver installed: nvidia-glx-new (proprietary option selected)
Resolution: 1280x1024
Monitor: NEC MultiSync 90 GX2

If any other information is needed, please ask. :)  

Pleasant tidings,
-David

---

### Post by sowelie on 2007-05-11
Wow, sounds like you've got a lot going on here.  Lets start with the first issue of beryl manager not starting at times or crashing.  This may also solve some of your issues with the startup.  First of all disable beryl on startup.  Then, launch it from the console and watch the output.  Load up SuperKaramba and see if you can get beryl to crash so you can see the output and start to diagnose the problem.  I think your random icon placement has a lot to do with this.  I had a similar issue in Gnome a while back and my solution was to reload beryl and the icons would magically place themselves correctly.  I think once you get it to start properly the icon issue may go away.

---

### Post by flowingfire on 2007-05-12
Hi!  I'm in KDE, so I decided to remove Beryl from the KDE autostart folder and log into gnome to activate its startup counterpart.  I think this has solved the redundant beryl-starting problem... But it hasn't solved the tray-icons-appearing-where-they're-not-supposed-to problem...  

As far as SuperKaramba goes, I've kinda given up on it at the moment and don't even load it.  I think I might try viewing the output like you suggested, though-- it might provide some valuable clues.  Either way, Beryl still causes it's own strange problems, though-- like the orphan tray icons.... Boy that's annoying!

Anyway, thanks.... I'll keep working at this and keep Ubuntuites updated if I get anything actually fixed.

-David

---

