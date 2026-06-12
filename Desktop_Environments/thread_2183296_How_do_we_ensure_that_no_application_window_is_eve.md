---
title: "How do we ensure that no application window is ever at full size in Ubuntu 13.10?"
date: 2013-10-24
forum: Desktop Environments
---

### Post by Jim_Granite on 2013-10-24
**How do we ensure that no application window is ever fully full screen size?**

The reason it matters greatly, especially in dual-boot Windows/Linux systems, is that we can only solve the problem of window controls being on the wrong corner for windows that are not full size ([see details here]("http://ubuntuforums.org/showthread.php?t=2182627&p=12824205#post12824205")).

At the same time, we have a setting in Ubuntu 13.10 to re-allow window menus to be directly  associated with the windows they belong to ([see details here]("http://ubuntuforums.org/showthread.php?t=2182900&p=12826615#post12826615")).

The problem is that these fixes work only for windows that aren't full size. :(

In order to make the Ubuntu 13.10 GUI workable (especially for those with dual-boot Windows/Ubuntu systems), **how do we ensure that an application window is NEVER full size?**

Note: [I]Some applications, such as the screenshot utility, somehow enforce this concept of disallowing full-size windows; so we just have to figure out HOW they accomplish that worthy task.
[/I][ATTACH=CONFIG]247199[/ATTACH][ATTACH=CONFIG]247198[/ATTACH]

---

