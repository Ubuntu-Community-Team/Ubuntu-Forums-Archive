---
title: "notification balloons location - how to change?"
date: 2009-04-24
forum: Desktop Environments
---

### Post by timcredible on 2009-04-24
i installed 9.04 jaunty today, and i removed the bottom panel and moved the top panel to the bottom, but the notification balloons for things like wireless connections still show up on the top right of the screen.  is there a way to change that to the bottom right?  thanks.

---

### Post by timcredible on 2009-04-29
bump.

---

### Post by [SomeGuy] on 2009-04-29
Can you send a screenshot? I don't understand exactly what you mean.

---

### Post by LIB53 on 2009-04-29
He's talking about this notification bubble i think: [http://www.markshuttleworth.com/archives/265](http://www.markshuttleworth.com/archives/265)

---

### Post by timcredible on 2009-04-29
yes, exactly.  it's really nice, but i tend to move the top panel to the bottom, and i was wondering if i could move the notification bubble also.

---

### Post by LIB53 on 2009-04-29
I've been wanting to know the same thing. I've trying to find some configurations, but going through all these folders is a pain. I even searched "notifications" but i get a bunch of random stuff. I hope someone knows a bit more about this. :(

---

### Post by pw_f100_220 on 2009-04-29
Ditto.  I also would like to be able to choose which monitor it shows on.  I generally keep pidgin at the bottom left of the left screen and to see those notifications at the top right of the right screen just surprises me every time.  I really like the look of the new bubble though.

Ability to change it in Fluxbox would be good, too.

---

### Post by cariboo on 2009-04-29
Where the notification bubbles show up is hard coded, and can't be changed. Have a look [here]("http://glyph.twistedmatrix.com/2009/04/notification-disappointment-in-ubuntu.html") points 4 and 5.

---

### Post by NTolerance on 2009-05-02
Hopefully something can be done to change this behavior.  The standard two-panel layout does not work well for low resolution screens such as the 1280x800 one on my laptop.  To gain more vertical space I set the top panel to auto-hide, and a notification area on a hidden panel is pointless, so I move the notification area to the bottom, but the Jaunty notification pop-ups continue up top, which is a bit illogical.  They should follow the position of the notification area in the panel.

---

### Post by JoelJohnson on 2009-05-05
Really disappointing to me... one of the biggest points linux fans are constantly making is how "customisable" linux is. "You can change anything" they always say. And here they are hard-coding something like that.

Of course it's not going to be pushing me away from Ubuntu. I am disappointed, however. I love the new system, I just don't ever see the notifications in the top-left like that.

---

### Post by kpkeerthi on 2009-05-05
If you are unhappy with the new notification system, you can revert to the default:
```
sudo apt-get purge notify-osd
```
```
sudo apt-get install notification-daemon
```
**Reboot.**

---

### Post by cvaty on 2009-05-05
menu > prefrences > pop-up notifications
and you should find the positioning there

or in the terminal
```

notification-properties

```

---

### Post by NTolerance on 2009-05-05
> **cvaty said:**
> menu > prefrences > pop-up notifications
and you should find the positioning there

or in the terminal
```

notification-properties

```

Neither of these applications are available in Jaunty final.  Are you possibly referring to apps that existed in Intrepid or one of the Jaunty beta releases?

---

### Post by mjbennison on 2009-05-05
> **NTolerance said:**
> Neither of these applications are available in Jaunty final.  Are you possibly referring to apps that existed in Intrepid or one of the Jaunty beta releases?
If I type sudo notification-properties at a command prompt I get a dialogue box and I can change the positioning of the test dialogues. Note you must do sudo or nothing happens - 
this is on Jaunty final. However... it doesn't change the position of the balloons away from the top right regardless of the settings! 

I will restart X and see if that makes a difference - no.

I came across this post when looking for a solution to having balloons AND a popup window for my mail notifier. Still looking for a solution for that.

---

### Post by cb951303 on 2009-05-17
I have the same problem and I don't have the "notification properties" menu entry either.

If the notification bubble position is hard-coded I'm going to lose respect for ubuntu developers. That would be the single most stupid design choice ever. In fact If I were the coder I would be ashamed to release it as stable before fixing this issue.

EDIT: It looks like "notification-properties" has nothing to do with new notification system. as far as I see it's for the old one.

---

### Post by NTolerance on 2009-05-18
Here's another potential issue with the new notification system.  Yesterday I was watching a fullscreen video on Hulu.  I needed to increase my system volume, so I used the multimedia volume key on my laptop to do so.  The volume notification pop-up seemed to steal focus from the fullscreen video and caused it to exit from fullscreen mode.  Has anyone else had a similar problem?

---

### Post by employeeno5 on 2009-05-18
> Here's another potential issue with the new notification system. Yesterday I was watching a fullscreen video on Hulu. I needed to increase my system volume, so I used the multimedia volume key on my laptop to do so. The volume notification pop-up seemed to steal focus from the fullscreen video and caused it to exit from fullscreen mode. Has anyone else had a similar problem?

I've had this problem, but only when using Compiz. If I turn off Compiz when using fullscreen video this is no longer an issue. I've gotten into the habit of turning off Compiz if I'm watching fullscreen flash video television-style anyways, due to the fact that it seems to perform better. I use the fusion-icon as a fast and easy way to switch between WMs.

---

### Post by gradinaruvasile on 2009-07-22
U can revert to the older style notification by (commands in terminal):

1. Install the notification-daemon package:

```
sudo apt-get install notification-daemon
```

2. Rename the /usr/lib/notify-osd/notify-osd executable

```
sudo mv /usr/lib/notify-osd/notify-osd /usr/lib/notify-osd/notify-osd-original
```

3. Create a symbolic link:

```
sudo ln -s /usr/lib/notification-daemon/notification-daemon /usr/lib/notify-osd/notify-osd
```

4. Kill the original notification:

```
sudo killall notify-osd
```

5. Launch the new notification - press alt+F2, type /usr/lib/notify-osd/notify-osd

6. Test:

```
notify-send test test
```

With this older notification type u can use the notification-ptoperties tool to set the location of the notification pop ups

---

### Post by Amenotep on 2009-11-08
> **JoelJohnson said:**
> Really disappointing to me... one of the biggest points linux fans are constantly making is how "customisable" linux is. "You can change anything" they always say. And here they are hard-coding something like that.

Of course it's not going to be pushing me away from Ubuntu. I am disappointed, however. I love the new system, I just don't ever see the notifications in the top-left like that.

You can still delete the notification program and install a new one. That's customization to me...;)

---

### Post by cyberkilla on 2009-11-08
> **Amenotep said:**
> You can still delete the notification program and install a new one. That's customization to me...;)

That's a thin excuse, isn't it? It really can't be that hard for them to add a gconf setting, at the very least:p

I wouldn't mind it being in the bottom-right, where nothing else is happening on my desktop.

---

### Post by Romanmir on 2009-11-10
Agreed. Here, here.

<rant>+1 for the idea of a gconf setting for every package option that canonical removes from the primary ui of any program "in order to not confuse the user."</rant>


Oh, and a gconf listing for things like this that would allow us tweak these things.

---

### Post by commonplace on 2009-11-29
So there's still no way to do this, even in Karmic? Ugh. LOTS of people move to a single panel at the bottom (with none at the top), and it would make perfect sense to have the notificiations follow the notification area. Boo.

/Kevin

---

### Post by cb951303 on 2009-11-30
another brain damage of the new notification system (which is also still crippled in karmic) is that it doesn't stack up notifications. if there are 2 notification at the same time, you need to wait for the first one to disappear to see the second. Pure brain damage...

---

### Post by ericwait on 2010-01-05
Does anyone know if this was fixed in 9.10 or in 9.04?  I have two monitors with the left one being my primary, I sometimes turn off the right monitor.  When I have the right monitor off, I don't see the notifications (current song, gwibber new tweet, etc.)

Thanks

---

### Post by jazzgossen on 2010-01-07
I'm running Karmic, and I haven't seen a solution to this either, short of reverting to the old notification system. (The notification-properties mentioned earlier in the thread is indeed for the old notification system.)

---

### Post by gradinaruvasile on 2010-01-07
I think notification-daemon is the official Gnome notification system. Notify-osd is a new thing, i think it was deployed only in Ubuntu so far.
And there is some discussion about notify-osd:

[http://macslow.net/?p=381](http://macslow.net/?p=381)

---

### Post by jazzgossen on 2010-01-07
From the developer's site: "There&#8217;s not going to be a configuration UI for notify-osd. We rather want the defaults to be rock solid." 

Whaat?? I guess it's time to fork notify-osd, then.

---

### Post by airtonix on 2010-01-07
> **jazzgossen said:**
> From the developer's site: "There’s not going to be a configuration UI for notify-osd. We rather want the defaults to be rock solid." 

Whaat?? I guess it's time to fork notify-osd, then.

gogogo! waiting for your forking fork of this forked thing.

---

### Post by killdashnine on 2010-01-16
> **gradinaruvasile said:**
> U can revert to the older style notification by (commands in terminal):

1. Install the notification-daemon package:

```
sudo apt-get install notification-daemon
```

2. Rename the /usr/lib/notify-osd/notify-osd executable

```
sudo mv /usr/lib/notify-osd/notify-osd /usr/lib/notify-osd/notify-osd-original
```

3. Create a symbolic link:

```
sudo ln -s /usr/lib/notification-daemon/notification-daemon /usr/lib/notify-osd/notify-osd
```

4. Kill the original notification:

```
sudo killall notify-osd
```

5. Launch the new notification - press alt+F2, type /usr/lib/notify-osd/notify-osd

6. Test:

```
notify-send test test
```

With this older notification type u can use the notification-ptoperties tool to set the location of the notification pop ups

THANK YOU!  The lack of configuration for the new notification system has been so very frustrating for so long.  With an 11.6" netbook, it took up a good chunk of the screen, and there was no way to prematurely close a notification.  Furthermore, if I moved the mouse over a notification bubble it would seem to reset the amount of time it would display for.  This is the first time I have been truly disappointed with the laziness in the development of an "upgraded" feature. Thats enough ranting; thank you very much gradinaruvasile!

---

### Post by FooAtari on 2010-01-24
> **gradinaruvasile said:**
> U can revert to the older style notification by (commands in terminal)...

Thanks. The new notifications were driving me nuts. Really bad decision to not allow any customization options

---

### Post by raker1000 on 2010-01-28
> **gradinaruvasile said:**
> U can revert to the older style notification by (commands in terminal):

1. Install the notification-daemon package:

```
sudo apt-get install notification-daemon
```2. Rename the /usr/lib/notify-osd/notify-osd executable

```
sudo mv /usr/lib/notify-osd/notify-osd /usr/lib/notify-osd/notify-osd-original
```3. Create a symbolic link:

```
sudo ln -s /usr/lib/notification-daemon/notification-daemon /usr/lib/notify-osd/notify-osd
```4. Kill the original notification:

```
sudo killall notify-osd
```5. Launch the new notification - press alt+F2, type /usr/lib/notify-osd/notify-osd

6. Test:

```
notify-send test test
```With this older notification type u can use the notification-ptoperties tool to set the location of the notification pop ups


Thank you thank you thank you!

This worked perfectly for me on Karmic. The main problem I have with the notify-osd is watching recordings in mythtv. I have a wide screen 16:9 monitor running 1280x720 and the videos are playing in 4:3, with black bars on the side margins. Well, every time I tried to change the system volume with the built in volume controls on the keyboard, the notify osd would place half of the bubble outside the borders of the video in the margin, and then a few seconds later, the bubble would disappear, leaving half of it sitting in the margin. This remnant of the volume osd would then sit there until i left the full screen video mode. Of course, I could use the mythtv internal volume controls, but they havent worked right since I install .22, and that's a whole other story.

Now when I installed the notification-daemon, it places the volume bubble bottom center, where it disappears as soon as it times out.

---

### Post by auh2o on 2010-02-01
I agree that not being able to change the position of the notifications to each user's liking is stupid, and I too will follow the instruction above and revert back to the standard Gnome notification daemon if it is indeed not possible with NotifyOSD.

But look here in the design specification for NotifyOSD, it talks about three possible different positions, one being the bottom right corner - and "a gconf key determining which of three  positioning schemes are used". 

[https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble](https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble)

So, might it be possible to edit gconf after all, or am I missing something here?

---

### Post by auh2o on 2010-02-09
**^ttt^**

---

### Post by TommyMac501 on 2010-02-09
> **gradinaruvasile said:**
> U can revert to the older style notification by (commands in terminal):

1. Install the notification-daemon package:

```
sudo apt-get install notification-daemon
```

2. Rename the /usr/lib/notify-osd/notify-osd executable

```
sudo mv /usr/lib/notify-osd/notify-osd /usr/lib/notify-osd/notify-osd-original
```

3. Create a symbolic link:

```
sudo ln -s /usr/lib/notification-daemon/notification-daemon /usr/lib/notify-osd/notify-osd
```

4. Kill the original notification:

```
sudo killall notify-osd
```

5. Launch the new notification - press alt+F2, type /usr/lib/notify-osd/notify-osd

6. Test:

```
notify-send test test
```

With this older notification type u can use the notification-ptoperties tool to set the location of the notification pop ups

Works perfect, now, how to get the standard notification balloon to respect the theme colors?..  :)

---

### Post by auh2o on 2010-03-06
Yes, that solution works, **but it is not necessary**. There IS a way to change the position of notify-osd to your liking, with a patch. Check out this thread:

[http://ubuntuforums.org/showthread.php?p=8820555](http://ubuntuforums.org/showthread.php?p=8820555)

The only question is HOW. The patch in that thread will simply move the notify balloon to the top screen edge, but it is obviously possible to edit it as you see fit. But I would need the help of someone much more experienced to do this!

But bottom line people - don't revert back to the old notification daemon. It IS possible to change the position of the new one.

If anybody could tell us how to get it to the bottom right corner (but rather with the same amount of distance to the screen edges as the original location, than *right* at the edges), please post either here or in that other thread.

---

### Post by nechus on 2010-03-20
Thanks, [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640")! It worked perfectly in Lucid Beta 1, too.

Can anyone tell me how I move these "old-fashioned" notifications to the top left corner of the screen now?

Thank you.

---

### Post by djstava on 2010-03-25
notify-osd position:
  
  1)GRAVITY_NONE: the behaviour in Jaunty. A notification will always go into the top right corner. 
  2)GRAVITY_EAST: the behaviour NotifyOsd has been having for about a week in Karmic's development cycle, with the notifications centered vertically on the screen. 
  3)GRAVITY_NORTH_EAST: the Karmic behaviour. Works like GRAVITY_NONE but does not put asynchronous notifications on top of the screen, even if there is no synchronous notification being displayed.

