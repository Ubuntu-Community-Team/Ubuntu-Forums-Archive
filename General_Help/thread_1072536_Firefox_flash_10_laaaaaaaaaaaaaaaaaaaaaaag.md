---
title: "Firefox flash 10 laaaaaaaaaaaaaaaaaaaaaaag"
date: 2009-02-17
forum: General Help
---

### Post by crazyfuturamanoob on 2009-02-17
I installed flash10 on my Ubuntu 8.10 64bit and it makes some serious laag. 

And its not about connection speed or GHz.

---

### Post by Thelasko on 2009-02-17
Is it the 64-bit flash beta or the 32-bit flash from the repositories?  Does it always do this, or only in full screen?

---

### Post by crazyfuturamanoob on 2009-02-17
I don't remember I manually installed it because installer didn't want to.

---

### Post by Thelasko on 2009-02-17
> **crazyfuturamanoob said:**
> I don't remember I manually installed it because installer didn't want to.

Please explain, step by step, how you installed it.

---

### Post by crazyfuturamanoob on 2009-02-17
Moved libflashplayer.so to ~/.mozilla/plugins. 

Its been a while since I did it, can't remember if I enabled something from any config files, probably not.

---

### Post by stchman on 2009-02-17
> **crazyfuturamanoob said:**
> I installed flash10 on my Ubuntu 8.10 64bit and it makes some serious laag. 

And its not about connection speed or GHz.

Did you install the 64 bit version of Flash 10?  If no then follow my instructions here.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

The 64 bit works far better than the 32 bit using nspluginwrapper.

---

### Post by Thelasko on 2009-02-17
> **crazyfuturamanoob said:**
> Moved libflashplayer.so to ~/.mozilla/plugins. 

Its been a while since I did it, can't remember if I enabled something from any config files, probably not.

Did you download it from [here]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html")?

---

### Post by philinux on 2009-02-17
I've just downloaded and installed this latest alpha plugin, 10.0 d21, and it works a treat. I'm running 64 bit Jaunty.

Full screen on sky news is ok but not on some you tube stuff. Get serious lots of frames dropped.

---

### Post by crazyfuturamanoob on 2009-02-17
> **Thelasko said:**
> Did you download it from [here]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html")?

Very likely.

And I never use any flash things in fullscreen, just windowed ones laag.

---

### Post by philinux on 2009-02-17
Just tried the d20 flash and full screen you tube is bad. But works fine as well in normal screen size. 

What exactly is happening on your rig.

---

### Post by crazyfuturamanoob on 2009-02-17
Youtube works great. But almost all other flash applications laag.

I removed that libflashthing.so from .mozilla and installing nonfree with synaptic. No difference.

---

### Post by DeMus on 2009-02-17
> **stchman said:**
> Did you install the 64 bit version of Flash 10?  If no then follow my instructions here.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

The 64 bit works far better than the 32 bit using nspluginwrapper.

I followed the steps on this site but I'm not quite sure I have the 64 bits version. How to tell? 

In Firefox the about : plugins page tells me this:

Shockwave Flash
File name: npwrapper.libflashplayer.so
Shockwave Flash 10.0 r15
MIME Type 	                Description 	     Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

How to un-install this before I use your method?

---

### Post by Maheriano on 2009-02-17
> **philinux said:**
> Just tried the d20 flash and full screen you tube is bad. But works fine as well in normal screen size. 

What exactly is happening on your rig.

This is what happens to me. Is there a fix?

---

### Post by philinux on 2009-02-17
> **Maheriano said:**
> This is what happens to me. Is there a fix?

Thats in adobe hands. Lets hope there's a beta version soon.

---

### Post by DeMus on 2009-02-17
> **stchman said:**
> Did you install the 64 bit version of Flash 10?  If no then follow my instructions here.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

The 64 bit works far better than the 32 bit using nspluginwrapper.

I tried your way but I had no sound whatsoever. So I went back to my old version and things are back to normal.
Strange that what works for one does not work for another.

---

### Post by Cope57 on 2009-02-17
Is your video drivers up to date?
[NVIDIA drivers]("http://www.nvidia.com/Download/index.aspx?") | [ATI drivers]("http://ati.amd.com/support/driver.html")

[Download 64-bit Plugin for Linux]("http://labs.adobe.com/downloads/flashplayer10.html") (TAR.GZ, 3.54 MB)
**Important:** All users should uninstall any currently installed Flash Player before installing the latest prerelease.

