---
title: "Multiple Monitor problem in 11.10"
date: 2011-10-22
forum: Desktop Environments
---

### Post by Eyeless Blond on 2011-10-22
Okay, ever since the upgrade from 10.10 to 11.04 I've been having the most annoying problem with my multiple monitor configuration. My preferred setup is to have a 24-inch LED-LCD monitor as my "main" monitor in landscape mode, with a 21-inch IPS monitor in portrait mode off to the right. This used to work fine, but ever since the upgrade to 11.04 it hasn't. In fact, what happens is really weird: I get a sort of "overlay" where the second, portrait monitor's workspace sort of overlaps on top of the main landscape monitor. 

So far this has meant I can't have the second monitor in portrait mode at all; I have to leave it in landscape to use it at all, which is really not ideal because my desk isn't really big enough to have both monitors like that. Any ideas on how to fix this?

---

### Post by bangbong on 2011-10-23
I am having the same issue... :lolflag:
Just upgraded today, noted that my box can shutdown properly now.

---

### Post by Eyeless Blond on 2011-10-23
Yeah, and Suspend doesn't magically move everything from RAM to the swapfile, which is much appreciated. So both Shutdown and Suspend work right now, and rebooting doesn't take five minutes either, which is cool.

I do wish this Unity thing wasn't so lame. What's with this useless "Home" lens? If you're going to make me waste a click every time I want to launch an application, fill it with widgets rather than waste my time with four icons that ought to already be in the Launcher pane! And why isn't anything customizable? Ugh.

Oh yeah, and I really wish Ubuntu could come up with a decent actually dark theme, rather than this washed-out "Ambiance" thing. If you're going to break my themes, the ones I've had on this computer since 2007, give me some new options at least.

But by far the most annoying thing to me is the monitors. Any ideas on how to fix it?

---

### Post by Eyeless Blond on 2011-10-24
So yeah, and now Unity has crashed on me, because I made the mistake of trying to open CCSM, and unity --reset is crashing on me. Almost makes me want to downgrade to 10.10, the only edition of Ubuntu where everything actually worked, despite the fact that it isn't supported anymore.

---

### Post by typhoon_tip on 2011-10-24
> **Eyeless Blond said:**
> So yeah, and now Unity has crashed on me, because I made the mistake of trying to open CCSM, and unity --reset is crashing on me. Almost makes me want to downgrade to 10.10, the only edition of Ubuntu where everything actually worked, despite the fact that it isn't supported anymore.

I was quite with you till I found some easy adjustment for Unity and 11.10, because Gnome 3 crashed on me (video driver issues), and I am very satisfied of the current performance and eye-catching results. Just google around and you will find a lot of apps to help you customize things up a bit to one's taste (gnome-tweak-tool will be sufficient, to help you select the themes, font size and other options).

Back to the thread, I have yet to try some multi-monitor configuration, as soon as I do I will post my findings (upgraded a few days ago, laptop).

---

### Post by Eyeless Blond on 2011-10-24
> **typhoon_tip said:**
> I was quite with you till I found some easy adjustment for Unity and 11.10, because Gnome 3 crashed on me (video driver issues), and I am very satisfied of the current performance and eye-catching results. Just google around and you will find a lot of apps to help you customize things up a bit to one's taste (gnome-tweak-tool will be sufficient, to help you select the themes, font size and other options).

Well, I'm not all that unhappy with Unity (I do wish I could put the launcher back on the bottom of the screen where it belongs, and configure that Home lens to something actually useful), but right now the problem is that Unity is outright crashing on me at startup; it's dumping me on a blank screen, with no launcher pane, and oddly with Nautilus's File menu where the top bar should be. By hitting Ctrl-Alt-F2 I can get to a terminal, log in, then type Unity --reset, which **also** crashes (something about compiz(core) unhandled configureNotify on 0x260016a! and Warn: this should never happen; you should probably file a bug about this), but while it's crashing I can hit Ctrl-Alt-F7 and get back to my work, as part of Unity --reset's proceedure is to temporarily replace compiz with metacity, so I can have a window decorator and shell that works... sort of... while I'm waiting for Unity to fail again.

---

### Post by typhoon_tip on 2011-10-24
> **Eyeless Blond said:**
> Well, I'm not all that unhappy with Unity (I do wish I could put the launcher back on the bottom of the screen where it belongs, and configure that Home lens to something actually useful), but right now the problem is that Unity is outright crashing on me at startup; it's dumping me on a blank screen, with no launcher pane, and oddly with Nautilus's File menu where the top bar should be. By hitting Ctrl-Alt-F2 I can get to a terminal, log in, then type Unity --reset, which **also** crashes (something about compiz(core) unhandled configureNotify on 0x260016a! and Warn: this should never happen; you should probably file a bug about this), but while it's crashing I can hit Ctrl-Alt-F7 and get back to my work, as part of Unity --reset's proceedure is to temporarily replace compiz with metacity, so I can have a window decorator and shell that works... sort of... while I'm waiting for Unity to fail again.

If you did an upgrade like me, try resetting everything and then logout/login again, it may work:

1. rename $HOME$/.config/dconf/user to $HOME$/.config/dconf/user.old
2. logoff or restart

That file stores all user settings of desktop, if you did an upgrade it may have messed up (I messed it up many times while attempting at Gnome 3...).

---

### Post by Eyeless Blond on 2011-10-24
Hmm... nope, doesn't look like that helped anything. Unity's still not coming back on boot, and unity --reset is still hanging at the same spot. Any other ideas?

---

### Post by Eyeless Blond on 2011-10-29
I guess no one knows how to configure multiple monitors in Ubuntu?

---

### Post by tyxle on 2011-10-29
[IMG]http://i759.photobucket.com/albums/xx240/tizzleh/ubuntu/monitor_setup.png[/IMG]I haven't figured out a way to fix it but, you can go into Monitor Setup and place one your screens ON TOP. This allows you to use both monitors but the mouse cursor will not go between screens unless you move it to the top or bottom of the screen. The upgrade screwed me up so badly I went back to 11.04. I hope this helps people who are going to stick with 11.10, til' a legitimate fix comes out.

---

