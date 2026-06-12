---
title: "KDE 3.5.0 broken"
date: 2005-12-18
forum: Desktop Environments
---

### Post by pestie on 2005-12-18
Hi, folks. I installed the KDE 3.5.0 final packages linked on kubuntu.org and now wish that I hadn't. Three things are really burnin' my ass right now:

1. The multiple monitor support is broken. I un-check multi-monitor maximize support, for example, because I don't want my windows maximized across both of my monitors. It ignores this and maximizes them across both monitors anyway. KDE 3.4.x never did this. Along these same lines, if I say I want my default window placement to be "center," it centers new windows on the whole desktop (i.e. half the window on one monitor, half on the other). I want it centered on monitor #1. Again, KDE 3.4.x worked correctly with the right multi-monitor options set. Finally, I told it I wanted unmanaged windows in monitor 1 and yet it always opens them on monitor 2. I think it may be confused by the fact that monitor 2 is to the left of monitor 1, so the lower-numbered X coordinates are on monitor 2.

2. Sound is totally broken. Any attempt to start artsd, manually or automatically, segfaults.

3. My settings got totally hosed up somehow. This didn't happen as soon as I installed KDE 3.5.0, but after one of the updates, I think. Basically, I logged out, logged back in, and a ton of stuff broke. A bunch of panel applets, like the desktop browser, clock, K menu, etc. didn't start. I had to control-alt-backspace to kill X, then delete my $HOME/.kde directory and start fresh.

I either want to fix some/all of these problems or roll back to the default KDE that comes with Breezy. I can live with the broken-settings thing, and even with the crappy multi-head support, but no sound? That's a bit of a problem. If there's no solution to that one, I'd just as soon roll back to KDE 3.4.x. It's not obvious to me how to do that, though, using aptitude or synaptic.

---

### Post by HermanAB on 2005-12-18
The Xinerama extensions is an X function - not KDE's fault.

Go to /etc/X11 and look at xorg.conf section "ServerLayout"

It is a good idea to backup this file on a CDROM once you have it working to your satisfaction...

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by vh1 on 2005-12-19
[QUOTE=HermanAB]The Xinerama extensions is an X function - not KDE's fault.[/QUOTE]
I think the thing is they worked in KDE 3.4 and not in KDE 3.5

I have all those options checked and operation is pretty normal. only odd thing is that windows open on the display containing the mouse cursor

---

### Post by f1dave on 2005-12-19
*2. Sound is totally broken. Any attempt to start artsd, manually or automatically, segfaults.*

Back in ye old days when I first got kde 3.5 beta packages, this was an issue. However, it's been long since fixed, so I'm surprised somewhat to see that it breaks on your system. I have a couple of suggestions-

1. Try another sudo apt-get update, sudo apt-get dist-upgrade to see if that fixes the problem.

2. Look in the ubuntu wiki for any issues with kde for your hardware.

3. If you know how, rollback your version of arts- there's a howto floating around here and also one on the wiki for KDEBetaKnownProblems

I hope you get some luck out of one of those.

---

### Post by Zotova on 2005-12-19
Does using alsa instead of arts fix your sound problem?

---

### Post by pestie on 2005-12-21
I fixed the sound problem!

I backed up /usr/bin/artsd and created a shell script that dumped its command line arguments to a file so I could at least see what the hell KDE was trying to do when it was trying to start artsd. The command line is:
```
/usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f
```
Changing "-l 3" to "-l 1" changes artsd's information level from "quiet" to "info." Next time KDE tried to invoke it, I saw several message boxes, two of which were complaining that some library files were missing. It was looking for /usr/lib/libarts_akode.la, I believe. A quick "aptitude install libarts1-akode" later and my sound is working.

I think the packages provided by kubuntu.org simply don't have all their dependencies set up correctly. Something, somewhere, should definitely be requiring **libarts1-akode** but isn't.

Now if I could just get multi-head support working right I'd *really* be happy. But I can live with it the way it is for now.

---

### Post by Asraniel on 2005-12-21
hm. i dont have the problem, BUT, i had to run the full upgrade 3 times, every time at least one package could not be installed, but the next time it worked. so, after 3 or 4 tries all were installed. look in adept if there are any updates left

---

### Post by pestie on 2005-12-25
The first thing I tried when I had problems was the update/upgrade procedure to make sure everything had installed correctly, and it had. Turns out that part of it worked fine for me the first time.

Another update: I figured out the multiple-monitor thing. It was simply that I misunderstood the options. I had turned *off* the following options:

Enable multiple monitor window placement support
Enable multiple monitor window maximize support
Enable multiple monitor window fullscreen support

I was thinking that enabling those options meant, for example, "Enable a maximized window to occupy multiple monitors as if they were one big screen." Turns out it means the exact opposite! "Multiple monitor window maximize support" means "treat multiple monitors as their own discreet entities, not as one big, unified desktop." So now all my dialog boxes and maximized windows are placed entirely on one monitor or the other, not in the middle, and not across multiple monitors.

My last complaint is related to the taskbar's multi-monitor support. Regardless of the status of the options such as "show windows from all screens" or "show windows from all desktops," dragging any application from the "primary" monitor (the one with the taskbar) to the "secondary" will cause that item to disappear from the taskbar altogether. Drag it back and it reappears. The problem arises when I minimize a window on the second monitor. No trace of the program exists anywhere except the window list dialog (middle-clicking on the desktop, for example). It looks like the program has crashed or something, but it's still happily running away with no visible trace. Clearly the options I mentioned are supposed to fix that, but they don't.

---

