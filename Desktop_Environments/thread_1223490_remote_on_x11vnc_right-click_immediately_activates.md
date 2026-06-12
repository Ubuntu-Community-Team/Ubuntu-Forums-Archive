---
title: "remote on x11vnc: right-click immediately activates the option in the context menu"
date: 2009-07-26
forum: Desktop Environments
---

### Post by michalre on 2009-07-26
Hi,

I am connected to the jaunty running x11vnc with the xtightvncviewer.
When I perform a right click a context menu appears but immediately the option with the cursor on it is activated.

For example in the gnome-terminal when I right click on the window client area, context menu appears (with items like Open Terminal, Open Tab, Close Window, Copy, Paste ...) but immediately the item Open Terminal is activated and new terminal windows is opened.

Let me know if I can provide any further info.

Thanks for any help.

---

### Post by krunge on 2009-07-26
> For example in the gnome-terminal when I right click on the window client area, context menu appears (with items like Open Terminal, Open Tab, Close Window, Copy, Paste ...) but immediately the item Open Terminal is activated 

Run x11vnc with the option '-dp -dp'  (i.e. twice for more output.)  This provides pointer debugging output.

I suggest running x11vnc in a terminal that is **not** on the remote desktop, but rather is a terminal on your local desktop (e.g. one you ssh to the remote machine.)  This way the verbose printout doesn't induce a huge volume of VNC updates.

Then get a flavor for the output by moving the mouse, clicking, dragging, etc.   And then reproduce the context menu problem and see if it is x11vnc that is injecting the 'extra' pointer event that is activating the menu action.  It may be something besides x11vnc...

---

### Post by michalre on 2009-07-26
> **krunge said:**
> Run x11vnc with the option '-dp -dp'  (i.e. twice for more output.)  This provides pointer debugging output.

I suggest running x11vnc in a terminal that is **not** on the remote desktop, but rather is a terminal on your local desktop (e.g. one you ssh to the remote machine.)  This way the verbose printout doesn't induce a huge volume of VNC updates.

Then get a flavor for the output by moving the mouse, clicking, dragging, etc.   And then reproduce the context menu problem and see if it is x11vnc that is injecting the 'extra' pointer event that is activating the menu action.  It may be something besides x11vnc...

Thanks for your response!

I have reproduced the issue 3 times in a row with x11vnc started with -dp -dp options. You can find the output in the attachment.

I have investigated further with xev tool and the difference between local physical right-click and remote x11vnc right-click seems to be that there is an extra move event between button down and button up events.
I tried to physically simulate the move on the local desktop and I can more or less confirm that if I hold a right button long enough to be able to make the move and then release it, it will activate the option from the context menu. Whereas holding the right button for the same amount of time (and then releasing it) without a move will not activate the options and context menu stays open.

---

### Post by krunge on 2009-07-27
> **michalre said:**
> I have reproduced the issue 3 times in a row with x11vnc started with -dp -dp options. You can find the output in the attachment.

I have investigated further with xev tool and the difference between local physical right-click and remote x11vnc right-click seems to be that there is an extra move event between button down and button up events.

In the x11vnc.log file I don't see the 'extra move event'.  Are you suggesting it is recorded in that log file?  If so, could you post a (or the) particular event sequence that shows it?

