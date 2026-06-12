---
title: "Getting Visual Effects to work on HP Laptop with ATI radeon xpress 200M graphics card"
date: 2008-02-01
forum: Desktop Effects &amp; Customization
---

### Post by AbuMustafa on 2008-02-01
hey guys, complete ubuntu n00b here. this is my 3rd day to be running ubuntu, and so far i love every bit of it, however, i am having a bit of difficulty enabling visual effects on my system.

im running a HP Pavillion dv5215us laptop. I have an ATI Radeon Express 200M graphics card (128 mb dedicated) and 1 gb of RAM.

i installed my graphics card through restricted drivers manager and everything runs great, but when i go to "system > prefrences > appearance" and then go to "visual effects" and try to enable them, i get a message that says: "The Composite extension is not available"

Again, I am a COMPLETE ubuntu (and linux) noob. any help would be greatly apprecaited.

thank you guys

---

### Post by Condoulo on 2008-02-01
hello, 
Ok, it is a very simple command. Just do a "sudo apt-get install xserver-xgl" 
Though it will probably not be the best performance wise after using it for a while, but it will allow you to get 3D effects.
Anyway, hope you enjoy
~ Condoulo

---

### Post by Earl_Maroon on 2008-02-01
I had the same problem when I first installed Ubuntu on my laptop (same graphics card). I can't remember exactly what I did to fix it though. I do remember this though - the first time I installed Ubuntu I had a lot of problems for no apparent reason. I reinstalled and things seemed to work (though I had to set up a few things). I can't remember if that was what sorted being able to use desktop effects though. I definitely remember that one thing I had to do was change xorg.conf (/etc/X11/xorg.conf) so it showed the correct resolution for my screen under the line SubSection Display (in my case: Modes		"1280x800"). You will need to sudo gedit it. I don't know if this helps.

---

### Post by coskierken on 2008-02-02
Here is what I have recently found through research and trial/error.  With the latest release of ATI 8.01, you no longer need xserver.xgl!  If your video card is supported, I would use Envy to load the driver.  It worked great for me (Core2Duo T7200 ATI X1700 mobility)  Video playback is still not working when Compiz is activated, so you have to change it to no effects when you want to watch a movie.  Compiz Switch is great for this, but not needed.  Also, in Synaptic is a GL Gnome manager.  I could not use it as when active, it corrupted my Compiz files (not sure which one) and some functions would not work correctly.  Emerald works nicely with Compiz.  Except for video, ATI has made some good improvements for my system with its new drivers.  Now, if they just get the video fixed, all would be good!:)
     With the new driver, many people are not able to log out or shutdown properly.  Here is the link which gives a fix and explains it.  Enjoy.

[http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23](http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23)

---

