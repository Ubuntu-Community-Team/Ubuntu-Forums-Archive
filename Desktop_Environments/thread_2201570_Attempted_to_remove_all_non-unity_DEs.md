---
title: "Attempted to remove all non-unity DEs"
date: 2014-01-24
forum: Desktop Environments
---

### Post by ztypomerleau on 2014-01-24
Well it started off as a search to return to the unity login screen from KDE Plasma, and I ended up installing Gnome. Attempting to remove that, all of my DEs are now gone and I essentially only boot to a terminal. How can I get only Unity back without having to find the disk?

---

### Post by deadflowr on 2014-01-24
From a terminal try
```
sudo apt-get update 
sudo apt-get install ubuntu-desktop
```
if it says ubuntu-desktop installed, try
```
sudo apt-get install --reinstall ubuntu-desktop
```
Tells us what happens next...

---

### Post by ztypomerleau on 2014-01-24
So far after the initial Ubuntu splash we have a black screen.
After the update and install I had rebooted. And no change while writing this.

---

### Post by ztypomerleau on 2014-01-24
Update: I hit the power button on the black screen and then the splash shows back up for maybe 2 seconds then shuts off. Going to leave it alone for awhile and see what happens. May just have to burn a new CD.

---

### Post by RadicaX on 2014-01-25
Can you not type in this blackscreen at all?

---

### Post by ztypomerleau on 2014-01-25
No, it's a state of nothing. The screen is physically off, and the computer is still on the Ubuntu splash. There is no way  to reactivate the screen without the laptop subsequently shutting down.

---

### Post by RadicaX on 2014-01-25
Ick, if you can not type in commands, there is not much one can do. Looks like you will have to reinstall, if you need to, run a livecd/usb and go into that, it would be a good time now to save any pictures/files you need with another usb. 

I would imagine it would be possible to see what went wrong from there too. It sounds like some key packages were corrupted or something in the start up phase, and that is why it freezes there. 

You can of course wait and see if deadflowr will send another reply with advice, they tend to be able to do a lot with these things, and have a much deeper insight into the workings of it. 

My question though, if the screen is physically off, how can you tell it is on the splash? Do you mean after turning it on, in a few moments it goes off?

---

### Post by Bucky Ball on 2014-01-25
I know this might sound obvious, but have you done a thorough check of your monitor cable to make sure it is in nice and snug both ends?

---

### Post by deadflowr on 2014-01-25
I wonder if you didn't delete the xserver package(remove them, I mean)

You can try this real quick
press ctrl + alt + F1(or F2-6)
This should give you a console, login and first try
```
startx
```
this usually will load the xsession.
or try
```
sudo service lightdm restart
```
if on 12.04
or
```
sudo restart lightdm
```
if on a different version.

Does anything happen, if no what did the screen say.

---

### Post by ztypomerleau on 2014-01-25
deadflowr you rock. After using the startx command we now have it further loaded. Although now we are stuck with the background and mouse cursor. Now I don't want to screw anything up again so I'll wait for your help again.

---

### Post by ztypomerleau on 2014-01-25
Bucky, I know what I had previously posted sounded like it could have been something as simple as that, but that is a problem that less intelligent users face. Given I am using Linux, albeit am still rather new, we can assume we are all smarter than the average user to get caught on something such as a cable becoming loose ;)

---

### Post by deadflowr on 2014-01-25
Not really sure on what the next step should be, but if you have the mouse and a background, unity might not be loading.
You can try and reset unity.(this should bring unity back to it's original state)
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

Not really sure about the splash screen hanging, the startx, et al, commands I posted were simply to see if you could run X.
Seems you can, which is at least somewhat positive news.

Something you might try would be
```
sudo dpkg-reconfigure lightdm
```
you could also try [reinstalling/resetting plymouth]("http://askubuntu.com/questions/157349/how-can-i-restore-my-boot-screen-in-ubuntu-12-04"), though I'm not sure that'll help.

It's hard to figure out without knowing what packages were uninstalled.
Ubuntu, for all the talk about unity, is basically a gnome desktop.
Removing gnome packages, can do a fair amount of damage, which you now can attest to.
On top of which, you also mentioned kde, which again adds another layer of craziness.
But it might just be simply things...

---

### Post by ztypomerleau on 2014-01-25
Ah, well at least there isn't anything irreplaceable on there. Going to switch this to resolved and walk away with a valuable lesson learned.

---

