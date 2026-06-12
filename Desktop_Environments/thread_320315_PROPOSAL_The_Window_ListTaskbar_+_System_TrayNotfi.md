---
title: "PROPOSAL: The Window List/Taskbar + System Tray/Notfication Area HYBRID"
date: 2006-12-17
forum: Desktop Environments
---

### Post by robin.com.au on 2006-12-17
> **NOTE**
I constantly change this post, so come check back every now and then.


**WINDOW LIST/TASKBAR + SYSTEM TRAY/NOTIFICATION AREA + PROGRAM LAUNCHER**
Problem I have with them:

1. You look at the Window List, you can't do anything to it. Everything just opens from left to right.

2. You have **an** icon here which represents 'opening' GAIM (program launcher)
then **another** icon there representing that GAIM is 'opened' (window list)
then **yet another** icon over there which shows the 'status' of GAIM (system tray)

Can you see the 'visual' redundancy? Maybe theres an applet to merge these 3? OSX Dock programs like kxdocker looks good but not very usable at this stage, and is mac-ish. We want something 'exclusive' to Linux.

**IDEAS/PROPOSAL**
Lets use 3 opened Firefox windows as an example.

For a start, make each task button in the window list rearrangeable by dragging.
Have 1 icon next to the Firefox button which can act as a system tray or a launcher.

In the Window List, there will be 1 Firefox button with 3 segments, each segment representing each window. When you drag the button, you drag all 3 segments and the systray icon with it . This is for people who do not like the current way of grouping windows, where you click on the taskbar and a menu comes up.

Picture speaks louder than words.
Here is what it might look like:
[http://www.robin.com.au/image/mywinlist.png]("http://www.robin.com.au/image/mywinlist.png")
[http://www.robin.com.au/image/mywinlistb.png]("http://www.robin.com.au/image/mywinlistb.png")

Animation speaks even louder than pictures.
[http://users.tpg.com.au/adsltimu/task-system-launcher.html]("http://users.tpg.com.au/adsltimu/task-system-launcher.html") (Flash 7+ required)
----------------------------------------------------
**[COLOR="#ff0000"]NEW![/COLOR]**
**07-01-07**
I've been discussing this in the XFCE mailing with the maintainers and many people liked it. But there are people who like the tasklist+systray but minus the launcher, others who like the tasklist+launcher but minus the systray, people like me who like all 3 together, and those who just like the grouping, drag&drop idea of the tasklist only. 

So I decided that in 'preferences' you are able to '**Enable/Disable System Tray integration**' and '**Enable/Disable Launcher integration**' .

Check out the discussion if you really have the interest.
[http://foo-projects.org/pipermail/xfce4-dev/2006-December/021967.html](http://foo-projects.org/pipermail/xfce4-dev/2006-December/021967.html)

To make such a 3-in-1 applet to possibly exist, I cannot expect developers to rewrite their apps. So what you have in this applet is simply our 'existing' systray, tasklist, and launchers, 'blu-tacked' together, minus the extra icons, plus grouping and plus drag&drop feature.
----------------------------------------------------
**CONTRIBUTED IDEAS**
> **aidanr said:**
> 
i like the idea of grouping application windows into one button, would be cool for gimp etc, i'd say a good option for selecting a single window in one button would be that when you click on one part of the button it brings all of those windows to the front but only focuses the one you clicked, if that makes sense


**FAQ**
1.-----
> **aidanr said:**
> 
the only other problem i can see is that the systray is useful because it is permenently visible, but if you move to another workspace it doesn't show the taskbar items for other workspaces so you lose the systray functionality there, unless you set the taskbar to show windows from all workspaces, which would just make things more cluttered

[COLOR="DarkGreen"]Let's refer to the images above. Let's say you swap workspace. The 'taskbars' disappear but the 'icons' remain. That's what I had in mind.
OR
You swap workspace, everything disappears (that's what 'aidanr' assumes), so you start using the window 'stick' function. More detail on post #3.
[/COLOR]

2.------
So what does the icon function as? Program launcher? System tray?
[COLOR="#006400"]Both. So the GAIM icon starts off as a program launcher. You click on it, it launches GAIM.
You click on the GAIM icon again, it starts functioning as a systray. So you left-click it, it focuses the GAIM window and forms a taskbar. You right-click it, it pops up a menu. The usual really. You close down GAIM completely, the GAIM icon becomes a launcher again.[/COLOR]

But what about apps which don't normally have a system tray?
[COLOR="#006400"]You click on the Firefox icon, it launches and forms a taskbar.
You click on it again, since it does not have a systray, it just launches another Firefox window and forms another taskbar.
[/COLOR]

Answers provided are what MY ideal taskbar+systray hybrid would work. Maybe theres a better way?

Feedback appreciated,
Thank you,
Robin

---

### Post by aidanr on 2006-12-17
very interesting, i like the second screenshot a lot

a few points

a) definitely agree with drag and drop
b) i like the idea of grouping application windows into one button, would be cool for gimp etc, i'd say a good option for selecting a single window in one button would be that when you click on one part of the button it brings all of those windows to the front but only focuses the one you clicked, if that makes sense
c) when you right click or hover a window icon you get the systray functionality? this should be fine once you can still set pop-ups and notifications to appear in one corner of the screen (personal prefence and i think it would probably be neater) 

the only other problem i can see is that the systray is useful because it is permenently visible, but if you move to another workspace it doesn't show the taskbar items for other workspaces so you lose the systray functionality there, unless you set the taskbar to show windows from all workspaces, which would just make things more cluttered


still, very interesting idea, i'll be keeping an eye on this thread

edit:// i assume this would be a  gnome panel applet right? you'd just remove the systray and task switcher and add this in its place from right click -> add to panel

---

### Post by robin.com.au on 2006-12-17
> **aidanr said:**
> 
b) i like the idea of grouping application windows into one button, would be cool for Gimp etc, i'd say a good option for selecting a single window in one button would be that when you click on one part of the button it brings all of those windows to the front but only focuses the one you clicked, if that makes sense

Yes, makes sense, I like it. It can be an option which can be enabled/disabled.
> 
c) when you right click or hover a window icon you get the systray functionality? this should be fine once you can still set pop-ups and notifications to appear in one corner of the screen (personal prefence and i think it would probably be neater) 

