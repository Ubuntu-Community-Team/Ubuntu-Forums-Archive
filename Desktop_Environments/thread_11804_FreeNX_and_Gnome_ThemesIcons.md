---
title: "FreeNX and Gnome Themes/Icons"
date: 2005-01-19
forum: Desktop Environments
---

### Post by dare2dreamer on 2005-01-19
I recently installed FreeNX from the (Ubuntu-Backports project) and found that while it works very well, and very very fast, it has some visual glitches.

Specifically, it seems to ignore custom themes and icons, reverting a remoted session to the basic gnome theme and iconpack. As a default Ubuntu desktop has several custom visual elements, I end up with broken icons all over my desktop.

I'm sure its some sort of configuration issue, as everything appears to be working other than FreeNX's ability to figure out where the theme-related stuffs are.

Any ideas?

---

### Post by jdong on 2005-02-13
Yeah, I've seen this numerous times, too. Doesn't happen with a session of ANY other WM/DE.

I'm clueless on this one, but don't think it's a Ubuntu-specific problem (google?)

---

### Post by lm05 on 2005-03-01
[QUOTE=dare2dreamer]I recently installed FreeNX from the (Ubuntu-Backports project) and found that while it works very well, and very very fast, it has some visual glitches.

Specifically, it seems to ignore custom themes and icons, reverting a remoted session to the basic gnome theme and iconpack. As a default Ubuntu desktop has several custom visual elements, I end up with broken icons all over my desktop.

I'm sure its some sort of configuration issue, as everything appears to be working other than FreeNX's ability to figure out where the theme-related stuffs are.

Any ideas?[/QUOTE]

From what I understand there is an underlying link to GDM being the root cause of this problem. Apparently if you disable it, the issues will go away.

However that is not a solution for me.... So....

The issue only occurs when you have logged in as the same user multiple times. i.e. If you have logged in to X/Gnome locally on the box and then logged in via a remote X or FreeNX session. So the answer is... only have one logged in session running at any given time. This works for me.

Let me know how you go!

LM

---

### Post by dare2dreamer on 2005-03-01
sounds like a lock file that needs to be removed or something similar.

Anyone know enough about GDM to take a guess?

---

### Post by ioliver on 2005-06-21
Did anyone ever find a solution to this one?

It's very annoying.

Ian

---

### Post by dare2dreamer on 2005-06-21
I'm not sure there ever was a definitive fix, however if you are logged out at the console then all of your remote sessions will work without issues.

I generally solve it by remotely restarting X/GDM if I forget to log out. ;-)

---

### Post by ioliver on 2005-06-22
I tried killing gdm, but ended up using the pragmitc approach of "sudo reboot"!

What's the best way to restart gdm?

I'm now using NX to connect to my two home Ubuntu boxes from my WinXP machine at work. It's *very* slick, despite my home ADSL being maxed out with a fair bit of bittorrent stuff.

Ian

---

### Post by jdong on 2005-06-22
After a bit of investigation:

The NX protocol limits the maximum color depth to 256 colors, it appears. Any icon theme requiring more colors is therefore not allowed.

NX 1.5.0 ("coming soon") will fix this by  adding more color support.

---

### Post by XDevHald on 2005-06-22
[QUOTE=jdong]After a bit of investigation:

The NX protocol limits the maximum color depth to 256 colors, it appears. Any icon theme requiring more colors is therefore not allowed.

NX 1.5.0 ("coming soon") will fix this by  adding more color support.[/QUOTE]
 Thanks for the update, I was wondering the samething about the icons and themes of why when extracting them they wouldn't work. :)

---

### Post by ioliver on 2005-06-22
But the 1st NX connection gets the right theme (as long as not logged in locally) And even getting a remote desktop using SSH and xnest suffers the same problem.

The 1st gnome login gets the right theme, and subsequent ones don't.

I'll try setting up an NX connection 1st and *then* logging in locally to get more data points, but my machine needs to complete a 400G copy first.

Once I've done this, I might stick it on bugzilla.

Ian

---

### Post by ioliver on 2005-06-23
As people have hinted, it's already a well-known problem, and quite a chewy one at that. 