I wonder how to trigger the notification showing by application ?For example,Network connected or unconnected?

Any body knows?

djstava

---

### Post by cojoco on 2010-10-17
Thanks for the tips.

I have reverted back to the old notify because the top right of my X display is on my *television*, which is not likely to be turned on.

It seems like there are any number of sensible reasons to want to change the position of the notifican area.  Forcing people to do ridiculously non-standard things to change simple configuration parameters is going to result in a lot of unhappy people, either because they can't reconfigure, or because the extreme steps they have to take to change the configuration will break something down the line.

---

### Post by Megaptera on 2010-10-17
Nifty GUI app to move OSD and change size etc in Lucid:

[http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)

---

### Post by vapor0 on 2010-10-24
That's awesome.

It's about time! I've hated this for years!

---

### Post by Krytarik on 2010-11-14
After I finally found the command to REALLY change the position of the notification bubble (it is in one of the comments below the article, who minds?), I spent the last night to write a python script for a simple GUI, in case you want/have to change the position more often (like me).

I have attached the respective files to install it in the usual way.


PS: I just want to share it because I really spent a couple of hours for writing this, it's my first mainly self-made script for a GUI, and I want to give anyone else the benefit of it, so that the time is spent not solely for myself.;) I hope you enjoy it!

UPDATE: Complete and up-to-date guide here:
[http://ubuntu4beginners.blogspot.com/2011/06/tweaking-notify-osd.html](http://ubuntu4beginners.blogspot.com/2011/06/tweaking-notify-osd.html)

---

### Post by xqz on 2010-12-23
Thank you so much.. I was looking everywhere with nothing working. Yours worked the best and easiest

---

### Post by ma65p on 2011-01-02
Super annoying after a while because the pop up has a large gap away from my menu bar. 

Also, clicking on the notification does nothing. I was expecting it to launch the associate app like growl or at least just go away. Well. fail. I will just turn off all notifications from now on.

Also try pidgin, it will notify you to death. 

Anyhow. Ubuntu is still fun to have though.

---

### Post by Krytarik on 2011-01-03
> **ma65p said:**
> 
Also try pidgin, it will notify you to death. 

Depends on the configuration.

Greetings

---

### Post by TyLLy_4 on 2011-05-24
> **JoelJohnson said:**
> Really disappointing to me... one of the biggest points linux fans are constantly making is how "customisable" linux is. "You can change anything" they always say. And here they are hard-coding something like that.

Of course it's not going to be pushing me away from Ubuntu. I am disappointed, however. I love the new system, I just don't ever see the notifications in the top-left like that.

Ohh boy! you'r going to be disappointed when you try out gnome 3 XD

---

### Post by martinr on 2011-06-03
> **cojoco said:**
> 
It seems like there are any number of sensible reasons to want to change the position of the notifican area.  Forcing people to do ridiculously non-standard things to change simple configuration parameters is going to result in a lot of unhappy people, either because they can't reconfigure, or because the extreme steps they have to take to change the configuration will break something down the line.

bump +1
I have the same problem in 10.04 LTS (Lucid). 
The issue irritates me enormously. 
Is anybody working on this?
Has a bug report been created already?

---

### Post by Frogs Hair on 2011-06-03
> **martinr said:**
> bump +1
I have the same problem in 10.04 LTS (Lucid). 
The issue irritates me enormously. 
Is anybody working on this?
Has a big report been created already?

See post #41 on this thread.

---

### Post by martinr on 2011-06-03
> **Frogs Hair said:**
> See post #41 on this thread.
I saw that already, but I'd rather have it supported, than playing the find the broken non standard bug fix game, down the line. If the maintainer fixes it once and for all, it will prevent annoying a lot of people with non standard fiddling around.

---

### Post by gresavage on 2011-06-04
> **martinr said:**
> bump +1
I have the same problem in 10.04 LTS (Lucid). 
The issue irritates me enormously. 
Is anybody working on this?
Has a bug report been created already?


Read this: [https://wiki.ubuntu.com/NotifyOSD]("https://wiki.ubuntu.com/NotifyOSD#Work for Lucid")

apparently this implies that there will be some customizability options soon. I don't know how many releases before they develop a full preferences editor but the outlook is hopeful.

This customizability would be greatly beneficial especially to those who have issues with the notifications appearing off screen or with theme conflicts (poor contrast quality etc.)

It seems as though the potential applications of libnotify are too great to ignore forever; especially if public outcry continues.

Ubuntu is generally good at fixing issues before a large portion of the general population ever even has to deal with them. I therefore have no doubt that in a few distros we may see a preferences editor for notify-osd especially since they are already at least in the brainstorming stage thereof. 

Until then you will have to make due!

---

### Post by Krytarik on 2011-06-04
> **gresavage said:**
> Read this: [https://wiki.ubuntu.com/NotifyOSD]("https://wiki.ubuntu.com/NotifyOSD#Work%20for%20Lucid")

apparently this implies that there will be some customizability options soon.
So, what exactly in that page made you conclude this?

I mean, we may hope that there is an ongoing development process, and we may hope that this will lead to more customizability options and a preferences GUI that is included by default, but I can't draw any specifics from that page.

Greetings.

---

### Post by gresavage on 2011-06-04
> **Krytarik said:**
> So, what exactly in that page made you conclude this?

I mean, we may hope that there is an ongoing development process, and we may hope that this will lead to more customizability options and a preferences GUI that is included by default, but I can't draw any specifics from that page.

Greetings.

well they discussed tweaks to be implemented in the link i provided. And further discussed specific gconf customizability with specific pertinence to positioning here:

[https://wiki.ubuntu.com/NotifyOSD]("https://wiki.ubuntu.com/NotifyOSD#position")

obviously these features have not yet been implemented but they are at least discussing/thinking about it

of course i may be misinterpreting the meaning of the article

---

### Post by Krytarik on 2011-06-05
> **gresavage said:**
> well they discussed tweaks to be implemented in the link i provided. And further discussed specific gconf customizability with specific pertinence to positioning here:

[https://wiki.ubuntu.com/NotifyOSD]("https://wiki.ubuntu.com/NotifyOSD#position")

obviously these features have not yet been implemented but they are at least discussing/thinking about it

of course i may be misinterpreting the meaning of the article
Well, I've visited that page a couple of times since installing Lucid 10.04 in October of last year, and I'm quite sure that those part hasn't been changed since.

---

### Post by MestreLion on 2012-06-15
> **gresavage said:**
> obviously these features have not yet been implemented but they are at least discussing/thinking about it

A workaround was implemented for this: there is a setting at dconf that changes the notify-osd behavior.

Look here for the steps:

[http://askubuntu.com/a/151542/11015](http://askubuntu.com/a/151542/11015)

---

### Post by overdrank on 2012-06-15
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

