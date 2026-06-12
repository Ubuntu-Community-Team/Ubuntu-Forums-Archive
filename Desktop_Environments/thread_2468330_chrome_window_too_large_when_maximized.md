---
title: "chrome window too large when maximized"
date: 2021-10-25
forum: Desktop Environments
---

### Post by Kilarin on 2021-10-25
My wife is running Xubuntu 20.04 on her machine, and she just ran into a VERY odd display issue.
As of today (It wasn't doing this yesterday) if she maximizes chrome, it maximizes to larger than the screen.  As in, the x button in the upper right corner is only about half visible.   You can see a little bit of the chrome window bleeding over into the second monitor.  If you drag the chrome window over to the second monitor and maximize there, the behavior is the same, the window is a little bit too large for the screen.   You can un-maximize and resize chrome, then maximize it again, it goes right back to too big for the screen.

This happens with chrome ONLY.  firefox, thunderbird, gimp, any other program she can maximize, and the window fits on the screen perfectly.  maximize chrome, and it maximizes too large.

Reboot the computer, chrome still maximizes too large.

Even though the controls are partially obscured, they are all still accessible, so this is more of an annoyance than a serious problem.  But she expected me to understand why it was doing this, and I've never seen anything like it before.

Save my reputation as a computer nerd with my wife please!  Help me figure this out!!!! :)

Is this a chrome problem?  or has something gone wonky in Xubuntu that I'm not familiar with?

Thank you,

---

### Post by T6&amp;sfpER35% on 2021-10-26
iv'e noticed the exact same thing in my Brave browser recently
it comes and goes ,sometimes it displays right other times it doesn't 
doesn't bother me too much since i can still click the corner buttons
i tried auto adjusting my screen but it doesn't help 
so , yea ...don't know

---

### Post by Kilarin on 2021-10-26
Well, at least I know I'm not alone. :)

---

### Post by ActionParsnip on 2021-10-27
If you press F11 to full screen, then again to bring it back does it then maximised OK? Just a brain idea

---

### Post by Kilarin on 2021-10-27
ok, MY computer just started doing this with chrome, same thing that my wife was seeing.
This morning everything was fine.  during the day, there was an update popup, I think chrome was in the mix, I took the update.
Now this evening, Chrome when maximized is bigger than my screen size.
I've attached a screenshot.  I've got two monitors,  I used Gimp to put a line at 1920, where the first screen ends, to show how chrome now overlaps onto the second monitor when maximized.  (and, of course, that most of the top bar extends past the top of the screen)