In either case, a shot in the dark: recently a fellow in these forums found an odd behavior with the mouse running x11vnc on his laptop with a partially closed lid:
[INDENT][http://ubuntuforums.org/showthread.php?t=1215708&highlight=x11vnc](http://ubuntuforums.org/showthread.php?t=1215708&highlight=x11vnc)[/INDENT]
Could something similar be happening with your setup?

---

### Post by michalre on 2009-07-29
> **krunge said:**
> In the x11vnc.log file I don't see the 'extra move event'.  Are you suggesting it is recorded in that log file?  If so, could you post a (or the) particular event sequence that shows it?

In either case, a shot in the dark: recently a fellow in these forums found an odd behavior with the mouse running x11vnc on his laptop with a partially closed lid:
[INDENT][http://ubuntuforums.org/showthread.php?t=1215708&highlight=x11vnc](http://ubuntuforums.org/showthread.php?t=1215708&highlight=x11vnc)[/INDENT]
Could something similar be happening with your setup?


I think I can see an extra move event in the output of the xev tool(attached).

But I am not very familiar with xorg system. Do you think that the extra move event could cause the context menu activation?

And if it is not in the x11vnc.log, do you have any suggestion how can I pinpoint the source of this move event?

I have forgotten to mention before that I don't see any movement of the cursor on the screen. And also xev.log is not reporting the change in the pointer coordinates:
```

MotionNotify event, serial 35, synthetic NO, window 0x7800001,
    root 0x1a7, subw 0x0, time 84648733, (74,127), root:(579,491),
    state 0x10, is_hint 0, same_screen YES

ButtonPress event, serial 35, synthetic NO, window 0x7800001,
    root 0x1a7, subw 0x0, time 84648749, (74,127), root:(579,491),
    state 0x10, button 3, same_screen YES

MotionNotify event, serial 35, synthetic NO, window 0x7800001,
    root 0x1a7, subw 0x0, time 84648802, (74,127), root:(579,491),
    state 0x410, is_hint 0, same_screen YES

ButtonRelease event, serial 35, synthetic NO, window 0x7800001,
    root 0x1a7, subw 0x0, time 84648802, (74,127), root:(579,491),
    state 0x410, button 3, same_screen YES


```

Thanks for any help.

---

### Post by krunge on 2009-07-29
> I think I can see an extra move event in the output of the xev tool(attached).

Yes, I see it.  Note that it happens at same time as the ButtonRelease event ("time" item in the xev output.)  x11vnc may be sending it right before the Release, I'm not sure.  I don't think it should make a difference...
> 
But I am not very familiar with xorg system. Do you think that the extra move event could cause the context menu activation?

I don't think it should.  That is surprising to me, I don't think a gui should  react to a twitch like that.

For these event sequences, are you saying you **do not** release the mouse button at that time?

---

### Post by michalre on 2009-07-29
> **krunge said:**
> 

For these event sequences, are you saying you **do not** release the mouse button at that time?


No, I release it. I performed a standard right button click.

---

### Post by krunge on 2009-07-29
> **michalre said:**
> No, I release it. I performed a standard right button click.
I think I finally understand: you press and release button3 expecting it to post the menu only, but it acts at though it was click+drag+release and it invokes a menu item.

And it makes some sense that the gui toolkit might interpret that (dx = dy = 0) motion event between the two button events as a drag (even though there was no actual displacement.)

In any event, I ran gnome-terminal and tried to reproduce your problem. I can't: it simply posts the menu as expected.  I verified with xev that I, too, am getting that dx=dy=0 motion event between the two button events.

I did not run this under GNOME though and need to test that later.  Why don't you try this in a failsafe session and see if it still happens (you could start a window manager like twm or xfce if you have difficulty doing the test w/o one.)

---

### Post by michalre on 2009-07-29
> **krunge said:**
> I think I finally understand: you press and release button3 expecting it to post the menu only, but it acts at though it was click+drag+release and it invokes a menu item.


Exactly! Great we are on the same page now.

I am able to reproduce the issue in gnome, kde and xfce. But in xfce not with the gnome-terminal but with the Eclipse IDE, because it has big context menus.

I think that it can simply be the matter of the popup position of the context menu and its items. When context menu appears in a position that mouse pointer is above one of its items, then item gets activated because the extra move event.

So I guess the question is where is that move event coming from.

On the other hand I might have some wrong/nonstandard configuration somewhere. I will try to reproduce the issue with Ubuntu Live CD soon.

---

### Post by krunge on 2009-07-29
> **michalre said:**
> But in xfce not with the gnome-terminal but with the Eclipse IDE, because it has big context menus.

So for gnome-terminal in xfce the menu worked properly?  That could be an important clue...
> 
So I guess the question is where is that move event coming from.

No, I am pretty sure it is x11vnc is sending it.  It has been doing it this way for over 7 years. This is the first complaint about this problem (that I have heard of.)

IMHO, the gui toolkit should track dx and dy and if they are always zero it should not think that a drag has occurred.

It is possible your desktop or something else is interfering in some strange way.  Can you collect a list of apps for which this problem occurs (ideally identifying the gui toolkit, e.g. gtk, qt, etc.)

---

### Post by michalre on 2009-08-02
I have some more, hopefully useful, info:

Note: By "reproduce the issue" I mean it is happening every time I do the right click.

1) I did a clean install of Ubuntu 9.04 Jaunty, then installed packages openssh-server and x11vnc and I can reproduce the issue with gnome-terminal. (It can even be reproduced after just booting to Live Ubuntu Jaunty CD).

2) Same as the point 1 but now I did a clean install of Ubuntu 8.10 Intrepid. I was able to reproduce the issue with gnome-terminal.