[http://bugzilla.gnome.org/show_bug.cgi?id=94049](http://bugzilla.gnome.org/show_bug.cgi?id=94049)

This bug is heading towards its 3rd birthday!  The maintainer does now seem to have accepted a patch, but things aren't exactly racing ahead.

Ian

---

### Post by ioliver on 2005-06-23
I'm currently testing a fix of using Run Application to launch "gnome-settings-daemon"  Working OK so far.
Ian

---

### Post by oofnik on 2005-06-29
I just installed the freenx server on my Ubuntu desktop, and the NX client on an XP box on my network. I just have to say I am simply blown away by the performance. All the VNC flavors don't even compare to this. Right before this, I found the builtin xino-server on Ubuntu (System -> Prefs -> Remote Desktop), which was faster than x11vnc, but I knew it could be better. Freenx is the answer!
This bug that you guys are talking about with the dual login issue isn't limited to freenx. When I run VNC servers on a separate X desktop running GDM and try to log in again, the same error happens. So I guess for now I just need to make sure to log out locally before logging in to freenx. I hope there will be some sort of work-around for this. Or perhaps, would it be possible to configure freenx to share a desktop rather than open a new one?

But anyway I tried running gnome-settings-daemon and my icons and everything appeared correctly, thanks ioliver. But here's something funky. Whenever I open the connection, I get this popup error no less than three times:
```
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The XFree86 Project, Inc
40300000
You are using XFree 4.3.0.
There are known problems with complex XKB configurations.
Try using simpler configuration or taking more fresh version of XFree software.
If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>
```
Does this happen to anybody else?  :-? It says it could be due to a bug in xmodmap, which is running to reconfigure my IntelliMouse buttons, but I don't know how to check this without disabling it.. oh well, I guess I can live with the popups, hah. :|

---

### Post by dare2dreamer on 2005-07-06
running gnome-settings-daemon fixes things for me as well. Is there a way to get nx to execute an arbitrary command on login so the command doesn't have to be fired off manually?

---

### Post by jdong on 2005-07-07
Yeah, that fixes it here, too (though I do feel a slight performance loss due to the more complex gradients and shading in the default themes)

Probably adding gnome-settings-daemon to your GNOME Session (Preferences) would do it. Running multiple copies doesn't cause any harm...

---

### Post by douceur on 2005-07-08
[QUOTE=oofnik]I just installed the freenx server on my Ubuntu desktop, and the NX client on an XP box on my network. I just have to say I am simply blown away by the performance. All the VNC flavors don't even compare to this. Right before this, I found the builtin xino-server on Ubuntu (System -> Prefs -> Remote Desktop), which was faster than x11vnc, but I knew it could be better. Freenx is the answer!
This bug that you guys are talking about with the dual login issue isn't limited to freenx. When I run VNC servers on a separate X desktop running GDM and try to log in again, the same error happens. So I guess for now I just need to make sure to log out locally before logging in to freenx. I hope there will be some sort of work-around for this. Or perhaps, would it be possible to configure freenx to share a desktop rather than open a new one?

But anyway I tried running gnome-settings-daemon and my icons and everything appeared correctly, thanks ioliver. But here's something funky. Whenever I open the connection, I get this popup error no less than three times:
```
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The XFree86 Project, Inc
40300000
You are using XFree 4.3.0.
There are known problems with complex XKB configurations.
Try using simpler configuration or taking more fresh version of XFree software.
If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>
```
Does this happen to anybody else?  :-? It says it could be due to a bug in xmodmap, which is running to reconfigure my IntelliMouse buttons, but I don't know how to check this without disabling it.. oh well, I guess I can live with the popups, hah. :|[/QUOTE]

I'm getting this error too.  Any ideas?

---

### Post by ioliver on 2005-07-14
To fix this popup try the following -

ln -s /etc/X11/xkb/rules/xfree86 /etc/X11/xkb/rules/xorg 
ln -s /etc/X11/xkb/rules/xfree86.lst /etc/X11/xkb/rules/xorg.lst

You may need to chuck sudo before each of those lines.

The bug is described here -
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=120858](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=120858)

The soft link fix worked for me.

Ian

---

### Post by gnomicon on 2005-09-03
[QUOTE=lm05]

The issue only occurs when you have logged in as the same user multiple times. i.e. If you have logged in to X/Gnome locally on the box and then logged in via a remote X or FreeNX session. So the answer is... only have one logged in session running at any given time. This works for me.

Let me know how you go!

LM[/QUOTE]

that is not a solution for me... 

i did setup automatic login on the server for local (gdm) AND remote (gdm/xdmcp) connections,

so that the old machines running a minimal slackware install connected to the server open a gnome session automatically when switched on, using a 'guest' account, using "X -query <ip> &" in /etc/rc.d/rc.local

I want everybody able to see the right icons in nautilus ! (the first connected see the right icons, other ones see only the 'unknown document' icon everywhere in nautilus (desktop and file browser)

It works on my Fedora Core 3 installation, so it should be working in Ubuntoo..

HELP !

---

### Post by bobcam on 2006-01-14
Hello

I have encountered the same problem with icons using freenx+breezy as server and nomachine client on XP.

Starting gnome-settings-daemon on the client works well but after that, there is no way to start openoffice on the server AND on the client ?

Any idea, solution, advice would be very apppreciated

Laurent

---