Do you also have latest [Java Version 6 Update 12]("http://www.java.com/en/download/") | After installing Java, restart your browser and [verify Java has been installed correctly]("http://www.java.com/en/download/installed.jsp").

> **Linux 64-bit Alpha Release Notes**

These release notes document known issues related to the alpha versions of 64-bit Adobe® Flash® Player 10, code named "Astro". Release versions of 32-bit Flash Player 10 for Windows, Macintosh, and Linux platforms are now available from the [Flash Player Download Center]("http://www.adobe.com/go/getflashplayer").

The alpha refresh build of the 64-bit Flash Player 10 for Linux is version 10.0.d21.1.

Please **uninstall** any versions of Flash Player before updating your installation.

[LIST]
[*][Overview]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#overview")
[*][System Requirements]("http://www.adobe.com/products/flashplayer/systemreqs/index.html")
(512MB of RAM, 128MB of graphics memory) Here is the biggest reason most Linux users are having problems.
[*][Features and Enhancements]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#features")
[*][Installation]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install")
[*][**Known Issues**]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#known")[/LIST]


[System Requirements]("http://www.adobe.com/products/flashplayer/systemreqs/index.html")
(512MB of RAM, 128MB of graphics memory) *I have a four month old laptop that has 3Gb ram, but barely passes the graphics memory of 128MB.*
Older Linux desktop and laptops are having problems.

Also note that shared video memory does not count.

---

### Post by Thelasko on 2009-02-17
> **Cope57 said:**
> (512MB of RAM, 128MB of graphics memory) *I have a four month old laptop that has 3Gb ram, but barely passes the graphics memory of 128MB.*
Older Linux desktop and laptops are having problems.

Also note that shared video memory does not count.
Thanks for that info!  I use an integrated graphics card and have been having some issues.  This explains a lot.

---

### Post by stchman on 2009-02-18
> **DeMus said:**
> I followed the steps on this site but I'm not quite sure I have the 64 bits version. How to tell? 

In Firefox the about : plugins page tells me this:

Shockwave Flash
File name: npwrapper.libflashplayer.so
Shockwave Flash 10.0 r15
MIME Type 	                Description 	     Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

How to un-install this before I use your method?

If you used the method on my site the .tar.gz archive contains the 64 bit Flash.  I installed 64 bit Flash on all of my Hardy machines and it works very well.

---

### Post by crazyfuturamanoob on 2009-02-18
Re-re-re-installed flash once again from this site [http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

No difference in performance.

---

### Post by rasmus91 on 2009-02-21
> Did you install the 64 bit version of Flash 10? If no then follow my instructions here.

Thanks so much. (yeah, runs bad in full, but it ran even worse full in 32 bit)

---

### Post by bluedalek on 2009-02-22
I followed the directions that were listed at :

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

I can now watch all my NHL games in full screen, smooth playback!  I have not tried YouTube (rarely use it), but if the HD hockey feeds from atdhe.net work full screen, I see no reason YouTube won't work.

Derek

PC Specs:
Ubuntu 8.04 64bit
AMD X2 5000
3 GB PC5400 RAM
512MB nVidia geForce 8500

---

### Post by crazyfuturamanoob on 2009-02-23
> **bluedalek said:**
> I followed the directions that were listed at :

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

I can now watch all my NHL games in full screen, smooth playback!  I have not tried YouTube (rarely use it), but if the HD hockey feeds from atdhe.net work full screen, I see no reason YouTube won't work.

Derek

PC Specs:
Ubuntu 8.04 64bit
AMD X2 5000
3 GB PC5400 RAM
512MB nVidia geForce 8500

I installed flash with that but didn't help. Maybe flash 9 will work better?

---

### Post by Thelasko on 2009-02-23
I watched an episode of [Frontline]("http://pbs.org/frontline/") over the weekend, and it worked beautifully in full screen.  Although, I should note that moving my mouse did not reset the timer on the screen saver.  My screen saver turned on every 20 minutes whether I moved the mouse or not.

I think this full screen performance issue varies from one implementation to another.

---

### Post by crazyfuturamanoob on 2009-03-24
Yay I just realized I can play/watch any flash application with no laag by Firefox->File->Save Page As->Open the app.swf from the directory created with a good flash player of choice!

---

