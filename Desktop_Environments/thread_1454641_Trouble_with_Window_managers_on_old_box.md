---
title: "Trouble with Window managers on old box"
date: 2010-04-14
forum: Desktop Environments
---

### Post by kaldor on 2010-04-14
Using this old PC as a server, with only 96 MB RAM. I tried installing a basic WM today just in case I needed it, and only icewm will work. icewm works fine, no problems at all. I installed Xorg, etc. But every other WM I try has a problem. No use listing them, they all have an identical problem and I tried too many to describe.

Whenever I try a new WM, I remove the previous one to be careful. I then type "startx" to start the X session, but up comes a very buggy, static screen with a small terminal in the upper left corner. 

It's not my graphics card. It worked on Damn Small Linux on JWM and Fluxbox flawlessly, but I switched to Ubuntu Server because I just hated the way DSL worked. And like I said, icewm has no problems at all. I'm just curious about some others I could try, but not a single one works.

Ideas? :)

Edit: More info

I decided to reinstall another WM, and when the terminal came up I typed in the name of the WM (in this case, twm) and.. the terminal grew a window border. I could click on the desktop (still full of static) and bring the menus up, but it just wasn't usable at all. All other WMs were the same way, except they brought their own theme to it. Why is just icewm working?

---

### Post by atomizer on 2010-04-15
from [http://xwinman.org/basics.php]("http://xwinman.org/basics.php"):

>  There is a system configuration file that startx  uses, and a user's own configuration file that is used in preference to the system one, if it exists. You can find out the names of these files by looking at the startx  script. (You can find out where the script is by doing "which startx".) The system configuration file is usually something like /etc/X11/xinit/xinitrc and the user configuration file is virtually always .xinitrc  in the root of your home directory. Look at the system file and see where it calls the default window manager. To change window managers for yourself, either copy this file to ~/.xinitrc and edit it appropriately, or create your own from scratch. It should end with "exec windowmanager" and any commands before that which don't finish quickly should be run in the background. Here's a simple example:

     #!/bin/sh
     xterm &
     exec fvwm
	 

The first line selects the program used to run the script itself. Without this your default shell will be used. The second line runs an xterm in the background, and the third line runs the window manager. The exec command is used to replace the script process with the process of the window manager itself. This is because X shuts down when the script finishes running, but if the window manager replaces it, it will shut down when the window manager quits instead, which is usually the desired behaviour.

You can see this for yourself if you change the first line to "exec xterm". The window manager will then not be started and X will shut down when you exit the xterm window. This is also an interesting experience is it illustrates exactly what a window manager does, and what X does itself. Without a window manager running you can still run programs, and bring up windows, but they don't have any decorations and you can't move them. 

---

