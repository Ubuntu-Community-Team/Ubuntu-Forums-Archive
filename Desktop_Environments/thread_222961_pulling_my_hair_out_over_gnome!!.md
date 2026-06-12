---
title: "pulling my hair out over gnome!!"
date: 2006-07-25
forum: Desktop Environments
---

### Post by harty83 on 2006-07-25
Okay so for some wacked out reason out of no where, gnome-panel-snapshot opens one after another and renders my computer useless.  It will open hundreds of them and I can't stop it.  All I can do is do a hard shutdown.  I can't figure out what causes it.  I'm typing along and then bam, it starts to happen.  Is there a way to disable gnome's snapshot capabilities or does anyone know how to fix this??!!

Aalan

---

### Post by aysiu on 2006-07-25
That's weird. Has it always done that?

Well, try this. Press Control-Alt-F1.
Log in.
Then type these commands: ```
killall gnome-panel-snapshot
killall gnome-screenshot
mv ~/.gnome2 ~/.gnome2.old
mv ~/.gnome ~/.gnome.old
mv ~/.metacity ~/.metacity.old
mv ~/.nautilus ~/.nautilus.old
mv ~/.gconf ~/.gconf.old
mv ~/.gconfd ~/.gconfd.old
exit
``` Then press Control-Alt-F7 and Control-Alt-Backspace to reset the X server and log out. Log back in again.

---

### Post by harty83 on 2006-07-25
It used to happen to me when I used breezy.  This is partly what drove me to kde.  But with dapper, gnome actually can do the things I want now so I would like to use it instead.  

When it does this, pressing Control-Alt-F1 does nothing along with Control-Alt-Backspace.  It simply renders me completely useless.

Do you think it is a config file of some sort?  I move the files and restart x and see if it does it again.

---

### Post by harty83 on 2006-07-25
Okay found a connection. It always happens when I am doing a control command.  For example control-o to open something, control-s to save, control-a to select all, etc.

---

### Post by harty83 on 2006-07-25
> mv ~/.gnome2 ~/.gnome2.old
mv ~/.gnome ~/.gnome.old
mv ~/.metacity ~/.metacity.old
mv ~/.nautilus ~/.nautilus.old
mv ~/.gconf ~/.gconf.old
mv ~/.gconfd ~/.gconfd.old

Okay, so I tried this and it didn't work.  My laptop froze up with opening hundreds of gnome-panel-snapshot.  I had to do a hard shutdown.  

I tried renaming gnome-panel-snapshot and gnome-screenshot but then I just got hundreds of metacity errors.  

This time I wasn't even using control!!  Any other ideas on what could be causing this?

Alan

---

### Post by aysiu on 2006-07-25
Does the same thing happen if you log in as another user?

---

### Post by harty83 on 2006-07-25
I did try to remove and purge metacity and reinstalled it.  Gnome seemed to load almost twice as fast after doing that so I wonder if it was something with metacity.  Anyway, I'll drive it for a while and see happens.  If it happens again, I'll create a new user and see if it happens under that user.

---

### Post by harty83 on 2006-07-25
Sigh...it happened again.  I just lost probably a half hour's worth of work.  I guess I will learn to constantly save the hard way.


Anyway, I'll try logging in as a different user and see if it happens.

---

### Post by aysiu on 2006-07-25
A half hour.
You could reinstall in a half hour...

---

### Post by harty83 on 2006-07-25
Created a test user and used it for five minutes before it happened again.

Help!!??  What in the world would cause this to happen?

---

### Post by harty83 on 2006-07-25
> A half hour.
You could reinstall in a half hour...

I could but the time it would take to back up my gigs worth of information and then get everything set back up would take more like several hours.  ;-)

---

### Post by aysiu on 2006-07-25
I have no idea. It may be worth your while to reinstall, unless someone else has a bright idea about it.

---

### Post by harty83 on 2006-07-25
> I have no idea. It may be worth your while to reinstall, unless someone else has a bright idea about it.

Thanks for all of your help.  I may just have to do that.  I'll sleep on it ;-)

---

### Post by VirtuAlex on 2006-07-25
Last time I saw something like this when my son spilled half a glass of water into keyboard and pretended nothing happened. But you tell that it happens only in gnome... That's odd.

