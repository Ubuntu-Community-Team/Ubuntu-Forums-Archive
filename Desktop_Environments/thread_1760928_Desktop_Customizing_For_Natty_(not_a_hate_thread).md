---
title: "Desktop Customizing For Natty? (not a hate thread)"
date: 2011-05-17
forum: Desktop Environments
---

### Post by GroogFish on 2011-05-17
First off I got to say that Natty is pretty interesting. I really like the space-saving techniques with the omni-bar, vertical app panel, and very fast omni search (similar to windows 7 but much faster). It will take getting used to but I think in the end it will eventually make working much easier and quicker.

It is in beta so I won't get ahead of myself and make assumptions but it seems like Ubuntu has sacrificed a lot of customizability with this release. A few things I've notice that maybe I can get some clarification on-

1. I cannot add panels or items to panels.
I would like to add the system-monitoring tools to my top panel so I can see when my CPU and RAM spikes.

In addition, pidgin no longer appears in my tasks bar. I'm guessing this is a bug? (I prefer it over Empathy. Rather not switch).

2. I cannot find a feature that leaves my vertical app bar visible all the time. When I make an application go full screen it pushes it out of the way. This is a bit annoying when I'm trying to find a file, folder, or application quickly.

Also when I open a file that I didn't mean to open I would like to see it popup in my app bar so I know instantly where to find it and close it. With this I will have to search for it.

Of course this all takes only a few extra seconds but it's just an annoyance.

3. I cannot change the size of my apps in the app bar and it doesn't automatically resize. This might not be a big issue for some but I use my Linux OS solely for work. As a developer I often have upwards of 20 files open and it usually fills my screen when using my avant window navigator. This is significant since I have a wide and short monitor.

4. I am unable to change the orientation of the app bar. This goes back to the fact that I have a wide and short monitor. Because of this it may seem better to fill up space vertically by adding a vertical app bar, but I have so many apps and usually work in text-documents that it would be better for me to have a horizontal app bar.

5. Unable to remove unneeded buttons. My app bar is going to fill up very fast. I do not need a workspace switcher, a home folder, the applications button, or the trash visible in this app bar. I will use these rarely and I would rather make room for apps I use often.

6. Apps at the bottom of the app bar does not adjust context menu accordingly.

[IMG]http://img691.imageshack.us/img691/2929/screenshotwgv.png[/IMG]

However I do like how Ubuntu is finally clipping unseen areas. I am using dual monitors and the one you are looking at is the short one. So when i take a screenshot I can see black area below. In previous versions I would be able to see the overflow. Does this also mean we are finally double image buffering as well? :)

7. I am unable to change desktop effects. I don't need a massive fancy shadow on every window. I prefer speed over desktop effects (but use Ubuntu for non-free software support).

8. I cannot move the Files & Folder button to the top. I would have use for this context menu since there is no longer a places button in the top panel. But I would rather have it at the top so I can access it easier.

9. Cannot clear recent file's history. As a developer I've worked on a couple adult entertainment related sites. I like to keep these hidden from my little ones for obvious reasons but now it seems there is no way to remove them from recent file history. There should be a context menu for this.

If there are already answers to these that's great. If not hopefully an Ubuntu developer will take not of them. Mostly little things but I don't think Ubuntu will be going back to the previous setup so they might as well work on such changes.

Thanks for reading!

---

### Post by Calash on 2011-05-17
Some possible work around for the current state of Unity:

1 - If you run Pidgin it shows up under the Mail indicator at the top right of the screen.  It will also notify you by changing this icon blue (default theme).  Empathy just does not work for our OCS setup at work so I have to use Pidgin.

For the others you can get some control by installing compiz-settings-manager and/or holding Alt+F2 and typing about:config in the run line.

The launcher (dock bar) is very gesture based by default.  If you need it quickly move your mouse to the top left of the screen fast and it will show up right away.  This can all be adjusted in the previously mentioned settings areas.

In all you have some good points for improvement.  I believe there is a better channel to submit they to the developers...it may be Launchpad but I am not sure and would not want to point you in the wrong direction.

---

### Post by coffeecat on 2011-05-17
Hi, I can't answer every one of your points, but here goes for what I can:

> **GroogFish said:**
> It is in beta

No, it isn't. Natty has been released; it is no longer in beta. However, this is the first proper iteration of Unity (Maverick's Unity doesn't really count), so we may reasonably expect to see more Unity features and customisations in future Ubuntu releases. 

> **GroogFish said:**
> 1. I cannot add panels or items to panels.

No, you can't. Unity's panels are not gnome panels, so gnome panel apps are not compatible. But no doubt some people are working hard to develop panel apps for Unity's panel. Watch this space! :)

> **GroogFish said:**
> 2. I cannot find a feature that leaves my vertical app bar visible all the time. When I make an application go full screen it pushes it out of the way. This is a bit annoying when I'm trying to find a file, folder, or application quickly.

Fortunately, easily fixed. Install compizconfig-settings-manager and look for Unity Plugin in the desktop section. There are four options under "Hide Launcher".

> **GroogFish said:**
> 3. I cannot change the size of my apps in the app bar and it doesn't automatically resize. This might not be a big issue for some but I use my Linux OS solely for work. As a developer I often have upwards of 20 files open and it usually fills my screen when using my avant window navigator. This is significant since I have a wide and short monitor.

