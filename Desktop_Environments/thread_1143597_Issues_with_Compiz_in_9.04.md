---
title: "Issues with Compiz in 9.04"
date: 2009-04-30
forum: Desktop Environments
---

### Post by CaptainEvilStomper on 2009-04-30
I'm having trouble figuring out why I'm having these weird issues logging in and logging out since I upgraded to 9.04. When I log in I get a black screen with nothing but my top panel showing, and after about 10 or 15 seconds Compiz starts up, my wallpaper appears, and AWN starts. Then when I log out an error message pops up just before my desktop disappears and the login screen comes up. I never have time to read the whole thing before it disappears, but I've managed to catch the words "Compiz" and "isn't compositing." There are also other weird glitches that happen occasionally when logging in, like one or more of my Screenlets camping out the desktop until I hit F9 for the first time, even though I have them set to stay in the widgets layer.

I thought maybe it was AWN that was causing all this so I unchecked it from my Startup Applications. Logging in is a little faster (I only get about 6 seconds of the black screen) and the error message hasn't showed up, but I'm still getting a few random glitches, and when I run "compiz --replace &" from the Terminal I get the following error message:

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

I was hoping someone here could explain to me what that means and what I could try that might fix it. As far as I know everything still technically works, so it's not a huge problem, but it is fairly annoying and I'd like to get it back to normal again if possible.

---

### Post by Efros on 2009-04-30
I too was experiencing some serious weirdness with compiz and AWN. I seem to have resolved it by putting some commands in the Startup Applications settings (previously Sessions). 

compiz --replace

bash -c "sleep 20; avant-window-navigator"

bash -c "sleep 5; fusion-icon"

bash -c "sleep 9; compiz"

The sleep command is there to try and get things to be executed in some kind of order, which is what the problem is I believe. Some of these may be redundant, but at least now after 30secs my dock is loaded and everything is hunky dory in the world of compiz. If you use conky you will have to use this command also

bash -c "sleep 30; conky"

---

### Post by demi_3399 on 2009-05-02
Thanks alot been searchin for some while now...the start up commands actually work once again thanks

---

### Post by t_floyd on 2009-05-04
Can you please explain a little bit more in details what you have done to make compiz working in a smoother way at log-in? Me too i'm experiencing the same start-up issues (black screen disappearing after 30 seconds), but i could not get what you have done to the system start-up file. Which file did you edit?

Thanks!

---

### Post by CaptainEvilStomper on 2009-05-05
@Efros: Thanks for the advice but I ended up ditching AWN and replacing it with Gnome-Do & Docky. I've never heard of the sleep command before now, though - good to know.

@t_floyd: Go to System > Preferences > Startup Applications (or hit Alt-F2, type gnome-session-properties, and hit enter). Services with a check in the box next to them will start when you logged in; unchecked ones won't.

BTW, I was also having weird issues where the Logout and Shutdown menus were't coming up if another window was in focus - I had to go into the Focus & Raise Behavior settings under General Options and set the Focus Prevention Level to off. I still haven't figured out the weird login delay/black screen issues but I think it's more an issue with Ubuntu than Compiz - I had the same problems in a virtual machine running Jaunty in VirtualBox, both with Compiz enabled and disabled.

---

