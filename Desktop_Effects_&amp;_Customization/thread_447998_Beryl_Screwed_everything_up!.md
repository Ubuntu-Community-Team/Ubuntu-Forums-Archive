---
title: "Beryl Screwed everything up!"
date: 2007-05-18
forum: Desktop Effects &amp; Customization
---

### Post by 1oki on 2007-05-18
I installed Beryl, and didn't like the way it looked. So I removed it and nothing has been right ever since.  I tried to get the original window manager but it wasn't installing properly.  After I removed Beryl, I could not minimize any windows, and all other apps were not showing up in the bottom task bar. When I tried to use the show desktop button without beryl I would get this message:
"Your window manager does not support the show desktop button, or you are not running a window manager."

So I then tried to go to the windows manager in the preferences section and I got this message:
"Windows manager "Unknown" has not registered a configuration tool"


And yes I did assign a configuration tool and the windows manager is not unknown...

So I installed Beryl again. When I went to open the cmd terminal the window was white. I know it was working because i could type commands in to run apps and they would. Now the only way to use the desktop with any means of efficiency is to install beryl, which doesn't work right anyways. I have removed and installed and rebooted it now a few times.. This is starting to act like windows. 

So this is what i was looking to try to do... I want to remove my desktop as a whole and reinstall it. But when I do the apt-get remove ubuntu-desktop, apt-get autoclean, apt-get autoremove, (reboot) apt-get install ubuntu-desktop. Nothing Changes!!!

any help?

---

### Post by irish_flu on 2007-05-18
OK, I think I see what part of the problem is.  The "ubuntu Desktop" package is (I believe) just a package that depends on other packages (like gnome, etc).

In other words, by removing that package I don't think you're actually removing any of the packages that matter to Gnome (the desktop environment) or Matacity (the default window manager).

If it were me (note, I've never done this exactly) I might try to uninstall and reinstall "metacity" and "metacity-common".

That won't rebuild Gnome, but I think it'll rebuild the window manager (which seems to be where your problems are).

---

### Post by 1oki on 2007-05-18
Thanks I will give that a shot right now!

---

### Post by 1oki on 2007-05-18
nope... didn't work... any other ideas? I don't have net at home so i wont be able to see this until monday! Common peeps I know you all are smart :)

---

### Post by lazyart on 2007-05-18
I think you want metacity back. :)

Launch a terminal window and type```
metacity
```This should bring back the application buttons.  Don't close the terminal window or your buttons will go away.  Now go to System>Preferences>Sessions.  If you see any reference to beryl there, remove it.  Then hit New and enter metacity as the description and for the command.

Now hit Control-Alt-Backspace.  This will restart X and dump you back to the login screen (so save anything you have open first!).  When you log in your apps should all have buttons again.

---

### Post by gigaferz on 2007-05-18
hey 1oki!!

im in the same boat here!

i have been reading a lot during the last couple of days but,nothing,

removing gnome private 2 (or something), and deleting .gnomeric were my only options, so far I havent found gnomerc at all!  I will remove gnome private 2 folder(but i remember seeing it empty?) to see what happens...

Meanwhile why dont you log in safe gnome  everything should work fine.  All this mess up is because beryl doesnt revert some config files....

---

### Post by gigaferz on 2007-05-18
** lazyart

I tried metacity  but it tells me its running already..aborting...

so I tried killing metacity, but I need a job Id number, How do i kill metacity? so I can launch it again?

---

### Post by m10 on 2007-05-20
you may try
```
metacity --replace
```
it worked for me...
i have/had a similar problem even if i never installed beryl
i thinked that it may be cose of the ntfs 'driver'? or just the desktop effects (i'm in Feisty)?
but this is not a definitive solution have i to do it at every boot now?

---

### Post by 1oki on 2007-05-21
> **lazyart said:**
> I think you want metacity back. :)

Launch a terminal window and type```
metacity
```This should bring back the application buttons.  Don't close the terminal window or your buttons will go away.  Now go to System>Preferences>Sessions.  If you see any reference to beryl there, remove it.  Then hit New and enter metacity as the description and for the command.

Now hit Control-Alt-Backspace.  This will restart X and dump you back to the login screen (so save anything you have open first!).  When you log in your apps should all have buttons again.

I could kiss you! This was exactly what I needed! Everything works fine now! Thanks! :D

---

### Post by gigaferz on 2007-05-23
Thank you for your help, I truly appreciate it, now if you excuse me, Im still looking to get sound in kopete, share files between 2 ubuntus, svae permanent setting for a xbox pad that by the way has the "y" s inverted, and try to run kof roms(wont run at all,only capcom roms ), and n64 roms properly (is too slow)..

Good thing im not into webcams or video stuff,  ohh, well,,,,, at least  replacing metacity, I noticed a better speed in apps and web browsing, also , using flock, is way faster then firefox (weird,huh?)

Thank you again!!!!

---

