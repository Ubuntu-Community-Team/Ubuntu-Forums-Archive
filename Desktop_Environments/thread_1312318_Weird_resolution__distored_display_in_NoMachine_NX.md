---
title: "Weird resolution / distored display in NoMachine NX Usage"
date: 2009-11-03
forum: Desktop Environments
---

### Post by pwyll72 on 2009-11-03
This is a continuation of this thread: [http://ubuntuforums.org/showthread.php?t=215924](http://ubuntuforums.org/showthread.php?t=215924)

original text copypasta:

"I have NoMachine NX server installed on my HTPC and connect to it regularly from work in order to configure things and just generally mess around. In the windows NoMachine client I've set up the connection so that the window uses "Available Area" as the resolution upon connection.

The work computer has a resolution of 1280x1024. What happens is that when I connect, the connection window uses up the full available are but creates a black border around a 1024x768 are in the middle which actually has the screen contents of the HTPC.

This problem does not occur when I connect using the same client to my other linux rig at home. In that case the connection adapts the resolution of the remote computer to fill the screen of the client computer.

Has anyone had this problem before? I suspect the reason is that it has something to do with the ATI driver settings over on the HTPC. My other rig has Nvidia and I don't get this problem."

I had had a similar problem; my work PC is dual-monitor and the display at home was showing the entire 2 screens worth of resolution squished/squashed/compressed/distorted into one screen size.

The detail for the fix is in the comments here: [http://www.opensourcetutor.com/2007/06/21/nomachine-nx-desktop-sharing-shadowing-now-available/](http://www.opensourcetutor.com/2007/06/21/nomachine-nx-desktop-sharing-shadowing-now-available/)

...and it boils down to 2 commands: Ctrl-Alt-L to activate "viewport" mode (which also seemed to have the side effect of locking the session on the local machine, so I had to unlock it immediately afterwards), and Ctrl-Alt-mousedrag to move around in the viewport.

Hope this helps!

---

