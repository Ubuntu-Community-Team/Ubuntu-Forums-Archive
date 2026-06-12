---
title: "Can't run Compiz!!"
date: 2009-11-08
forum: Desktop Environments
---

### Post by XProflmfao on 2009-11-08
Hey everyone,
   
So I heard about this program called Compiz that can change your desktop environment into cool animations and whatnot, so I decided to use it. After finding out on the software manager on Ubuntu that Compiz is preloaded to my computer, I went on the Ubuntu wiki and it told me to run Compiz by typing this command in the terminal:
[FONT=Courier New]
compiz --replace[/FONT]

After that, it looks like it starts running, my wallpaper pops up from beneath my windows, but then in the end everything just goes back to my old desktop. Then when I check my terminal, I get this:

[FONT=Courier New]Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png[/FONT]

I'm not sure what this really means, but it does say something about Xgl and nVidia not present. I would like to use Compiz because it sounds like it has a lot of eye candy and animation, which I LOVE!!!!

Note: the part where it says: "WARNING: Aplication calling GLX...." and all the text afterwards only pops up after my desktop clears itself into my wallpaper. I think that's the part where everything gets messed up and Compiz can't start.

More info: I'm using the latest version of Ubuntu, Karmic Koala 9.10.

Thanks beforehand for any useful info! But before then, I'm just going to stick with good ol' Ubuntu desktop!

---

### Post by XProflmfao on 2009-11-14
Anyone? I still can't use Compiz...

---

### Post by andrea000 on 2009-11-14
run compiz in the terminal and post the output

applications->accessories->terminal

> compiz
you may also want to use compiz check the link
is at the bottom of this post

---

### Post by XProflmfao on 2009-11-16
> **andrea000 said:**
> run compiz in the terminal and post the output

applications->accessories->terminal


you may also want to use compiz check the link
is at the bottom of this post

Like I said, just running compiz won't work. I tried just pressing the program on applications, did alt+F2 and tried to run it, terminal too, nothing works, everything is the same. Also, the only reason I posted all those mumbo jumbo "WARNING!" stuff on top in Courier New font was because I ran "compiz" on the terminal.

---

### Post by XProflmfao on 2009-11-16
Since no one is willing to help me on this problem, I guess I can make do without Compiz. What a shame I never even got to try out Compiz and see if I liked it...

---

### Post by darshana on 2009-11-16
Did u installed the VGA card drivers?. If im not mistaken Compiz need Open GL drivers

---

### Post by Haribda on 2009-11-17
I'm having the same problem. Can anyone tell us how to do it? I'm on 9.04 still

---

### Post by Haribda on 2009-11-17
Here's my output when i write compiz in terminal.

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by stinkeye on 2009-11-17
Youtube video:
[_[COLOR="DarkRed"]Enable Compiz Fusion & Desktop Cube[/COLOR]_]("http://www.youtube.com/watch?v=Shs1brD2pdU")
Go to this guys channel. he has lots of ubuntu howto's.

---

