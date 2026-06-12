---
title: "Gnome Panel (aka the Taskbar) Disappers"
date: 2008-07-16
forum: Desktop Environments
---

### Post by mattdee on 2008-07-16
Hey All,
I just wanted to document a fix for a problem the newbies to GNOME can face...

The problem is that the GNOME Panel (aka the Taskbar) disappears and you can't or don't know how to get it back...

Here's the fix or at least the one that works for me!

Hopefully you have a launcher on your desktop for the GNOME-terminal.

Click it and run the command 'gnome-panel' in the background like so:
gnome-panel &

If it tells ya you don't have gnome-panel installed...go ahead and install it like so:
sudo apt-get install gnome-panel

Once installed, rerun the gnome-panel command like so:
gnome-panel &

With any luck all your old settings will still be there...

Cheers,
Matt D

---

### Post by quackquack on 2008-07-16
i've never had this problem, how do you get it?

if you don't have a terminal shortcut on your desktop you could use Alt-F2 and type "gnome-terminal" and press run xD

... or, you could just press alt-f2 and type "gnome-panel" without opening a terminal. 

Also, alot of other problems with the taskbar can be fixed with a "killall gnome-panel" command to reset them.

:)

---

### Post by mattdee on 2008-07-17
You can make it happen by deleting all you taskbars (aka panels).

My problem happened one day when I logged in and no taskbars.

I tried alt-f2 but it didn't work...I think that's because that function is tied to the gnome-panel.

Give it a shot and see if you can make it happen and test the solution.

I posted it because I didn't see any solutions out there on the intertubes...

---

### Post by quackquack on 2008-07-17
ah, i see. well then if this happens and you dont have a terminal icon, you could right click the desktop, click create launcher and under command type "gnome-terminal" and give it whatever name ("Terminal" would be good lol) and click ok. That way if it happens and you dont have a terminal icon on your desktop you don't need to panic hehe.

how do you delete all panels? it wont let me delete both panels, if i only have one left, the delete option is shaded out on the remaining panel. :S

---

### Post by Koroush on 2008-07-17
So, this just happened to me today and I'm searching for an answer.  Unfortunately, I have no idea what I did or how I did it, my best guess is that when I was trying to fix my wireless yesterday I managed to screw something else up.  At any rate, I don't have a launcher for the terminal on my desktop and alt-2 does not work.  So, I need advice.  asap... got work to be doing...

BTW: for some godforsaken reason, right clicking to create a launcher isn't working either, it doesn't respond, nothing comes up.

Update: Never-mind, I remembered that you can find things to 'run in terminal' so I did that.  None of my applets work anymore though, any advice?

---

### Post by quackquack on 2008-07-17
have you tried "killall gnome-panel" to reset the panels?

if that doesnt work, type this in terminal:

"sudo rm -rf ~/.gnome ~/.gnome2 ~/.gconf ~/.gconfd" 

and press Ctrl+Alt+Backspace and log back in.

this should delete folders containing certain settings and force gnome to recreate the files you deleted, replacing the settings back to defaults. this should fix the panels, but you may lose any customised menu settings and things like that.

it wont delete any documents, pictures or anything else other than configuration files which will be recreated as soon as you log in.

if that STILL doesn't work, you can try Alt+F2 and type "gconf-editor" in the box and press ok. in the window that opens, navigate to apps, panel and reset all the keys by going to each folder in the "panel" directory and right clicking on each one and clicking Unset key to reset them to their original values. Especcially delete all the keys in the folders like that have "applet" in thier name then log out and back in.  I havent tried this myself though, but i saw somewhere that it worked (can't remember where lol)



Hope this helps :D

---