### Post by mc4man on 2013-10-24
(referring to an ubuntu session (unity
What you'll notice in your screen is the maximize/restore button isn't in screenshot window.

The only way to max a window is to do it yourself by clicking the max/restore button or invoking grid to top which only will happen when grabbing/moving a window & pulling into top panel.
( which sometimes maxes to below panel, sometimes into panel.

So you could simply avoid doing either, as far as grid it can be disabled in ccsm (compizconfig-settings-manager

Or you can remove the max/restore button altogether globally or on a per window basis, couple of ways to do that

---

### Post by stinkeye on 2013-10-24
As mc4man said there are various things you can do which are not perfect and lose you screen real estate.
If your main problem is due to a dual boot situation, why not make your MS-windows install behave like unity.
Here's one ......[**_[COLOR="#B22222"]LeftSider 1.03[/COLOR]_**]("http://www.softpedia.com/progDownload/LeftSider-Download-139241.html")
:P

---

### Post by mc4man on 2013-10-24
I believe our friend here wants windows & ubuntu to align as much as possible which is ok with me even if I don't.
So in this matter you could apply the same theory as you did to switch to right, just remove 'maximize' 

Otherwise pretty simple to do in ccsm (compizconfig-settings-manager

Open, go down to the 'window rules' plugin > Non maximzable windows
Type in 
type=any
Click on enable the plugin by checking the little box
screen shows

(that setting can be used for individual window classes if desired though I believe you want all.
The only real downside is you'll lose restore, not big deal, you can resize manually if desired

Note - windows rules plugin can do alot of things & while not an issue with this simple deal if wishing to experiment I'd strongly suggest creating a new user & experimenting there. That way if anything gets really borked no big deal..

---

### Post by Jim_Granite on 2013-10-25
> **mc4man said:**
> maximize/restore button isn't in screenshot window.

I hadn't actually noticed that, until you mentioned it, but, yes, you correct that the window controls are missing, and that this is NOT what I wanted.
All I want is for window controls to stay put, and, one workaround is to somehow set the maximum window size to one pixel below the monitor vertical resolution.

> **mc4man said:**
> The only way to max a window is to do it yourself
At the moment, I'm **manually** maximizing windows to as close to one pixel below my vertical screen resolution as I can get.

However, I can't count the number of browser windows that pop up in front or behind the current browser, many of which are maximized and all of which need to be closed. To close them, I have to hunt and peck for the window controls, which not only are on the wrong side, but, they're initially hidden, which necessitates further mouse clicks, just to close a window that popped up outside of your pop-up blocker.

Plus, a browser is just one of many applications, so, any browser-specific solution is merely a point workaround, e.g., 
 *[Firefox]about:config->browser.tabs.closeButtons->(change from 1 to 3 to force the tab close button to stay to the right)*

So, there still is a need to PREVENT a maximized window from being the full screen size (where one pixel below vertical resolution should fix this bug instantly).

> **mc4man said:**
> Or you can remove the max/restore button altogether globally or on a per window basis, couple of ways to do that
After reading your post, I experimented with the "screenshot" application, and, realized that **removing** the max/restore button is a lousy solution because you can't **RESIZE** the resulting window. That's bad. 

**The real goal is to have the window controls stay put** (instead of bouncing all over the place and even hiding sometimes).
The *workaround* (at the moment) is to manually RESIZE every application to just a tad under full-screen size. 
Only then do the window controls stay where they belong.

But, you still want the ease-of-use double-clicking on the top window border to maximize the window (to one pixel below vertical resolution).
And, you want the window control "maximize" button to do the same thing.
The goal is to keep the window controls from bouncing all over the place.

For example, with a maximized window, e.g., using KolourPaint as shown below, all the internal pop-up dialog boxes will have the window controls on the right, yet, the main window itself will have the window controls on the left. That makes absolutely no sense from a usability standpoint.
[ATTACH=CONFIG]247216[/ATTACH]
> **stinkeye said:**
> you ... lose you screen real estate
Maximizing a window is normally convenient, easy, and common. 
In this case, it's miserable because you can only do it manually (as any automatic method causes the window controls to bounce around).
That's why I seek an automatic solution.

Losing one pixel of real estate is vastly preferable to window controls that inexplicably bounce around so that you can never predict where they'll be with your "hand memory".
[ATTACH=CONFIG]247217[/ATTACH]

> **stinkeye said:**
> If your main problem is due to a dual boot situation, why not make your MS-windows install behave like unity.
While I understand that window controls can be on the left or the right, there is no added value to either one, so, for Unity to allow a left/right setting makes sense.
In fact, the left setting might satisfy long-time dual-boot Mac users while the right setting would satisfy dual-boot Linux users.

I, myself, have been using Windows since version 3-point-something, so, my "muscle memory" expects the controls in the top right.
In addition, it's absolutely crazy to have to modify the other operating system (that isn't even running at the time) in order to work around a bug in Unity.

The fact that the window controls bounce around all over the place is the real problem.
If the setting to put them on the right simply worked, there would be no further comment (nor need to fix the bug with a workaround).

Given that mc4man pointed out the problem with eliminating maximize/minimize capability, the best workaround I can think of is to somehow set the maximum screen size of any maximized window to one pixel below the vertical resolution of the monitor. In my case, with a 1920 x 1080, the setting I seek would simply set the maximum window size to 1920x1079.

> **mc4man said:**
> I believe our friend here wants windows &  ubuntu to align as much as possible

The real goal is to have the window controls stay put (whether that be right or left, shouldn't matter).
I prefer my window controls on the right (for a variety of good reasons), and there is absolutly no added value to them being on the left.
If the setting to put window controls on the right actually worked, we wouldn't even be having this discussion.

The real problem is that the window controls bounce all over the place.
So, this thread is merely an attempt at an elegant workaround to that bug.

> **mc4man said:**
> pretty simple to do in ccsm (compizconfig-settings-manager).
Open, go down to the 'window rules' plugin > Non maximzable windows

I'm a bit confused by that suggestion, because, I still want windows to maximize the same way they always have (for decades!).
I only want them to maximize to one pixel below vertical screen resolution instead of to screen resolution (so that the window controls stay put).

> **mc4man said:**
> I'd strongly  suggest creating a new user & experimenting there. That way if  anything gets really borked no big deal..
Due to the Ubuntu 13.04 DVD crashing every time I tried to have it set the initial partitions, I have to re-install the operating system all over again anyway.
But that's the topic of a different conversation. I only bring it up to point out that I'm documenting the setup so that I can reproduce it when I finally get the Ubuntu DVD to stop crashing when resizing partitions (it works just fine if you let it take all the defaults, after Windows 7 got the primary partition).

---

### Post by stinkeye on 2013-10-25
> **mc4man said:**
> I believe our friend here wants windows & ubuntu to align as much as possible which is ok with me even if I don't.

It's ok with me too but because of the global menu in unity and what I've read so far it seems 
changing MSwindows, if possible, would be easier.

---

### Post by Jim_Granite on 2013-10-25
> **stinkeye said:**
> It's ok with me too but because of the global menu in unity and what I've read so far it seems 
changing MSwindows, if possible, would be easier.

I'm not sure what you mean but, as an old man who has been using computer software since the 80's, I'll reiterate these two statements:

1. The bug here is simply that the setting to put window controls on the right isn't working properly.
2. The workaround to change some other operating system that isn't even running at the time, doesn't make any sense.

Changing all your other operating systems to work around a Unity bug makes even less sense when you consider that you now have to change EVERY Windows and Linux OS on every computer in the household (since every other Linux handles this without problem, and specifically RHEL6, which is still on my work computers).

The problem is in Ubuntu 13.10. Not in Microsoft Windows. Not in RHEL6. Not in Centos 6. Not in Fedora. etc.
It's a really simple-to-explain unity bug:

BUG: The Unity setting for windows controls isn't working on all windows:
```

/usr/bin/unity-tweak-tool
[unity-tweak-tool]Window Controls->Alignment->Right
```

This bug in this setting is that it should simply change ALL window controls to the right, not just some.
All we're doing here is to attempt a workaround to this bug.

---

### Post by stinkeye on 2013-10-25
> **Jim_Granite said:**
> I'm not sure what you mean but, as an old man who has been using computer software since the 80's, I'll reiterate these two statements:

1. The bug here is simply that the setting to put window controls on the right isn't working properly.
2. The workaround to change some other operating system that isn't even running at the time, doesn't make any sense.

Changing all your other operating systems to work around a Unity bug makes even less sense when you consider that you now have to change EVERY Windows and Linux OS on every computer in the household (since every other Linux handles this without problem, and specifically RHEL6, which is still on my work computers).

The problem is in Ubuntu 13.10. Not in Microsoft Windows. Not in RHEL6. Not in Centos 6. Not in Fedora. etc.
It's a really simple-to-explain unity bug:

BUG: The Unity setting for windows controls isn't working properly:
```

/usr/bin/unity-tweak-tool
[unity-tweak-tool]Window Controls->Alignment->Right
```

This bug in this setting is that it should simply change ALL window controls to the right, not just some.
All we're doing here is to attempt a workaround to this bug.

I wouldn't actually call it a bug.
Unity was designed with the window controls to be used on the left and doubt if Canonical regard it as a bug when
you are able to move the window controls with some **third party** tweak tools.
....and as you mentioned "dual-boot" in your first post, I assumed you wanted window controls to be consistent
in both operating systems and gave you a solution.

---

### Post by Jim_Granite on 2013-10-25
> **stinkeye said:**
> I doubt if Canonical regard it as a bug when you are able to move the window controls with some **third party** tweak tools
That's interesting. Thank you for that information. I appreciate the detail.
I had not realized that the tweak tool wasn't from Canonical. 
So, I guess there are two bugs then - but it doesn't really matter (except for filing a bug report to the appropriate people).
Usually developers appreciate bug reports, since it tells them in no uncertain terms what they need to fix.

> **stinkeye said:**
> I assumed you wanted window controls to be consistent in both operating systems and gave you a solution.

Actually, I want do consistency and I do appreciate the suggestions.
It matters not, functionally, whether the controls are on the right or left - but - historically - all other Linux and all Windows operating systems default to the right.
Our "muscle memory" clearly defaults to the right, whether we're on our pc, our kid's pc, a library PC, our friend's PC, etc.

To "allow" users the "preference" to put them on the right or left is just fine.

But, other than Canonical, I doubt there is any Linux out there that has the window controls in the wrong spot, by default.
And, I doubt there is any Windows system out there that, by default, puts the window controls on the wrong side.

So, even if I *did* switch my dual-boot system over to the wrong side, I'd still have to switch to the right side whenever I used another Windows or Linux machine in the household and at work and at the library, etc.

> **stinkeye said:**
> I wouldn't actually call it a bug.

To make this one version of Linux different than all the rest is a goal of the developers; but to do it in a way that is incompatible with the use model on all other Linuxes, and, which adds absolutely no value, would be considered a *lost functionality or usability bug* at every software company I've ever worked at.

I will need to comb through the bug report logs to find out what Canonical has to say about this, as I can't be the first person who is dismayed by this coding error.

---

### Post by stinkeye on 2013-10-25
What you may find is recently Canonical (like others) are more focused on tablet/phone functionality
because they see this as the future and a market they can break into more readily.
Sometimes the fuctionality of the desktop even becomes secondary like the fact
you cant click on a launcher icon to minimize that application.

I find ways to make unity work for me because I  feel the upside still outweighs the downside,
while others have moved  on to more traditional destops like xfce or cinnamon in lnux mint.

As I only boot into windows occasionally to play the one game, 
the window controls on the left are something I quickly got used to.
Actually I don't even use the buttons anymore.
I find it easier to use mouse gestures rather than go to some little button in a corner.

---

### Post by Jim_Granite on 2013-10-25
> **stinkeye said:**
> What you may find is recently Canonical (like others) are more focused on tablet/phone functionality
I don't doubt they're copying what they can from Apple, whom they see as successful with GUIs; but they're actually not going to get there by making window controls that bounce all over the place.

> **stinkeye said:**
> Sometimes the fuctionality of the desktop even becomes secondary like the fact you cant click on a launcher icon to minimize that application.
Hmmm... maybe that's why I constantly can't find my minimized windows within an application. I haven't figured out yet (it has only been a few days) what the preferred method is to find, say, the third window of five that I've opened in an application.

> **stinkeye said:**
> 
Actually I don't even use the buttons anymore. I find it easier to use mouse gestures rather than go to some little button in a corner.
I've used what we called "strokes" at the time, since the mid 1990s on a variety of proprietary systems. I never did like them, and, over time, they all were deprecated as being unworkable. Maybe they're better nowadays, but, I use the Lenovo "erasure" in the middle of the keyboard, sans a mouse (I am always of the KISS principle) and I don't see the value in strokes (unless they've vastly improved over time).

If I could only figure out a way to have the MAXIMIZE button not go to 1920x1080, but, to 1919x1080, I'd have a perfectly good workaround to the bug that the window controls don't stay on the same corner for the various windows.

---

