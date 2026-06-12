---
title: "No top panel with Unity"
date: 2018-04-12
forum: Desktop Environments
---

### Post by atatistcheff on 2018-04-12
Ok, I admit I've been messing with some themes on Ubuntu 16 and I have a condition now that when I enable Unity, my top panel "widgets" or whatever they are on the right disappear.  I think that Unity is overwriting that top panel.  The icons are either underneath or otherwise borked.  I'm referring to the little icons normally in the upper right like sound, clock, logout, etc.  These are all gone when I select Unity with the CompizConfig Manager.  If I go back to Gnome they come back but of course I lose all the cool Unity stuff.  I've searched all over for a setting that will enable the items on my top panel again but have struck out so far.  Any assistance would be appreciated.  Even if it means reverting all my settings to the default Unity desktop.

---

### Post by Frogs Hair on 2018-04-12
Try the following commands and if that fails use the Unity reset command. 

```
sudo apt-get install dconf-tools 
```   ```
dconf reset -f /org/compiz/
``` Unity Reset: ```
setsid unity
```

---

### Post by atatistcheff on 2018-04-12
Thanks for the suggestions, I've tried all of that and the icon are still missing.  If it helps they are actually there just under whatever is sitting on top of the panel.  If I invoke the HUD it fuzzes out the top panel and I can see shadows of the items like clock, sleep, logout, etc.  So they're there just underneath something.  Also in the login screen the panel does show.  It's just after I login that something is sitting over the top of the panel.  Very frustrating!  Turning off Unity brings it back so there's something in Unity that is causing me this grief.

---

### Post by atatistcheff on 2018-04-12
Another update, I used the Unity Tweak tool to reduce the Panel opacity to zero.  When I do this the icons start to come through on the right.  I can see the clock is working, see the volume control, etc.  However they are still under something so I can't click on them.  Also, the top menu on the left is now slightly visible as well but also not clickable.  The bar across the top which is covering the panel shows the name of the active window on the left.  If a screenshot would help I can post.

 Hope this helps to narrow down to whatever setting I've screwed up!

---

### Post by Frogs Hair on 2018-04-12
I have experienced overlapped panels and launchers with early versions of Unity and reset command resolved that. There might be relevant thread here, but I'll have to search for it.

---

### Post by atatistcheff on 2018-04-12
I tried setting up another user and of course Unity works fine there.  Are there any settings outside the /home/username directory?  I wouldn't think so, I've been trying to compare settings in the files under the .config folder and not having any luck so far.

---

### Post by Frogs Hair on 2018-04-12
Still looking , the link/ possible solution is in one of my posts.

---

### Post by Frogs Hair on 2018-04-12
The first command may require sudo , but try it first without.


```
rm -rf ~/.compiz-1 ~/.config/compiz-1

``````

sudo reboot

```

[https://ubuntuforums.org/showthread.php?t=2386528&page=3](https://ubuntuforums.org/showthread.php?t=2386528&page=3)

---

### Post by atatistcheff on 2018-04-12
I've blown away the entire .config directory as well as .compvis-1.  It's crazy that this thing is hanging on somehow.  Just tried deleting the .cache directory too then rebooting.  Same thing.  

Just to make sure I'm following the right procedure here's how I am switching between Unity and non-unity.  

Start CompizConfig Settings Manager
Disable Window Decoration in the Effects section (this causes me to lose the window moving/sizing and other controls)
Check the Ubuntu Unity Plugin in the Desktop Section - resolve conflicts or ignore, doesn't seem to matter
After this Unity starts and puts some kind of panel on top of my panel making all the buttons/icons inaccessible.  I can't even logout now.  Have to either switch back to non Unity or just use the terminal to reboot.

If there's a better way I'm open.  
I'm about to give up and live without Unity for now.

---

### Post by Frogs Hair on 2018-04-12
You ran the command the in the affected session not the new user you created correct ?

---

### Post by atatistcheff on 2018-04-12
Yes, done everything in the original user's home directory.

---

### Post by logix2 on 2018-04-13
What is on top of the panel? A work-around would be to create a new user, delete your current user (transfer any data from the home folder you may need), then you can rename the new user the the old name.

---

### Post by mc4man on 2018-04-13
Go to .config/dconf, inside will be a file named user
Either delete or if desired rename to user.bak
Then _immediately go ctrl+alt+F3 to go to tty3_
From there login with username & password, once logged in type in  reboot, press enter

This should give you the default gsettings, see if that does it..

---

### Post by atatistcheff on 2018-04-13
> **logix2 said:**
> What is on top of the panel? A work-around would be to create a new user, delete your current user (transfer any data from the home folder you may need), then you can rename the new user the the old name.

Yes, that will probably be my last resort.  This setting appears to be hanging on somewhere very sneaky.  Deleting the entire .config and .cache directories didn't fix it.

---

### Post by mc4man on 2018-04-13
> **atatistcheff said:**
>  Deleting the entire .config and .cache directories didn't fix it.
That won't work, told you what may..

---

### Post by atatistcheff on 2018-04-13
> **mc4man said:**
> That won't work, told you what may..

Nope, didn't work either.  Apparently this wayward setting is kept somewhere nobody knows about.  I've switched to another user account on this machine as it appears there is no way to fix this for my original user.

I appreciate all the suggestions, at this point I'm going to cut my losses and go with the other account.  Spent too much time on this already!

---