[https://i.imgur.com/yr2efTj.png](https://i.imgur.com/yr2efTj.png)

oh, and yes, I tried f11 and back, no difference.

---

### Post by forreggbor on 2021-10-28
I thought I'm alone but great to be in a company. :-D
It might be a chromium issue:
[https://bugs.chromium.org/p/chromium/issues/detail?id=1261797&q=maximized&can=2](https://bugs.chromium.org/p/chromium/issues/detail?id=1261797&q=maximized&can=2)

---

### Post by ajgreeny on 2021-10-28
I am not seeing that at all in my Xubuntu 20.04 using the PPA for chromium from [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) which ata present gives me version  chromium-91.0.4472.27.

I am about to change to the dev ppa from the same developer which is chromium-95 to see if that makes any difference; back in a few minutes.

EDIT:
Still no problem for me with chromium-95.0.4638.17

I do not use Chrome, only chromium, so can not really comment about that.

I wonder if this might be related to a proprietary graphic card and driver; what graphics system do you have?
My systems (all of them) use integrated Intel graphics.

---

### Post by Kilarin on 2021-10-28
thank you for the link forreggbor.  Since this is happening ONLY on chrome, that might be it.
I have both chrome and chromium installed.   The problem does not happen on chromium right now, only on actual chrome.

I'm running a ThinkPad E15 Gen 2 with an intel i3-1115G4 processor, graphics is Integrated Intel UHD
My wife's machine is also a Thinkpad, but its a t490s with an i5-8365U processor, graphics is also Integrated Intel UHD

---

### Post by ActionParsnip on 2021-10-29
If you make a fresh Ubuntu user and log in as that, is it the same?

---

### Post by Kilarin on 2021-10-29
[quote="ActionParsnip"] If you make a fresh Ubuntu user and log in as that, is it the same? [/quote]
Good idea!
Tried it, chrome does the same thing when logged in as the new user.  :(

---

### Post by Paddy Landau on 2021-10-31
I notice that you talk about having two monitors. What happens if you restart with just the one monitor connected?

Of course, it might be the bug that @forreggbor posted. Be sure to upvote the bug ("star" the issue).

I don't have the problem; I'm using Ubuntu (which uses Gnome). Your wife is using XFCE. You don't say what you are using?

If you are also using XFCE, what if you log in with Gnome? (N.B. use a separate test account to test this, otherwise it could mess up your own account settings.)

---

### Post by nautix on 2021-11-03
I, too, have noticed this behavior as of a week or two ago. I wasn't able to narrow down which apps or screens were affected and which weren't. Now I see a pattern.

It only occurs with Chrome, not other apps (so far).

When I have Chome setting "Use system title bar and borders" set to OFF and maximize a window, about half of the tabs and the upper-right buttons (minimize, maximize, close, etc.) are obscured by the task bar. (I keep my task bar at the top of the screen.)

When I have "Use system title bar and borders" set to ON and maximize the window, the entire title bar is obscured by the task bar.

When I use dual screens, only the primary screen is affected. The secondary screen works fine.

I'm running Barrier to share my keyboard and mouse with my Windows laptop, but when I kill barrer and barriers processes, the problem persists.

So, the pattern I see is that it only affects Chrome (so far) regardless of whether or not I use the system title bar and window decorations, and only on the primary screen regardless of whether or not I have a secondary screen.

---

### Post by nautix on 2021-11-03
CORRECTION:

It affects the secondary monitor, too.

---

### Post by repetezvous92 on 2021-11-03
An up-to-date Xubuntu 20.04 with the very same issue here, first noticed a few weeks ago on my laptop with Intel graphics and on both Brave and Chrome browsers. I've started the Xubuntu 20.04 install on my other computer this evening (for the first time in a month or so), installed all the waiting updates (including for both above browsers) and I now have the same annoyance on this machine (this also has Intel graphics).

Both Chrome and Brave are displayed perfectly with every restart of either browser. It's marginally worse when using Chrome over Brave, in that that the [x]  button to close the browser is completely obscured with the window  maximised. 

There are no such issues at all when using Firefox on either machine, and I only have the one display for my desktop PC.

EDIT: This looks relevant, I think?

[https://www.reddit.com/r/xfce/comments/qhp3zg/bug_maximizing_edgechrome_goes_out_of_the_panel/](https://www.reddit.com/r/xfce/comments/qhp3zg/bug_maximizing_edgechrome_goes_out_of_the_panel/)

---

### Post by ActionParsnip on 2021-11-04
Possibly a bug then...?

---

### Post by Paddy Landau on 2021-11-04
> **repetezvous92 said:**
> This looks relevant, I think?
[https://www.reddit.com/r/xfce/comments/qhp3zg/bug_maximizing_edgechrome_goes_out_of_the_panel/](https://www.reddit.com/r/xfce/comments/qhp3zg/bug_maximizing_edgechrome_goes_out_of_the_panel/)
I've added a comment there to cross-link this thread and to note the previously-noted bug.

---

### Post by angelsguitar on 2021-11-04
Same here. First noticed this Chrome behavior about 2 weeks ago. I'm running Xubuntu 20.04.

---

### Post by Paddy Landau on 2021-11-04
> **angelsguitar said:**
> Same here. First noticed this Chrome behavior about 2 weeks ago. I'm running Xubuntu 20.04.
Reminder to everyone with this problem: Remember to upvote ("star") [the bug]("https://bugs.chromium.org/p/chromium/issues/detail?id=1261797") so that the devs take it seriously.

---

### Post by Kilarin on 2021-11-07
Thank you so much everyone for all the help and research!
I've starred the chrome issue.

---

### Post by ptroy2 on 2021-11-12
Hi

It's happening to me with chromium [COLOR=#5F6368][FONT=Roboto]95.0.4638.69 (Official Build) snap (64-bit) and Xubuntu 21.10

PhilTroy[/FONT][/COLOR]

---

### Post by cfharris on 2021-11-15
Just want to add that I have the same issue exactly as [COLOR=#000000]Kilarin describes. 
[/COLOR][COLOR=#000000][/COLOR]
Xubuntu 20.04 fully patched.

---

