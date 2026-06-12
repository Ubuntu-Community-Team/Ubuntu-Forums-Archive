---
title: "tsclient - move full-screen to another workspace?"
date: 2008-09-27
forum: Desktop Environments
---

### Post by kacheng on 2008-09-27
Hi,
I'm having some problems with tsclient in fullscreen mode.  I'm connecting to my Windows computer at work which uses Terminal Services/RDP.

1. Can't seem to find a way to minimize the remote session.  

[PART 1 SOLVED] 
A. If you are running visual effects (Compiz) y. If you double-click the tsclient taskbar item now, you can minimize tsclient.

Is there a better way?ou need to install Advanced Desktop Effects Settings Manager (CompizConfig Settings Manager) from Add/Remove Applications.  Go to Utilities|Workarounds and DISABLE Legacy Fullscreen support
B. Ctrl-Alt-Enter now toggles the screen to show the ubuntu toolbars.  Now quite minimizing, but at least gets you back to ubuntu without having to disconnect and reconnect. If you double-click the tsclient taskbar item now, you can minimize tsclient.

Is there a better way?


2. Can't resize the windowed remote session.  It stays the same size, and doesn't scroll, making it difficult to navigate to the edges of the screen which are just off the edge of my screen.  The only choices on the tsclient options are 640x480 (way too small), 800x600 (too small), 1024x768 (full screen), and greater.  Any way to run a 1024x700 window or something like that?


3. Can't seem to move the remote session to another workspace.  I would love to be able to move the remote session in full screen to a separate workspace and be able to switch from desktop to desktop using Ctrl-Alt-Left/Right Arrows.  I can't explain how awesome that would be!

---

### Post by Offoffoff on 2008-11-05
That is funny to say, but in Intrepid I have absolutely the same problem. I lose my compiz hot keys settings after I have updated my Gutsy. Now I can not get out from tsclient session with familiar hot keys (ctrl+alt+left, ctrl+alt+right). And ctrl+alt+enter does not really work, I have to push that combination two or three times to get compiz environment. What am I have to do with? In the past I had three remote session on the cube sides and it was really useful and fun.

---

### Post by tonyalbers on 2008-11-05
> **kacheng said:**
> Hi,
I'm having some problems with tsclient in fullscreen mode.  I'm connecting to my Windows computer at work which uses Terminal Services/RDP.

1. Can't seem to find a way to minimize the remote session.  

[PART 1 SOLVED] 
A. If you are running visual effects (Compiz) y. If you double-click the tsclient taskbar item now, you can minimize tsclient.

Is there a better way?ou need to install Advanced Desktop Effects Settings Manager (CompizConfig Settings Manager) from Add/Remove Applications.  Go to Utilities|Workarounds and DISABLE Legacy Fullscreen support
B. Ctrl-Alt-Enter now toggles the screen to show the ubuntu toolbars.  Now quite minimizing, but at least gets you back to ubuntu without having to disconnect and reconnect. If you double-click the tsclient taskbar item now, you can minimize tsclient.

Is there a better way?


2. Can't resize the windowed remote session.  It stays the same size, and doesn't scroll, making it difficult to navigate to the edges of the screen which are just off the edge of my screen.  The only choices on the tsclient options are 640x480 (way too small), 800x600 (too small), 1024x768 (full screen), and greater.  Any way to run a 1024x700 window or something like that?


3. Can't seem to move the remote session to another workspace.  I would love to be able to move the remote session in full screen to a separate workspace and be able to switch from desktop to desktop using Ctrl-Alt-Left/Right Arrows.  I can't explain how awesome that would be!

You can save a connection and then edit the .rdp file and change desktopheight and desktopwidth to match what you need. Actually you can change a lot of things in here. 
You can move the window to another workspace by right-clicking on it in the taskbar and choose which workspace to move it to. Works fine here.

---