Yes, maybe. By default, I think the notification bubble should appear directly under systray icon, just so user will know that bubble belongs to that app. I like how the bubble appears in Kopete, when someone sends the first message to you.
> 
the only other problem i can see is that the systray is useful because it is permenently visible, but if you move to another workspace it doesn't show the taskbar items for other workspaces so you lose the systray functionality there, unless you set the taskbar to show windows from all workspaces, which would just make things more cluttered

Yes I thought about that, but this is assuming that the window icon disappears if changing workspace or if all tasks are closed. I'm also wondering how often do people use the 'stick' function for window managers. I pretty much never use it. So maybe that function will see more use. Of course, it is a bit more work to do, especially with Metacity window manager, which currently does not remember window 'state' for each app. Whereas Enlightenment DOES remember the state.

Also another solution, which requires developers to rewrite the app, so it's more cumbersome. Don't you think the systray functions the same as an applet? Look at the note-taking app, Tomboy. It was a systray app, but now it's an applet for Gnome.

> 
still, very interesting idea, i'll be keeping an eye on this thread

edit:// i assume this would be a  gnome panel applet right? you'd just remove the systray and task switcher and add this in its place from right click -> add to panel
That's the idea. But don't get too excited. It is just a proposal and unfortunately I cannot code :(. So if this idea gets popular, you never know, people might start making something out of it.

Glad to hear that you like it.

---

### Post by aidanr on 2006-12-17
[QUOTE=robin.com.au]
Cluttered you say? In what way? Please explain.[/QUOTE]

ok, so the way i'm reading this is that the icon on the button in  the window list (taskbar) has the same functionality as an icon in the system tray

therefore, with the default settings, the window list only shows windows from the current workspace, so if you want to access the system tray functionality of a program you would have to switch to the workspace that program is on. to overcome this you could change the behaviour of the window list to show windows from all workspaces, but then you have a lot more buttons in the window list and hence more clutter

edit:// nm i see you updated the op, hadn't thought about the window icon remaining

---

### Post by maxamillion on 2006-12-17
This isn't an issue in xubuntu ... you could migrate to xfce if it bothers you too much :)

---

### Post by robin.com.au on 2006-12-17
Yes sorry aidanr, I actually withdrew the question about clutter. You are too fast.

> **maxamillion said:**
> This isn't an issue in xubuntu ... you could migrate to xfce if it bothers you too much :)
I AM using Xubuntu. I know theres an applet which has the system tray right next to the window list (funny I can't find that applet anymore). But what I want is, the app icon in the systray and the app icon in the window list, to be more 'related/grouped together'. Instead of 1 icon of Kopete here in the taskbar and **another** icon of Kopete there in the systray and **yet another** icon of Kopete over there as a program launcher. Hope you get what I mean.

---

### Post by robin.com.au on 2006-12-20
I've added a Flash demo so you all can visualize what I have in mind more clearly.

Minimum requirement is Flash Player 7.

[http://users.tpg.com.au/adsltimu/task-system-launcher.html](http://users.tpg.com.au/adsltimu/task-system-launcher.html)

Hope it looks good to you,
Robin

---

### Post by aidanr on 2006-12-20
hey, really nice job on the flash animation:KS:KS:KS:KS:KS

---

### Post by robin.com.au on 2006-12-21
Glad you like. Though the thread still remains not very active. What a shame.
I encourage people to take a look [http://users.tpg.com.au/adsltimu/task-system-launcher.html]("http://users.tpg.com.au/adsltimu/task-system-launcher.html")
I spend quite a bit of effort, creating this demo, as if it is like a 'screencast'.
Would like to hear your thoughts and your feedbacks on whether such a concept is worth adopting.

---

### Post by tszanon on 2006-12-21
Very interesting. Hope someone codes it one day.
The flash demo is very good, it helps a lot to understand.

---

### Post by rich.bradshaw on 2006-12-21
This is an excellent idea - awesome work on the animation as well! Hopefully there is someone here who knows how to do this...

---

### Post by tszanon on 2006-12-21
> **robin.com.au said:**
> **WINDOW LIST/TASKBAR + SYSTEM TRAY/NOTIFICATION AREA + PROGRAM LAUNCHER**
Maybe this should be in the 3rd Party Projects? Though there aren't programmers involved, there is a **concept** of what should be done. Maybe the idea could be discussed a little more before coding, and I think it would be great to have a seperate category for discussing and coding.

---

### Post by robin.com.au on 2006-12-21
Good to know the idea is well received.
Discuss away, that's all we non-coders can do really, just talking about it may grab some interested coder's attention.

For new comers to this thread, we are talking about this [http://users.tpg.com.au/adsltimu/tas...-launcher.html]("http://users.tpg.com.au/adsltimu/tas...-launcher.html (Flash 7+ required)") (Flash 7+ required)

---

### Post by robin.com.au on 2006-12-23
People who still uses flash player 7 for their browser would have encountered problems viewing my flash demo and may have frustrated people for lack of information in the demo.

I apologize.

I use Flash 8 through wine.
I even make it publish to an SWF file specifically for Flash Player 7.

Yet 'dynamic' texts still do not appear in Flash Player 7 for linux. (not sure if it's linux specific)

Anyway, I accidentally made several texts appear as 'dynamic', now it's changed to 'static', except the window title.

So now the only problem that will occur if using FP7, is that the window title of the app will not appear. If you are fussy, you can get FP9 beta 2 here [http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html")

I apologize again for the inconvenience.
Demo is here for your convenience.[ http://users.tpg.com.au/adsltimu/task-system-launcher.html]("http://users.tpg.com.au/adsltimu/task-system-launcher.html")

---

### Post by tomane on 2007-01-02
Nice work with that animation.
Now to what matters...
I found a couple inconsistencies in the demonstration:

**step 2a: **When a window/program is opened using this proposal, things will get pretty messy if we don't have a way to differentiate between running apps and launchers. Well, yes, you can fade the icon but there are colour combinations with which you can't tell the difference. Having only one icon per application makes it imperative to have some clear way to distinguish launchers from running icons.

**step 4: **When Kopete is launched, you have three handles, two of which correspond to *actual* windows and one that doesn't (it's a background app), shuffled. From a (personal) usability perspective this is *extremely *counter-intuitive because background applications have very specific purposes and deserve a place of their own. Imagine Klipper, kwallet, rythmbox, firefox, one terminal, and a file browser all mixed together... The point is, tray-type applications should be pushed to the tray side once launched, not forgetting the visual distinction needed to differentiate from the launcher.

**step 5:** (in the sequence of step 4) when rearranging window handles the difference between tray-apps and window handles should be preserved. Plus another question:
 - If I have another launcher in the bar, which hasn't been launched, can we *arrange* it too, mixed with the window handles?
I think it shouldn't because looking for a launcher between handles to open windows is not productive, much less efficient.

I suggest that you have a bar with 3 distinct areas: launchers, window list(with launcher attached) and tray area. Once an application is launched, its launcher is moved to the tray area if it is a background application (klipper), or moved to the window list (just like firefox in the demo). You could resort/arrange tray icons, window handles and launchers, but *not* mix them together.

**step 6: **(major flaw here) How can the system know which applications can have several instances/windows and which can have only one? Let me elaborate. The usage shown with the firefox handle looks nice, but with the kopete handle you have an inconsistency. In step 2b, left clicking in the (running) firefox launcher opens a second window. In step 6, left-clicking in the (running) kopete launcher does one of 2 things: a) close it *or* b) hide its window(?). This is not consistent behaviour. In case it's a), the system had to know which applications allow several instances and which don't, but yet, it wouldn't be consistent with the left click in (running) klipper, which opens a menu. In case it'd be b), it would be just plain wrong and hiding window handles should be done through a menu opened with a right click on the launcher icon. That's 3 different behaviours for the same action. Having this unified launcher/window handle scheme, it is imperative to have a clean way to manage them.


I like the basic idea of eliminating the (visual) redundancy of icons, but it requires a lot of effort until something practical and usable comes up. And we must keep in mind that we must avoid creating breakage with the applications themselves, in case the respond to clicks on the taskbar (something that I'm particularly familiar with O:) )

Cheers,
--to

---

### Post by robin.com.au on 2007-01-03
You have raised good points.

> **tomane said:**
> Nice work with that animation.

**step 2a: ** ... you can fade the icon but there are colour combinations with which you can't tell the difference. Having only one icon per application makes it imperative to have some clear way to distinguish launchers from running icons.

I agree. A faded icon as a not-launched app is not distinguishable enough. It may become too difficult to see. Any suggestions? I will think about this in the next version of the demo.

> 
[B]step 4: ... Imagine Klipper, kwallet, rythmbox, firefox, one terminal, and a file browser all mixed together... The point is, tray-type applications should be pushed to the tray side once launched, not forgetting the visual distinction needed to differentiate from the launcher.

I created this demo with 'grandmas' and complete computer 'newbies' in  mind.
I find that when I introduce people to computing or Linux, they get confused when trying to launch apps.
EXAMPLE: Let's look at the default panel layout in GNOME. 1 panel on top with sysem tray and 1 panel at the bottom with tasklist.

I tell them to launch Firefox. Firefox button appears in tasklist at the bottom. Clear enough.
I tell them to then launch Klipper. What happened? Nothing shows up. They were expecting to see something happen in the tasklist. But you and I know that the Klipper icon appears in the top panel in the system tray. But the newbies don't know that, and what if they don't know what the icon is suppose to look like?

We computer literate 'professors' are so used to the idea of taskbars and systrays in mind. We are still living in the Windows world I think. This is an effort to simplify things and keep 'related apps' all in 'one place'. But we live in a world where there are apps with systrays and apps with no systrays, and putting them together in one place, will unfortunately cause inconsistencies. 

For people who wants to use an applet like in the demo, but still wants 'systrays' to be on 1 side, 'running apps' on the other side and the 'launcher' on another side, you can do so withh drag & drop.

> 
**step 5:**...  - If I have another launcher in the bar, which hasn't been launched, can we *arrange* it too, mixed with the window handles?

I guess.
> 
I think it shouldn't because looking for a launcher between handles to open windows is not productive, much less efficient.

I believe it would not be hard to locate, since, everything (systray/launcher/task) are all in 1 place. And we distinguish between different apps with it's own distinct icon. Except now we won't have situations where there are more than 2 icons of the same app on the same panel. And since apps are grouped as 1 task, there won't be situations where the Firefox task button will be right in between 2 Terminals. You will definitely know, that all Terminals will always be to the left/right of Firefox.

I do understand your concern, and my idea 'may' not be as organised as it sounds. But we won't really know unless we use it and see how it affects our daily workflow.

> 
I suggest that you have a bar with 3 distinct areas: launchers, window list(with launcher attached) and tray area. Once an application is launched, its launcher is moved to the tray area if it is a background application (klipper), or moved to the window list (just like firefox in the demo). You could resort/arrange tray icons, window handles and launchers, but *not* mix them together.

That sounds like an idea, and I like it, and could be included as an extra feature that can be enabled/disabled. I created a mockup with a link below:
[http://www.robin.com.au/image/mywinlistc.png]("http://www.robin.com.au/image/mywinlistc.png")
Is that what you mean?

But I came across a problem. Look at an app like Opera. I currently have a systray running for it. Should it be on the taskbar side or the systray side?

> 
[B]step 6: ... The usage shown with the firefox handle looks nice, but with the kopete handle you have an inconsistency. In step 2b, left clicking in the (running) firefox launcher opens a second window. In step 6, left-clicking in the (running) kopete launcher does one of 2 things: a) close it *or* b) hide its window(?). This is not consistent behaviour. In case it's a), the system had to know which applications allow several instances and which don't, but yet, it wouldn't be consistent with the left click in (running) klipper, which opens a menu. In case it'd be b), it would be just plain wrong and hiding window handles should be done through a menu opened with a right click on the launcher icon. That's 3 different behaviours for the same action. Having this unified launcher/window handle scheme, it is imperative to have a clean way to manage them.

Ahh I can see why it can be confusing.

For Firefox, it does not have a systray, so when you LEFT-click the icon, it would launch and 'continue' to behave like a launcher whereas Kopete and Klipper would launch  and 'turns' into a sysem tray. RIGHT-click on a launcher normally does not do anything so I added the 'special menu'.

 I suggest you run Kopete and Klipper, and left/right-click on their systray icons and see how they behave. They behave 'exactly' like the demo (after launch).

Our current systray app is already an inconsistent thing. We left click on the icon, sometimes it focuses a window and creates a task button, sometimes it opens a menu, depending on the app.

To make such a 3-in-1 applet to possibly exist, I cannot expect developers to rewrite their apps. So what you have in this applet is simply our 'existing' systray, tasklist, and launchers, 'blu-tacked' together, minus the extra icons, plus grouping and plus drag&drop feature.
---

Anyway I've been discussing this in the XFCE mailing with the maintainers and many people liked it. But there are people who like the tasklist+systray but minus the launcher, others who like the tasklist+launcher but minus the systray, people like me who like all 3 together, and those who just like the grouping, drag&drop idea of the tasklist only. 

So I decided that in 'preferences' you are able to 'Enable/Disable System Tray integration' and 'Enable/Disable Launcher integration' .

Check out the discussion if you really have the interest.
[http://foo-projects.org/pipermail/xfce4-dev/2006-December/021967.html](http://foo-projects.org/pipermail/xfce4-dev/2006-December/021967.html)

Oh, and thank you for the interest. If I have time, I will fix and add more features, that was discussed, into the demo.

---

### Post by jclmusic on 2007-01-11
i think this is a great idea :) makes so much more sense!

---

### Post by pracslipkerm on 2007-04-07
This concept sounds great - the demo is fantastic, makes understanding the idea much easier. I look forward to seeing if anything comes of this - I found this thread looking for an answer to how to customise xfce taskbar...

---

### Post by robin.com.au on 2007-04-15
There's still flaws that needs to be addressed. 
The main issue is, how could this taskbar handle many many windows in 1 workspace?
I wanted to do a version 2 of this demo but these couple of month i've been sooooooooooo lazy.
Right now im using my laptop in bed. Sooooo lazy. I'm gonna watch some shows now.

---

### Post by dzv on 2007-04-16
I'm using Avant Window Navigator, and for me it seems to do a lot of what you want:

Certain launchers will automatically turn into a 'running app' icon when the program is launched (identified by a small triangle at the bottom of the icon).  Clicking on the 'running app' icon then focuses the window, rather than launch another instance.  Wwhile for other app launchers, a new icon appears on the dock each time it is launched.  Currently, the choice of which launchers act this way seems to be un-editable.  It's just the way it works.  It seems the program's author(s) have chosen what they believe to be the most sensible apps to apply it to.  Perhaps it could be modified so that you could choose which launchers to act this way.  Personally, I think the best idea would be that all launchers on the dock become 'running app' icons when launched, and then when more than one instance of an app is opened, they are all grouped in one icon, expanded when the icon is clicked (or mouse-overed).

As far as system tray icons go, I think it's not much of a problem to allow them to be another icon on the dock.  However, this might be a pain for some people who run a lot of system tray apps.  In which case, they might prefer a dedicated system tray.

---

### Post by robin.com.au on 2007-04-17
Interesting, 

The author seems to have lotsa pretty looking apps. [http://njpatel.blogspot.com/](http://njpatel.blogspot.com/)

I personally am not interested in another mac 'dock'. I have already tried so many other poor unstable imitations of it, like gnome-dock, kxdocker, etc. 

Even if they become stable, it would simply be a mac dock. Already done, nothing unique. If I want a dock, ill just get a mac. Quicksilver anyone?

What I want is something unique, something that the Linux community can say: 'you can't get this in any other OS!'

Although my proposed task-system-launcher applet is based on the same idea as a mac dock, when you look at it, a dock does not really come to mind (does it?). I also find that a dock takes too much height-space, and does not keep track of how many windows are actually opened for each application. I'm sure if I start using a Mac (I wish) and start getting used to the Mac 'way of life', the issues I raised above will probably be not an issue. But  most of us here are mainly Linux users, let's have something different from a dock, Apple can keep their dock.

If there is a .deb file out there for Avant, i will no doubt download it and play with it immediately. It still looks like a mac dock, but it seems to function a little different, maybe even better than a dock. I would like to get a feel of it before concluding whether it's 'just another dock' or not.

Thanks for sharing dzv, your post almost got me off my lazy *** and start getting this applet happening. Keep it coming and I might just get back to working on a better demo(which also involves sitting on my lazy ***) with less flaws, that's what some developers need me to do.

Robin

---

### Post by tehkain on 2007-04-22
I hate the OSX like docks since they focus on being big and graphically intense. Why? I just want the functionality. On top of that the Panel is perfect to house these icon launchers.

I am a fairly new developer but I am going to be starting  to develop a panel applet. The applet will work like the dock as a launcher/opener. Other then that I am gonna have to take a peak into the source code for some of these projects and see how I can maintain the functionality along with finding a way to fit it into the gnome panel.

---

### Post by robin.com.au on 2007-05-13
> **tehkain said:**
> I hate the OSX like docks since they focus on being big and graphically intense. Why? I just want the functionality. On top of that the Panel is perfect to house these icon launchers.
Of course you can resize the icons smaller in the OSX dock, so that's not the main issue I have with it. It is the lack of visual feedback showing the 'currently opened windows', whereas a panel (gnome/kde/xfce) has a taskbar/tasklist that does that. I think if a tasklist were to be implemented into the dock, it would turn out something like my demo.

> 
I am a fairly new developer but I am going to be starting  to develop a panel applet. The applet will work like the dock as a launcher/opener. Other then that I am gonna have to take a peak into the source code for some of these projects and see how I can maintain the functionality along with finding a way to fit it into the gnome panel.
Wonderful, would like to see how it turns out.

---

### Post by MaX on 2007-05-13
> **robin.com.au said:**
> Interesting, 

...snip...
> **robin.com.au said:**
> 
If there is a .deb file out there for Avant, i will no doubt download it and play with it immediately. It still looks like a mac dock, but it seems to function a little different, maybe even better than a dock. I would like to get a feel of it before concluding whether it's 'just another dock' or not.

Check this out for the .deb file
[http://ubuntuforums.org/showthread.php?p=2307772]("http://ubuntuforums.org/showthread.php?p=2307772")
> **robin.com.au said:**
> 
Thanks for sharing dzv, your post almost got me off my lazy *** and start getting this applet happening. Keep it coming and I might just get back to working on a better demo(which also involves sitting on my lazy ***) with less flaws, that's what some developers need me to do.

Robin

I really like your idea. Hope it works out into an actual application!

---

### Post by henriquemaia on 2007-06-10
Wonderful idea. I really loved the flash animation. I just hope this gets developed.

---

### Post by KIAaze on 2007-06-10
Fantastic idea! :D

---

### Post by sethmahoney on 2007-06-10
This is a really fantastic idea.  A couple suggestions/responses:

> **robin.com.au said:**
> A faded icon as a not-launched app is not distinguishable enough. It may become too difficult to see. Any suggestions?

Desaturation is the first thing that comes to mind.  Some kind of user-defined distinction is my second suggestion.  Perhaps optional integration with Beryl/Compiz through dBus to allow some flashier effects would be my third suggestion.

> **robin.com.au said:**
> But I came across a problem. Look at an app like Opera. I currently have a systray running for it. Should it be on the taskbar side or the systray side?

Maybe another model to consider (I'm actually not quite clear that this isn't what you're proposing already) is to distinguish as little as possible between systray apps and non-systray apps.  So having a way to "hide" or "extra-minimize" all windows for an app into its launcher icon (middle-click?) might be a start for resolving this issue.  Second, give *all* running apps the "launcher" icon on the left.  Third, have the initial click on the launcher icon launch the app, but all subsequent clicks open a menu.  Fourth, right-clicking on the launcher icon could open the systray menu for those apps that have them.  So, you could have something that looks like:

Starting state (X is a launcher icon):
```
X_____________________
```

Launcher icon clicked ([    ] is a taskbar item):
```
X[      title           ]_________
```

Another app launched (new app, new, non-permanent launcher icon):
```
X[     title     ]X[     title     ]__
```

Click on the first icon:
```
X[     title     ]X[     title     ]___
+-----------+
|  context  |
|    menu   |
|           |
+-----------+
```

First app minimized to icon:
```
X_X[     title     ]__________
```

And then have all apps, systray apps or regular ones, follow this pattern which would take some getting used to, but seems more intuitive overall.

You might also consider allowing easy configuration of different mouse buttons, hotkeys, and user-definable icons (I so hate the aMule icon).

---

### Post by gabng on 2007-08-01
I think this is a great idea, reserving screen space is always good.
Maybe this can be implemented as a panel applet, then users can add it to their panel if they want to use it in place of taskbar and notification area.

---

### Post by weblordpepe on 2007-08-02
Holy cow thats a great thing with grouping the child windows in the task-list like that.

Like how if you click on Firefox, all the other applications in the tray get smaller & just their icon is shown, and firefox gets bigger & shows some clickables for its child windows.

Kinda like how in the Mac, the applications menu on the top of the screen is tailered for the foreground application.


[SIZE="4"]EDIT:
You should make a blueprint for this so the devs take notice of it.
[https://blueprints.launchpad.net/ubuntu/gutsy](https://blueprints.launchpad.net/ubuntu/gutsy)[/SIZE]


Its not very often that the basic interface for a computer is improved upon in a significant way. I reckon this could be the next 'big' change. And it should be on linux first.

---

### Post by robin.com.au on 2007-08-02
Sorry guys, im still sitting on my lazy ***.
Other than that I've been real busy. I used to think I have soooo much time on my hands. Well not young anymore.

Anyway, I criticized about Avant Window Manager before,  I take it back, it's very nice & usable. Too bad compiz aint stable yet, but soon.

I wanted to make a blueprint, since February, but never got to it. I'm also not too sure what a blueprint should consist of. Must it be technical? Cos I really don't know the inner workings of panels/applets.

That blueprint URL looks tempting to click on. Might do that tomorrow. (That's what I said, 5 months ago)

---

### Post by Jhongy on 2007-08-02
Very impressive animated mock-up...

but.... for me, personally, this would be disasterous for (my) usability.

I want launchers to be in exactly the same place, every time -- I don't want them to move depending on whether that application is already open or not.

Systray applets also tend to be "special" -- they tend to be programs you leave running for longer periods of time. I want those functions to be in the same place, every time. I want to change network, or Beryl settings, whatever -- it's always there, in the same place, not moving around on the application switcher. I don't have to figure out where it is and why, or have to think "is this a launcher or a running applet?" before I click. That would just make previously simple taks overly "stressful". (an analogy is the abouse of the target="_blank" attribute on HTML links, or JavaScript popups -- you never have certainty when you click something as to what the action will be... sucks for usability).

Also, what's the big deal with duplication? On a PDA or mobile phone, this is important, but on everything else -- even the most limited of laptops, panel real estate isn't a problem. Also, I can put up with it on the PDA, as it is designed such that you don't have to *bother* with closing open programs.

I do agree that when "notification area" applications have a full program instance running that shows up on the taskbar, they should remove themselves from the notification area until they are minimised again to avoid duplication. But this is a minor point and down to individual application developers.

I've used a ton of docks, etc, and, aside from the "neat/cool/bling" factor, never really got into them. Sure, it's clever that a launcher can double up as a running application button.. but.... IME, it slows me down. I have to scan the list for mini arrows, different colour shading, or other tricks, so I can see what is actually running. Can't click-click-click between open apps as easily .

I guess, if this were an add-on panel applet, then fine -- I wouldn't use it. But this doesn't look like it would be up the Gnome dev's alley. 

In short, IMO, the notification area, the task list/switcher and the launchers all serve different purposes. I go hunting in specific areas to perform these specific tasks. There's a little overlap visually, but so what? Just seems totally counter-intuitive to create a "hybrid", and then have to rely on fancy visual clues and remembering different contextual behaviours to achieve the same result.

I love compiz-fusion, and don't mind a bit of bling -- but for me this is really form over function.

---

### Post by weblordpepe on 2007-08-02
> **robin.com.au said:**
> That blueprint URL looks tempting to click on. Might do that tomorrow. (That's what I said, 5 months ago)I'll tell you what I tell all of my colleagues. Do it or I'll punch ya in the guts. :lolflag:

---

### Post by ugm6hr on 2007-08-03
I like this.  Especially the combination of systray / launcher (which I have always thought was a bit wasteful).  

One thought from a personal view.  I would find it more natural if "launchers" of closed apps return to a "fixed" (i.e. prespecified) location in the taskbar (either left or right - perhaps customizable).  I think it would indeed confuse me if my launchers (of which I use many) were interspersed with open apps on the taskbar.

Just to make sure you don't feel like there's no support for your idea...

An XFCE fan :)

---

### Post by smah77 on 2007-09-12
> **Jhongy said:**
> I want launchers to be in exactly the same place, every time -- I don't want them to move depending on whether that application is already open or not.

That's a good point, though I think that problem could be overcome perhaps.

> **Jhongy said:**
> I don't have to figure out where it is and why, or have to think "is this a launcher or a running applet?"

If I understand correctly, part of the point would be so that you never have to think about whether what you're clicking on is a launcher or an applet or a running task.  All icons should function more or less the same, as if the program is already running.  A simple example would be a gaim launcher: If it isn't running, it starts gaim (and, probably, should change the icon - maybe non-running launchers could be desaturated or something).  If it is running, it opens your buddy list.  As far as the user is concerned, the interaction should be the same either way.

> **Jhongy said:**
> I do agree that when "notification area" applications have a full program instance running that shows up on the taskbar, they should remove themselves from the notification area until they are minimised again to avoid duplication. But this is a minor point and down to individual application developers.

I generally think that the notification area should never be used by running tasks or what are effectively launchers (ahem, tomboy and gaim).  It should only be used, well, never.  There should only be panel applets and the window list.

> **Jhongy said:**
> Just seems totally counter-intuitive to create a "hybrid", and then have to rely on fancy visual clues and remembering different contextual behaviours to achieve the same result.

I'm reading this in the exact opposite way.  Currently, we have separate areas that cue us (visually) to use different ways of interacting with them (they're in different contexts).  The idea should be to make them all effectively act in the same way and require only one way of working with them.  The current panel/launcher/window list/notification area doesn't do this, and if we weren't all accustomed to it it wouldn't make a lot of sense.  The Apple dock doesn't do this, though its better at it, since it combines launchers and running tasks.  The logical step, for me, would be to use the same set of interactions with any given program, regardless of where we're used to seeing it.  Gaim should be gaim whether it is running or not, and should more or less behave, as far as the panel is concerned, like firefox or tomboy or openoffice: Left click = open/launch, right click = menu.

---

### Post by MaX on 2007-10-01
So, is this dead?

---

### Post by madsmeg on 2007-10-01
Started last December and has only 4 pages... i wouldn't go as far as dead as.. not posted on regularly :)

---

### Post by weblordpepe on 2007-10-03
AAH!! Who woke me up? Damnit! Be quiet we're trying to sleep in this thread.

---

### Post by Mr. Picklesworth on 2007-10-26
Your window list here is really interesting. I like how you handle the division between open windows and running processes; inspires a level of sanity that I previously have seen only from the Mac's otherwise irritating shared menu bar. I think I will stare at the panel's window list applet and try to apply some of this idea! (No promises, mind. Anyone else, feel free to beat me to it, since I will take forever).
One change I suggest: The icon for a running process should be visible on all workspaces.

The way you handle launchers is also intriguing. Personally, I never use launchers, since I can just use Deskbar or the menu. However, what they do here is unify programs that are and are not running under the same interface, which is good. The division of open processes and open windows handles that fine for me, though. We can probably settle on a middle grounds:
Processes could tell the applet that they want to be divided, marked as special processes. They are thus grouped on a particular side, with a nice bar to separate them from regular processes. Any process can take over its various handlers on that applet. (The default would include Quit in a context menu for the process, which should get the message across: Put Quit In Your Context Menu).

I'll use Tomboy as an example...
No, in my scenario it does not have a launcher or anything of the sort. It is a process run at startup. It registers itself as special, and now I have something that *looks* a bit like a launcher, but is actually a notification of a running process. This is a good way to have a program quickly available but not taking up much visual space. When Tomboy opens a top-level window, that window appears beside the notification, as in your example with launchers.

The goal there is to integrate launchers, running processes, notifications and open windows under one hood which clearly presents the differences and the similarities.

Note that I am not thinking to take over the notification area, since that gadget is quite different. (Notifications are not tied to processes, so it would be *very* inconsistent to duplicate its job here). However, having said that, this could solve a serious issue with the notification area and be a fine alternative to its use. According to the GNOME Human Interface Guidelines, the only things that should appear in the notification area are 'notifications'. Applications should not be permanently placing themselves there as some arbitrary alternative to the window list. Three very common examples of applications misusing it that way are Liferea, Tomboy and NetworkManager. Their notifications can be tied directly to running processes, they have the same context menus as running processes, and they are always there as long as the processes exist. They are not really notifying us of anything significant except that they exist (which is already known).
Those particular programs would feel more at home making us aware of their existence via our new applications list, on which they would now be able to take up minimal space, be visible consistently across all workspaces, and have access to their signal handlers on the list.

---

### Post by zeusalmighty on 2008-01-20
Very nice concept! I've been busting my head as to why on earth there wasn't a feature like re-arranging your tasks on the taskbar! Why oh WHY?! I'd be really happy to at least see that in Ubuntu.

---

### Post by robin.com.au on 2008-01-21
Hellooo,

As you can see, it's been how many years? I still have not done anything about the idea, im always busy, or busy being lazy, but hopefully this idea helps to inspire someone in some related/unrelated endeavour on their UI design.

I also have a distaste for the concept of floating windows which we are all far too familiar with. The idea of moving, resizing, minimizing, maximizing windows, windows blocking windows. This idea of taskbar and systray hybrid is only a small temporary bandaid but does not address the window issue directly.

I talked about this on another thread as old as this one, and also as equally unpopular. I didn't explain too clearly, probably because I tried to explain with 'words'. Should have done a flash presentation.

[Ion3]("http://modeemi.fi/~tuomov/ion/") is what im talking about basically. The way window managers should be.

Too lazy to promote any of my ideas but If I were to push any idea in the far future, it would be some sort of user-friendly ion3-based thing.

So yeah this post really can be summarised to:
Lost interest in this taskbar/systray idea, this thread is pretty much dead to me, currently interested in [Ion3]("http://modeemi.fi/~tuomov/ion/"). Funnily enough the author of ion3 had also lost interest in his project according to wikipedia.

But hey if someone comes along to implement this idea, im all for it.
Avant-window-navigator doesn't count, still copying the mac dock completely, still good though.

---

### Post by krizz on 2008-05-13
It's a great idea. Especially the Notification-Launcher merging it would be great! Other features great too!

I can't help in development so I just adding my enthusiasm :D

Great Work robin.com.au

---