3) I tried tightvnc client and realvnc client from both Windows and Ubuntu Jaunty and I was able to reproduce the issue for every combination of OS and vnc client

4) I have installed tightvnc server on Ubuntu Jaunty. Connected to this vnc server I was not able to reproduce the issue. Also according to the xev there was no Motion event between Button press and Button release events.

5) I have tried various themes through GUI System->Preferences-> Appearance. For some, like "New Wave" I was not able to reproduce the issue in any application.

I am thinking about building x11vnc from the sources. Do you happen to know how complex a change to the sources would it be to remove that intermediate Motion event? I don't want to break some other functionality :-)

Thanks

---

### Post by krunge on 2009-08-02
Thanks for your last post.  I was able to reproduce the problem.

I had to do it running gnome-terminal inside GNOME.  Last week I tried gnome-terminal inside of fvwm and could not reproduce the problem.

Using a Debian squeeze/sid test machine in my basement I tested all of these window managers:```
GNOME, FluxBox, KDE, TWM, WindowMaker, XFCE, and Failsafe-Terminal
``` Only for GNOME and XFCE did gnome-terminal give the incorrect behavior (i.e. execute the first menu item, 'Open Terminal', when button3 was released).  For all of the others, FluxBox, KDE, TWM, WindowMaker, and Failsafe-Terminal, gnome-terminal acted correctly when I released mouse button3 (i.e. it simply posted the menu and invoked no action.)

I also tested the konsole terminal for all of the above window managers, and in no case did clicking mouse button3 do anything but the correct expected behavior of simply posting the menu.

Please verify that you find something similar.

It is also good there is a obvious workaround: don't release button3 until you move the mouse into position.

Since gnome-terminal failed in GNOME and XFCE and the menu colors looked somewhat different, perhaps it is related to some sort of "theme" as you suggest (i.e. you couldn't reproduce it in one of them.)

It is easy to blame x11vnc for this (and OTOH it should be easy to provide a workaround option for this), but I do have a feeling this is really a regression in the app/toolkit or app/toolkit+theme interaction that the developers did not intend to introduce.

---

### Post by michalre on 2009-08-02
Glad you was able to reproduce the issue.

I can confirm it for the following apps(after colon is the unwanted action, and window manager is in the brackets (I have only tested gnome and kde for now)):

1) gnome-terminal: new terminal (gnome, kde)
2) gedit: undo (gnome, kde)
3) Tomboy/New Note: close (gnome, kde)
4) Evolution/Compose Message: Undo (gnome, kde)
5) google chrome unstable: back (gnome, not tested in kde)
6) Eclipse IDE: whatever is under the pointer (has big contex menus) (gnome, not tested in kde)

I could not reproduce it for konsole or any other application from the kde application menu.

Hopefully my tests in kde are valid, because I did not perform clean install of the kubuntu. I just did sudo aptitute install kubuntu-desktop, restarted pc, selected KDE session and logged in.

I think that you are right about the bug(regression) in the app/toolkit. Unfortunately it seems, that, at least for now, only x11vnc exposed that bug.

Also from my simplistic high level understanding of x11vnc as redirector of an user input and xserver output, injecting motion event which was not performed on the client can be considered as an incorrect behavior. What's your take on this?

---

### Post by krunge on 2009-08-03
> Also from my simplistic high level understanding of x11vnc as redirector of an user input and xserver output, injecting motion event which was not performed on the client can be considered as an incorrect behavior. What's your take on this?
I believe x11vnc is playing it safe in a very simple way to make sure the mouse in the correct position before injecting the button event.

You see, the mouse may have been moved by the user on the physical display, an application performing a warp, or a 2nd vncviewer user. If it skipped the motion event to position the mouse, it could inject the button click in the wrong window, etc

BTW, the VNC protocol only sends the triple (x, y, button_mask), and so x11vnc is simply moving the mouse to (x, y) before applying the button_mask.

x11vnc could do things more carefully by polling the X server for the actual physical mouse position right before it injects the button event and decide to skip positioning it if it looks OK, but it doesn't currently.

