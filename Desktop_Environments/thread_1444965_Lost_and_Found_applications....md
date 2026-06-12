---
title: "Lost and Found applications..."
date: 2010-04-02
forum: Desktop Environments
---

### Post by jlubey on 2010-04-02
Hey guys,
im fairly new to ubuntu, but i think im getting the hang of it. i just have a quick question:

i booted up my kubuntu partition, and for some reason the icons for some of my quick launch applications were missing. i investigated more and apparently 4 applications got moved to the ¨Lost and Found¨ folder in my application Launcher. (Amarok, Opera, Kopete, and Thunderbird). i have no idea why this happened, or what it means. what i would like to know is how to move them back where they belong and get their icons back (im assuming a simple uninstall and re-install would work here, but im not sure what commands to use. sudo apt-get install --reinstall didnt help).

Kubuntu 9.1, fully updated
any help would be greatly appreciated!! Thanks!

---

### Post by irishbreakfast on 2010-04-02
Files that were saved during failures are put into lost+found. Depending on what happened to your machine lately, I'd be inclined to run an fsck (file system check). Please read the man pages (man fsck) for the switches to use. fsck runs automatically after a certain number of boots, I think it is set to 30 by default.

sudo apt-get remove package
sudo apt-get install package

If, however, it is just missing icons and not the application, there should be a simple method to restore them. But I can't help there as I don't use kubuntu.

---

### Post by jlubey on 2010-04-02
thanks for your reply!

im still having trouble though. i ran fsck and it had a few lines of text about ¨orphaned nodes¨ but that was it (i dont know if that is important or not). i rebooted, went into Konsole and tried sudo apt-get remove/ then install, but the applications still just stay in lost and found.  so i tried playing around with purge commands, autoremove, install --reinstall, nothing seems to work to get them out of the lost and found. they will reinstall, but they never leave lost and found (one thing to note is that the settings for the applications havent changed, in thunderbird all my old emails are still there). after trying all this, i rebooted and somehow amarok was finally gone from the lost and found. so i was able to sudo apt-get install amarok and now that is where it is supposed to be :)  im still having issues with the other ones though, any ideas??
thanks again!

---

### Post by jlubey on 2010-04-02
ok nevermind i finally got it!
i went poking around my entire filesystem and found a few files having to do with kopete, opera, and thunderbird. i manually deleted everything i could find for these applications, logged out, and they are gone from the lost and found (it doesnt even show lost and found anymore :D )
i just finished re-installing them, and they work perfectly. thanks so much for your help!!

---

### Post by benerivo on 2010-04-02
I think the programs are fine, it's just maybe at some point kde4 could not locate them. It has since found them, and has put them in a special menu location. Try fixing it by right clicking on the K menu and editing the menu. From the new edit window you can try to restore the original system menu, which might put them back. If that fails you can just move them manually to the correct menu sections. From this menu editor you can also set the icons to whatever you want.

The same thing happened to me a long while back, when i tried to change either the icon or run command of an app icon in the panel. This had the effect of changing that same app in the main menu, and it ended up in lost and found.

EDIT - i see it's been solved.

---

### Post by jlubey on 2010-04-02
you know what, i had just marked it as solved and it happened again. your reply just fixed it and made me realize something- it was after i changed the icon that they moved to lost and found. i tried what you said and manually moved them back where they belong. thank you so much! you saved me a lot of headaches and time :D

---