---

### Post by harty83 on 2006-07-25
That would def cause some problems!!  :-)

It is most definitly only happening in gnome.  I've been using kde for months now and just decided this week to switch back to gnome.  

As one last step before I decide to do a complete reformat (and go through all the hassel that comes with it), I've removed and purged anything gnome.  So I ran 

```
sudo apt-get remove --purge gnome*
```

Now I'm reinstalling ubuntu-desktop

```
sudo apt-get install ubuntu-desktop
```

We'll see what happens.

---

### Post by zxee on 2006-07-25
You might want to look in /var/log/syslog also right after this happens do dmesg in a shell hopefully there's some related output there.

---

### Post by jimmygoon on 2006-07-26
What kind of keyboard do you have.... what the heck.... what kind of COMPUTER do you have... Just to ask the really sadly obvious question... Is there any chance you've spilled, at any point in time, a liquid into your keyboard, OR... Does your keyboard "map" Ctrl to Print Screen?

---

### Post by harty83 on 2006-07-26
> 
I've looked through the logs and can find nothing that signifies a problem.

> What kind of keyboard do you have.... what the heck.... what kind of COMPUTER do you have... Just to ask the really sadly obvious question... Is there any chance you've spilled, at any point in time, a liquid into your keyboard, OR... Does your keyboard "map" Ctrl to Print Screen?

This problem occurs on a Dell Inspiron 5150 laptop.  It happened during class yesterday (in the middle of taking notes!!  Thank God for autosave).  And it was happening last night while using an external keyboard (Dell standard pc104 keyboard).  I don't think it is something I spilled since it happens using both keyboards and kde does not signify that it is having any kind of problem. How would I check to see if ctrl has been mapped?  And why would it open one screenshot after another (like up into the hundreds before I kill the machine) if the key was just mapped?

Thanks!

edit:  Is there an alternative for metacity that i can install easily?

---

### Post by VirtuAlex on 2006-07-26
Log into text console and return to gnome. Make the bug happen again. If you wait long enough it will use up all the memory and system eventually will kill offending process. It also should output some error message at the console then and maybe make a log entry somwhere. Maybe there will be some useful information in there?

---

### Post by harty83 on 2006-07-26
> Log into text console and return to gnome. Make the bug happen again. If you wait long enough it will use up all the memory and system eventually will kill offending process. It also should output some error message at the console then and maybe make a log entry somwhere. Maybe there will be some useful information in there?

The computer had a hard lockup before it got to the point where the system started to shut things down.  I've searched through any logs I could think of and found nothing.  Just a gap in time where I rebooted the machine.

The beast happened appeared again a few minutes ago.  The screenshot gui actually appeared and I was able to consistantly click cancel.  I guess I was able to get ahead of it because I was able to stop it.  But, even though it stopped, both my keyboards (laptop keyboard and external) stopped working.  My mouse would work though.  I couldn't make the menus drop down nor do anything with icons in the system tray (like use the shutdown button).  I could open programs that had shortcuts on my desktop or in the panel. 

I did successfully do a purge uninstall of most everything gnome and reinstalled it all last night.  And it has happened a few times already today.  I'm at a loss!!  What is this beast and how do we stop it??  Is it back to kde for me?  

Thanks for everyone's suggestions!!

---

### Post by VirtuAlex on 2006-07-26
What if you just disable the troublemaker? Move it somewhere so system couldn't find it.

---

### Post by harty83 on 2006-07-26
> **VirtuAlex said:**
> What if you just disable the troublemaker? Move it somewhere so system couldn't find it.

Tried that a few days back and instead of gnome-panel-snapshot windows I get metacity error boxes.

I just decided to try out openbox instead of metacity to see if that takes care of the problem.  So far so good.  But time will tell!

---

### Post by jimmygoon on 2006-07-26
Change you keyboard mapping for the PRNTSCRN button to open a new terminal... that way if you start getting tons of terminals popping up... you know it has something to do with the keyboard or however gnome is polling the keyboard.

as for spilling something, even if you were using an external keyboard the internal one would still be on....

---

