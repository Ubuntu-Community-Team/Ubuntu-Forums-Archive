---
title: "Splash Screen Background Color?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by kLOTTiS on 2006-09-24
How can I change the background color of the splash screen that is normally brown, my whole setup is skinned white/silver but that stays brown :(  and also selected dropdown adress box in firefox, Does anyone know how to change these? Any help will be greatly apreciated

---

### Post by kitpierce on 2006-10-01
I was wondering this as well.  I have stumbled upon a walkthrough that mentions the usplash configuration, but typing **sudo usplash** in the terminal did nothing so far as I could tell.

Is there a graphical tool for picking the color of the splash screen much like there is for setting the splash image itself?  Thanks!

---

### Post by kitpierce on 2006-10-01
Found it - although this seems to be in an odd place.  Go to System... Administration... Login Window there will be a box for background color.  Changing that color had the desired effect not only on the login window but behind the splash screen as well.

---

### Post by nick.inspiron6400 on 2007-07-28
Thanks!

---

### Post by skrimpy on 2007-12-10
thank you! exactly what I needed :D

---

### Post by ColdFusionEESG on 2007-12-14
> **kitpierce said:**
> Found it - although this seems to be in an odd place.  Go to System... Administration... Login Window there will be a box for background color.  Changing that color had the desired effect not only on the login window but behind the splash screen as well.

Did that weeks ago, but only changed the login window BG for me?? :-(

Now I should mention that the Ubuntu logo with the horizontal bar that zips back and forth like a Cylon eye only ever showed while booting when I used the Live CD....never once installed.

So I see a black screen for about 50 seconds....then my themed login window...then a splash screen with a small image I selected in the middle with the default Ubuntu baby puke brown as a background.

any ideas?

I may have to dig into that USplash stuff

Cheers

---

### Post by johnbl on 2007-12-14
Maybe you need to update to Gutsy and see then what happens. Gutsy solved lots of niggling problems I was having.

---

### Post by ColdFusionEESG on 2007-12-14
> **johnbl said:**
> Maybe you need to update to Gutsy and see then what happens. Gutsy solved lots of niggling problems I was having.

Ooops...sorry I should have mentioned I'm on Gutsy already ;-)

---

### Post by johnbl on 2007-12-18
If hit User Cp you can edit your profile to reveal your version et al. Helps..

---

### Post by danwood76 on 2007-12-18
> **ColdFusionEESG said:**
> 
So I see a black screen for about 50 seconds....then my themed login window...then a splash screen with a small image I selected in the middle with the default Ubuntu baby puke brown as a background.


Edit the /etc/usplash.conf file to the correct screen resolution will show the splash screen.
I had this issue when installing gutsy, it defaults to 1280x1024 when it cant work out the screen resolution, mine was on a widescreen laptop.

Make the file look like this:

# Usplash configuration file
xres=1024
yres=768

this worked on my laptop with a resolution of 1280x800
you should then see the usplash on startup and shutdown

regards,
Danny

---

### Post by ColdFusionEESG on 2007-12-18
Hey Danny,

Thanks for the tip.

I too have a laptop with 1280x800 resolution and the usplash.conf file was in fact set the way you mentioned.

I did see the usplash screen on shutdown (not restart), but nothing at all at start up (still the black screen for about 50 seconds.....then my themed login window....then another "splash screen" which I added an image to using Gnome Art Manager...still has the Ubuntu brown BG though).

Baby steps!! ;-)

Cheers

---

### Post by danwood76 on 2007-12-18
well you could try the natural resolution of 1280 x 800, this actually didnt work for me but I have an ATI graphics card in this lappy and it made it play up for some reason.

My splash screen looks a little squashed :)

---

### Post by ColdFusionEESG on 2007-12-18
Gave the native res a shot....no change...still just on shutdown.

Now something about all this has me confused....so bear with me while I tell my story ;-)

I use Gnome Art Manager to dload artwork.  For all types of artwork EXCEPT splash screens, the install button is activated and I can directly install things like login window themes.  For splash screen themes I have to dload the files and then fire up System>>Preferences>>Splash Screen and then install the dloaded files.....select an installed theme and activate it.

So that changes what I see AFTER logging in.  It's called a Splash Screen.

Now there is the usplash.conf file we've just chatted about.....it also seems to be called a  "spalsh screen"

Now you can see my confusion....which one is truly the splash screen.  Based on System>>Preferences>>Splash Screen i'd have to say it's what you see AFTER logging in.

All this probably doesn't help debugging this stuff ;-)

Are there other ways than Gnome Art Manager to get this stuff in place??

TIA

Cheers

---

### Post by danwood76 on 2007-12-18
I think the difference is that the usplash.conf refers to the ubuntu splash screen, whereas the one you get through the menu is actually the GNOME splash screen.

usplash.conf = ubuntu splash config

You could try a really low res like VGA (640x480) that will be the native resolution the system will first boot up in, I think grub is VGA resolution correct me if im wrong.

regards,
Danny

---

### Post by ColdFusionEESG on 2008-01-03
Just a quick update....the latest kernel (.47) fixed up the Ubuntu Splash screens....now seen on boot up...shutdown, and restart.

---

