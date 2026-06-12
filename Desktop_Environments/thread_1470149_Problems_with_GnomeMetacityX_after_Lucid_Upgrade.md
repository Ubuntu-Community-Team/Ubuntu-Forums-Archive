---
title: "Problems with Gnome/Metacity/X after Lucid Upgrade"
date: 2010-05-02
forum: Desktop Environments
---

### Post by azmanam on 2010-05-02
System:

Gateway box
P4 3GHz processor
1 GB RAM
one 40 GB Western Digital IDE Hard drive
one 500 GB Western Digital IDE Hard drive
NVidia-GeForce FX 5200 DDR 128MB Video Card
Hauppauge HVR-1600 Tuner Card (with accompanying remote of unknown model #)
Creative Sound Blaster X-Fi Card

---------------

Ran Lucid upgrade on a mythbuntu box on Friday.  On startup, though, the desktop looked quite odd - in fact, I didn't even know it was my desktop at first.  It was a small white terminal 'window' in the upper left corner of a black screen.  My mouse was responsive, because I had to mouse over the 'window' before I could type.  I say 'window' because it had no toolbar, and I couldn't move, resize, or close it.  No top or bottom panels on Gnome.  Like I said, it was so unrecognizable I didn't initially think it was my desktop.  I assumed it was nvidia drivers, and spent a long time making sure they were installed - they do not seem to be the problem.

After searching forums/internets, found several pages telling people to rename/move/delete .gnome, .gnome2, etc and gnome should revert to default.  Problem persists.  I can open gedit or firefox by running from command line, but when I close those windows, the image of those windows remain as part of the background.

Next, I found several pages telling people to run gnome-panel from terminal.  *Lucid upgrade did not install gnome-panel by default, and I had to install it from aptitude.*  After installing it, I can run it from terminal.  The top and bottom panels return, but I get a series of error messages in the terminal window:

```
~$: gnome-panel

(gnome-panel:2459): GVFS-RemoteVolumeMonitor-WARNING **: 
invoking IsSupported() failed for remote monitor with dous name 
org.gtk.Private.GduVolumeMonitor: 
org.freedesktop.DBus.Error.noReply: Did not receive a reply.  
Possible causes include: the remote application did not send a 
reply, the message bus security policy blocked the reply, the 
reply timeout expired, or the network connection was broken.
** Message: Could not connect to session manager: Could not get 
owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2459): WARNING **: Could not connect to session 
manager: Could not get owner of name 'org.gnome.SessionManager':
no such name
```

additionally, after those messages, I DO NOT get a command prompt back.  Pressing arrows or home, end, etc display ^[[B^[[A, etc.  I have to ctrl+alt+F1 to a command prompt.

Then I saw a lot of pages telling people to run metacity from terminal:

```
~$ metacity
Window manager error: Unable to open X display

~$ metacity --replace
Window manager error: Unable to open X display

~$ DISPLAY=:0 metacity --replace &
Window manager warning: Failed to load theme "Clearlooks": 
Failed to find a vaild file for theme Clearlooks

[  357.726227] end_request: I/O error, dev fd0, sector 0
[  357.834355] end_request: I/O error, dev fd0, sector 0
```

... and it hung for ~ 45 seconds between I/O errors

Now, the good news is I can run mythfrontend from terminal, and the DVR part of my computer works without problem.  so the computer technically does what it is supposed to, but I'd like to have my desktop back, too.

---

### Post by azmanam on 2010-05-02
Interestingly, if I run metactiy from gnome terminal BEFORE I run gnome-panel, the window toolbar comes back (but it looks box-y and old fashion-y).  Error message reads:

```
~$ metacity
Window manager warning: Failed to load tehem "Clearlooks":
Failed to find a valid file for theme Clearlooks
```

then it hangs and I don't get a command prompt back

I also noticed in aptitude that compiz is not installed.  Does it need to be?

---

### Post by dave_blob on 2010-05-03
I just experienced a very similar problem - upgraded to lucid, white box, unresponsive.
ctrl-alt-1 to terminal, then `top` shows gnome-panel at 100% cpu.

I fixed it though :)

rm ~/.gconf/apps/panel   (deletes your panel config, resetting it to default)
pkill gnome-panel

reboot/restart session.

All good! 
I think it may have something to do with the gnome-do launcher i had in my panel, at a guess.

---

### Post by xtralargekeg on 2010-05-19
I have been having the same problems. I upgraded to Lucid Ubuntu 10.04 but nothing will happen in the desktop screen. I am able to login but i might get the Background. but most of the time it is just the blank top panel. 
 
I tried all but nothing.

---

### Post by borkabrak on 2010-08-12
I'm having this issue as well.  After upgrading, I get strange behavior from any flavor of gnome while logging in.

A regular gnome session shows me the new purple background and hangs the entire computer.  In synaptic, I found that gnome wasn't even installed.  After installing it (an adventure in itself), I find that it still doesn't work -- I get the login sound and then I get kicked back to the login screen.

This is frustrating, and I'm disappointed to see that three months have gone by without an answer to the OP.  This obviously happens to people; where do I find a solution?

---

