---
title: "Ubuntu for my Grandma"
date: 2009-11-08
forum: Desktop Environments
---

### Post by KEBDARGE on 2009-11-08
Hey all!

I just installed Ubuntu 9.10 on my grandmothers laptop. She is switching from Windows XP because I didn't wanna spend a few hours repairing Windows everytime I visit her.

Now I want to dumb down this Ubuntu installation as much as possible so she will notice as less as possible from the fact she has a new OS.

The thing is, she only uses Skype and Firefox. That is it.

Now, how can I hide as many options in her user account as possible and restrict her privileges so much that she can perfectly and easily use those two programs and isn't bothered with any other clutter?

I was thinking myself about some kind of Kiosk-mode were she basically has two huge buttons on her screen for the two programs. 

Since I am a MacOSX user myself, I am not that goof in setting up Ubuntu. I am still pretty green behind the ears when it comes to tweaking Ubuntu.

Any help highly appreciated!

---

### Post by jward3010 on 2009-11-08
To put the icons on the desktop, go into the Applications Menu, right click on the icon and "Place on Desktop" or something. Right-click on that new Desktop icon and choose resize icon - stretch it out as big as it will go. Maybe you should make the top panel much bigger, so when the Skype icon ends up there, she will see it. Right click on the top panel, change panel properties, increase it's size.

Hope thats a little helpful.

JW

---

### Post by KEBDARGE on 2009-11-08
Hey!

Thnx for you answer. I just installed a Windows XP theme. That must already help a lot.
I think the system is pretty much ready to go. Only Skype gives me problems. It is sad to see that the skype version for Windows and Mac is much more evolved then the Linux version…

Some things that remain to be done:

1) Disable the login sound of ubuntu
2) Get the camera working (for some reason there is no image, but only a green blurry window where the video should be in Skype)
3) Restrict her privileges so she can't access the system settings and so on.
4) Make Both skype and Firefox launch at login.

Anyone some ideas how to fix this?
Thnx!

---

### Post by jward3010 on 2009-11-08
1) Can be done in sessions or startup applications. Look for "Gnome Login sound" and untick.
2) Haven't a clue
3) Create a new user, maybe call it "Granny" (I suppose that makes sense) and automatically that user will be set to not be able to "Administer the system". What this exactly means for the "System" menu I'm not sure but give it a try and see what you can change and not. Even better, get rid of the Ubuntu menu (right-click and "remove this item").
4) Both Skype and Firefox can be put in "Startup Applications" so as to start at login.

See how you get on with these.
4)

---

### Post by KEBDARGE on 2009-11-08
Cool! Most worked!

Now only the webcam remains the be solved. but after doing some research on the web, i found that that might not be that easy…

I opened a new topic for that issue alone right here:
[http://ubuntuforums.org/showthread.php?p=8273797#post8273797](http://ubuntuforums.org/showthread.php?p=8273797#post8273797)

this one is more or less solved. thnx!
):P

---

### Post by jward3010 on 2009-11-08
Webcam's are a little up and down, unfortunately not as handy as switching off the login sound. I'd say in the next couple of months there will be a big improvement in Ubuntu support ad compatibility.

---

### Post by jward3010 on 2009-11-08
If you want to be more elegant with starting Firefox and Skype on startup try this in Startup Applications:
For Firefox:```
sleep 5 && firefox
```
For Skype:```
sleep 10 && skype
```

This will delay there startup by 5 and 10 seconds respectively so that the desktop environment has a chance to load properly without being interrupted by these heavy apps, it should create even more stability for that reason as well. You don't want a crashed desktop one day when you're no where near your Granny.

---

### Post by Scunnered on 2009-11-08
For the login sound try System > Preferences > Sound and change sound themes to NO Sounds.

Another thing that you could do if you wish to clean up the various lists against Applications, Places and System is to System > Preferences > Main Menu and then remove the click from the items you don't wish to display. 

Hope this assists

---

### Post by KEBDARGE on 2009-11-08
cool. all seems to work.

Now the only thing that remains is that the keyring needs to be unlocked before skype can work.
Is there a way that the keyring unlocks automatically?

already found it. 
Thnx everyone for helping me out.

My grandmother will be happy and free of viruses now and I can focus on the tea and applepie again when I am there ;)

---

### Post by Dullstar on 2009-11-08
Just saying, it probably would have made more sense to start off KDE just because it is a little closer to Windows in the interface regards.

---

### Post by jward3010 on 2009-11-08
> **Dullstar said:**
> Just saying, it probably would have made more sense to start off KDE just because it is a little closer to Windows in the interface regards.
To be fair that's not a bad point.

---

