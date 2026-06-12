---
title: "Tiny, unreadable fonts"
date: 2007-10-21
forum: Desktop Environments
---

### Post by kooldino on 2007-10-21
I have my Kubuntu machine hooked up to my 42" LCD TV.  I run it in 800x600.

Whenever I got to the graphical login screen, the text on the screen was always so tiny that it was unreadable even on a screen of that size.

Once I logged in, the fonts were normal.

However, I've been playing around trying to get compiz to run on the machine.  At one point at the login screen, I typed the wrong password, and it wouldn't allow me to retype it for some reason (I wish I knew what the reason was, but I couldn't read the error message), so I did a CTRL+ALT+BACKSPACE to restart the X server.

Now, after I login, all of the text is the same tiny, unreadable text.  To top that off, when I go to shutdown from the K Menu, I ONLY have the "logout" option anymore.  So to kill the machine, I have to do it via the command line.

How can I fix this?

---

### Post by Nero_Flint on 2007-10-21
Type in the wrong password during the login again....this time try and see what the error message is (I know that they pass quickly). I think that will be the key to getting the help you need.

---

### Post by kooldino on 2007-10-21
The error message doesn't disappear quickly...it's written in red text and stays on the screen.

The problem is that the font is about 2 pixels tall, and there's no way to read it.

---

### Post by kooldino on 2007-10-21
Still can't figure this out...I can't do anything with this machine until this is solved.

:(

---

### Post by else on 2007-10-22
I think you may have caused the x server to start in safe mode.  change your login session to gnome default and login.  when you logout i think it will be back to normal.  something similar happened to me and after some stuffing around i think that is what fixed it.

---

### Post by kooldino on 2007-10-22
I don't have gnome installed. :(

---

### Post by kooldino on 2007-10-22
> **else said:**
> I think you may have caused the x server to start in safe mode. 

Also, why would "safe mode" have tiny fonts?

---

### Post by ToastyX on 2007-10-22
This sounds like a DPI issue. If you're using the binary NVIDIA driver, it will try to figure out the DPI of your display based on the DDC information and the current resolution, and text will be sized accordingly. 800x600 on a 42" display results in a low DPI, which results in small text. To fix this, you can manually set the DPI to a more sane value.

If you're using the binary NVIDIA driver, edit /etc/X11/xorg.conf, go down to the section that has Driver "nvidia", and add this line:

Option "DPI" "96x96"

Then restart the X server.

---

### Post by kooldino on 2007-10-22
I'll try that as soon as I get home this evening.  Thanks!

---

### Post by kooldino on 2007-10-22
Ok, that more or less did the trick.

I put 96x96 in the file, and it got me back to KDE with a legible font size.

From there, I adjusted all of my fonts, but found that certain ones just wouldn't look right no matter what I did.  For instance, to make the KDE menu fonts look normal, it required a rather large font size (14 or so) which coincidentally was the same font setting for menu bars, which ended up looking relatively gigantic.

So in the appearance area under the system settings in KDE, I disabled "force font DPI".  I was able to configure everything back to normal...with the exception of Firefox, where everything (menus included) look small, however they are readable up close (they're probably an ~8 point font).  

I wish I could get it back to how it was, but either way, this is a good start.

Also, despite the settings that I specify in the system settings, my only listed option on the KDE Log Out menu is "log out".  There is no shutdown or restart option.

Also, since all of this went awry in the first place, after I login and the desktop is loading, the cursor will turn into an "X" in the middle of the screen, and the screen will redraw itself a few times before it starts drawing the KDE login screen.  I don't particularly care about this, but I figured I'd mention it just in case it was a sign of something.

So anyway, that's where I am now.  All seems well except fore firefox and my logout options are all but gone.

---