However, in the current x11vnc 0.9.9 development tarball there is an option that should work around the problem you are seeing.  Run something like this```
x11vnc -env X11VNC_WATCH_DX_DY=1 ...
``` This mode doesn't poll the X server for the actual pointer position, but it will skip the extra motion event if the mouse pointer hasn't moved since the last vnc pointer event.

---

### Post by michalre on 2009-08-03
Thanks, I will give it a try.

---

### Post by michalre on 2009-08-07
I have been using x11vnc-0.9.9_TEST_i686-Linux with the option -env X11VNC_WATCH_DX_DY=1 for 4 days now and the issue is gone.

Thanks for your effort. This has been a single best and fastest support I have ever get. Thanks again and good luck with x11vnc in the future.

---

### Post by krunge on 2009-08-15
> **michalre said:**
> I have been using x11vnc-0.9.9_TEST_i686-Linux with the option -env X11VNC_WATCH_DX_DY=1 for 4 days now and the issue is gone.
Very good!
> Thanks for your effort. This has been a single best and fastest support I have ever get. Thanks again and good luck with x11vnc in the future.
Thanks for the kind words.

However, I am still wondering if this really is a problem with the menu theme (or something similar.)  Is it really 'acceptable form' for a menu to assume the user will never bump or glitch the mouse a pixel or two before releasing the button?  For example, somewhat rushed motion to clicking area with mouse not completely stopped yet.

I am not a HCI person, but IMHO I think it is 'good form' for a menu to post with the mouse a few pixels outside of any of the menu item 'active zones' to avoid (to a good degree) these accidental glitches. Many of the  menus do that and it appears to be intentional. If you agree, maybe you can file a bug against the menus you found to help save the world :-)

---

### Post by michalre on 2009-08-30
[QUOTE=krunge]

For example, somewhat rushed motion to clicking area with mouse not completely stopped yet.[/QUOTE]

Actually this has happened to me more than one time with the local physical mouse. It can be reproduced pretty easily.

I did some local testing and found the following concerning the right mouse button behavior when a context menu appears under the mouse cursor:

1) Sequence: press, wait less then cca 500ms, release - does not activate the context menu item.
2) Sequence: press, wait more then cca 500ms, release  - does activate the context menu item
3) Sequence: press, move pointer during cca 500ms period, release - does activate the context menu item.

It is apparent that point 3 is inconsistent with the point 1. And since the point 1 makes perfect sense to me, point 3 behavior is IMHO a bug. And the correct behavior should be that if the mouse makes a move within that cca 500ms period, context menu item should not be activated. 

I am not sure under which component should this bug go. I think the best solution should be independent on the themes and their context menu positions, just like the point 1.

I am not familiar with the X architecture but since point 3 behavior can be reproduced in gnome and in kde as well could it indicate that the bug is below the level of a window manager and the right component for the bug would be Xorg server itself?

---

### Post by bono8106 on 2010-06-07
I would like to echo the point that x11vnc could be considered to have incorrect behavior here (for sending an unneeded mouse move event).

I can understand where this might be helpful, if the mouse had been moved by a separate application or another user... however, the menu auto-selection problem (discussed here) is not the only issue caused by the extra mouse move event...

1) gnome-terminal - every mouse click causes a selection of the character underneath. This is not only a nuisance, but can be a problem - say I select some text in one applciation and then click on a gnome-terminal window to activate it and paste the selection into gnome-terminal - this won't work because the click triggers a character to be selected in gnome-terminal, which overrides the previous selection which I wanted to paste.

2) at work, we use clearcase gui tools, which accept a selection of objects on mouse-click, but that selection does not work when there is a mouse-move event in between the mouse-down and mouse-up.

I'm  sure there are other applications which exhibit similar problems.

The point is that, it would be much harder to fix all the applications out there (VERY unrealistic to expect a fix in clearcase proprietary tools for example), probably unrealistic to expect a fix everywhere.

Furthermore, other vnc servers for real x displays, such as vino, do not have this problem.

I tested the new option to monitor DX_and DY, and am happy to report that this works for me too. If I run into any issues with use, I will let you know here.

Bottom line though for me is, the problems caused by the extra mouse-move event are serious in that they affect my day-to-day work constantly. At the same time I have not in the past, and do not expect to run into issues with applications moving my mouse cursor around.

So,

+1 for turning the X11VNC_WATCH_DX_DY option on by default in a future release, and leaving the old behavior as an option that has to explicitly be set to revert back to the old way.


Cheers,
-Nikolay

---

