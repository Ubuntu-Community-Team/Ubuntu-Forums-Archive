---
title: "Eve-Online problem"
date: 2007-07-08
forum: Gaming &amp; Leisure
---

### Post by Meogeo on 2007-07-08
I have just installed Eve-Online through Wine, when I go to play Eve the log on screen goes black, also it tells me that it could not locate the sound drivers.

Is there some configuring I need to do if so how do I go about it.

Many thanks in advance.

---

### Post by stuart.crouch on 2007-07-09
Usually the black screen is because eve needs arial.ttf, but its not available -
Have you copied arial.ttf to ~/.wine/drive_c/windows/fonts/ directory?  If you have windows installed you'll find it on your windows partition, just copy it over.  If you dont have windows you'll need to install the ms core fonts (sudo apt-get install msttcorefonts) and then locate the arial.ttf and copy it over.

When it comes to sound I think you just need to tell whine what to do - 
Have you run winecfg (type it in a terminal) and selected a sound driver?  I had to select OSS sound before I got anything from eve.

Let us know how you get on

---

### Post by Sammi on 2007-07-09
Here is the Wine Application Database entry for Eve-Online: [http://appdb.winehq.org/appview.php?iVersionId=8291](http://appdb.winehq.org/appview.php?iVersionId=8291)

Is has all the info you need to fix Eve, although stuart.crouch already mentioned most of it.

---

### Post by Meogeo on 2007-07-09
Thanks Stuart and Sammi that has got me into the game.

---

### Post by Ziggyz on 2007-07-15
Hey, I am getting back into eve after I made the switch from xp to ubuntu, and the only real problem I found was the sound. Its constantly choppy, should I just try different sound drivers until it sounds good?

---

### Post by Sammi on 2007-07-16
Try running winecfg and chang the sound interface architecture you are using in Wine there. ALSA gives poor performance on my machine, so I have set Wine to only use OSS.

---

### Post by eljoeb on 2007-07-16
Wine and Eve don't seem to get along for me.  I can get into the game, but none of the chat boxes have any text in them.  I assumed this was the font problem (probably is, but hold on).  I copied all of the contents of my XP font folder into Wine's windows folder and it still doesn't want to work.  

This is sad, because Eve is the only thing that keeps me on Windows.  Well, that and MS Office and Decent Joystick support (can't get the #@%@% Sidewinder to work... thread for another day).

Anyone have similar problems with Eve? Am I missing something?

---

### Post by stuart.crouch on 2007-07-16
See this thread

[http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=539909&page=1#20](http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=539909&page=1#20)

It seems that the new eve is using the documents and settings folders to store stuff
Wine symlinks your real documents folders to the wine virtual hard drive.
If you already had an eve folder it seems to cause permission issues.

See this post in the same thread for a way to fix it using wineconfig

[http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=539909&page=1#23](http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=539909&page=1#23)

> 
So I rm -rf'd .wine and started over. I installed the rev1 client patched it, and got rev2 running. Still no chat, ok tried the fix above it worked so I dug deeper and then found an easier fix for the chat issue ;)

Under winecfg goto the Desktop Integration Tab. Down at the bottom will be where it creates links for the "wine users" to the "real users" Uncheck the create links on all the folder. What you are left with is REAL folders for your profile instead of fake links. No need to manually create any folders, or anything. Im not sure why the default is to link the two users, maybe for people who use office applications or something, but it clearly causes issues with Rev2!


I didn't need to do this, but I had no eve related folders in my home or documents directory until after Eve was installed, so it could be related to set up.

Let us know how you get on.

---

### Post by eljoeb on 2007-07-16
It worked!  I took off the symlink and it worked immediately! Thank you very much!

---