Ditto, look in Unity Plugin in ccsm - experimental tab. You can change the launcher size there. I find a size of about 34 more comfortable than the default.

> **GroogFish said:**
> 4. I am unable to change the orientation of the app bar. This goes back to the fact that I have a wide and short monitor. Because of this it may seem better to fill up space vertically by adding a vertical app bar, but I have so many apps and usually work in text-documents that it would be better for me to have a horizontal app bar.

No you can't; not yet. So many people want this that I'll be surprised if this is not a feature that will be added in 11.10.

> **GroogFish said:**
>  5. Unable to remove unneeded buttons. My app bar is going to fill up very fast. I do not need a workspace switcher, a home folder, the applications button, or the trash visible in this app bar. I will use these rarely and I would rather make room for apps I use often.

You can't remove the applications, files and folders and trash icons, but you can remove the home folder one. Right-click and untick "Keep in Launcher".
> **GroogFish said:**
> 7. I am unable to change desktop effects. I don't need a massive fancy shadow on every window. I prefer speed over desktop effects (but use Ubuntu for non-free software support).

You can with ccsm, but take care. You might want to avoid trying to enable the desktop cube until you've read this link. :-s

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

> **GroogFish said:**
> 9. Cannot clear recent file's history. As a developer I've worked on a couple adult entertainment related sites. I like to keep these hidden from my little ones for obvious reasons but now it seems there is no way to remove them from recent file history. There should be a context menu for this.

Workaround:

[http://ubuntu4beginners.blogspot.com/2011/05/clear-history-in-files-folder-zeitgeist.html](http://ubuntu4beginners.blogspot.com/2011/05/clear-history-in-files-folder-zeitgeist.html)

A couple more links for you:

[http://omgubuntu.co.uk/natty/](http://omgubuntu.co.uk/natty/)

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

Good luck!

---

### Post by coffeecat on 2011-05-20
> **coffeecat said:**
> You can't remove the applications, files and folders and trash icons, 

The OP doesn't seem to have come back since starting this thread, but someone's just let me know that there is a workaround for this point, at least the applications and files/folders icons, here:

[http://ubuntu4beginners.blogspot.com/2011/05/hide-applications-andor-files-folders.html](http://ubuntu4beginners.blogspot.com/2011/05/hide-applications-andor-files-folders.html)

---

### Post by candtalan on 2011-05-29
> **GroogFish said:**
>  2. I cannot find a feature that leaves my vertical app bar visible all the time. When I make an application go full screen it pushes it out of the way. This is a bit annoying when I'm trying to find a file, folder, or application quickly.

[http://ubuntuguide.net/how-to-change-unity-sidebar-launcher-auto-hide-behaviour-in-ubuntu-11-04](http://ubuntuguide.net/how-to-change-unity-sidebar-launcher-auto-hide-behaviour-in-ubuntu-11-04)

---

### Post by wildmanne39 on 2011-05-29
> **candtalan said:**
> [http://ubuntuguide.net/how-to-change-unity-sidebar-launcher-auto-hide-behaviour-in-ubuntu-11-04](http://ubuntuguide.net/how-to-change-unity-sidebar-launcher-auto-hide-behaviour-in-ubuntu-11-04)
Hi, you can use the super button and it will bring up the launcher with number on them then just hit the number you want and it will open,also you can change the way the launcher works in ccsm.

---

### Post by AlbaKirkee on 2011-05-29
Greetings:  Someone may have already posted this remark, but for emphasis I would like to reiterate the need for a future version of Ubuntu Natty to allow the user to move the application sidebar to the bottom of the screen.

Most users have widescreen monitors, so naturally there will be more real estate to work with if the sidebar could be repositioned to the bottom of the screen.  

Maybe someone with influence with the cognoscente at Ubuntu can get them to fix this problem.

Thanks.....

Bob
[B]
[/B]

---

### Post by jerrrys on 2011-05-29
seems to be a lot of customizing going on.  i smell a mega-thread 

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Desktop+Customizing+For+Natty&as_qdr=all&sa=Google+Search&lang=en#936](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Desktop+Customizing+For+Natty&as_qdr=all&sa=Google+Search&lang=en#936)

---

### Post by grahammechanical on 2011-05-30
Hi albakirkee

Regarding this comment

> Most users have widescreen monitors, so naturally there will be more  real estate to work with if the sidebar could be repositioned to the  bottom of the screen.  

That does not make sense. Perhaps you meant 

> Most users **do not** have widescreen monitors

I have a widescreen monitor and the launcher fits fine but I try to imagine how it would look on my last monitor which had a portrait orientation and yes, in this case I agree that the launcher should be movable.

Regards.

---

### Post by Frogs Hair on 2011-05-30
See this thread for a CPU / Ram monitor for the panel . I have not had any problems with resizing applications , maybe I'm not understanding correctly.

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

To keep the panel visible at all times open the CCSM if installed . Select the  Unity plug-in and under autohide choose never.

---

### Post by AlbaKirkee on 2011-06-07
After using Natty for several days now, I've decided I like the side-panel just as it is.... As a part-time Windows user, I was accustomed to having the panel at the bottom of the screen, but I've adapted.   Thanks.....

---

