---
title: "No Gnome Panels !"
date: 2011-07-18
forum: Desktop Environments
---

### Post by unhopeful on 2011-07-18
I just installed Ubuntu today along side windows, it installed fine and everything was fine untill i done a restart ( the first restart ) and now when i log in all i get is my desktop Pic and no panels at all. i can right click on the screen to bring up the drop down menu, but that is about it. there is no start button to press as there is no panels at all. i tried a fix i found on this thread were i put in sudo commands to delete the panels and then re install them, but that didnt work either. im at my wits end. it done the same last night when i installed it and i thought it was one of the LOADS of updates i let it install, but today i didnt let it install them all and it still done it. and help would be greatfull as i want to get away from Win7

---

### Post by wildmanne39 on 2011-07-18
Hi, are you using 11.04? if so are you logging into unity or ubuntu clasic? if you do not know take a screenshot by hitting the prt/screen button and post it here.

---

### Post by unhopeful on 2011-07-18
it is 11.4. ive tried to run in classic and it does the same thing. as for taking a screen shot. i can press the prntsc button, but then how do i get to were it is. i have no panels so cant acces my computer or anything ?

---

### Post by jba3 on 2011-07-18
Right click the desktop, then Konsole / Terminal. Type "gnome-panel" and hit enter. See if the panel comes back.

If it does, you can add a startup entry for gnome-panel. I'm not sure that's the "right" way to do it, but it solved it for me when I had that happen.

---

### Post by wildmanne39 on 2011-07-18
> **unhopeful said:**
> it is 11.4. ive tried to run in classic and it does the same thing. as for taking a screen shot. i can press the prntsc button, but then how do i get to were it is. i have no panels so cant acces my computer or anything ?
Hi, ok try what this link says, you can open a terminal by hitting ctrl+alt+t.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by Blasphemist on 2011-07-18
This is what you need to do from the link above.
```
Reset Compiz

The following commands will reset all the settings for Compiz. You can run it in a terminal if available, or a tty:

gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```

I'm betting you were doing some customizing before the reboot. Be careful with that. I'm not saying don't do it, just be more careful.

---

### Post by unhopeful on 2011-07-19
> **Blasphemist said:**
> This is what you need to do from the link above.
```
Reset Compiz

The following commands will reset all the settings for Compiz. You can run it in a terminal if available, or a tty:

gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```

I'm betting you were doing some customizing before the reboot. Be careful with that. I'm not saying don't do it, just be more careful.

Ok. them comands wokrd. but i wasnt able to use Ctrl+alt+t to bring up a terminal. that wouldnt work. so i tried other Ctrl+alt hotkeys and found that Ctrl+alt+F1 turns the hole screen into a Terminal. so was able to get back into linux .

But then i decided to try and set up my Duel screen with the Nvidia server settings and now the Main screen stays black while the second screen( witch is a 32" LCD TV ) only shows the top right corner of my desktop ZOOM'd way in. 

Is there by any chance a simaler comand as above to reset the Nvidia server settings ?

Thanx for the help, at least i was back on for a few minutes. 

Spot the Ubuntu noob : )

---

### Post by Blasphemist on 2011-07-19
which nvidia card are you using and which driver for it are you using? Please post the results of this command.
```
sudo lshw -c Display
```

What is shown in additional drivers relating to nvidia? Are multiple drivers shown and does one show active?

---

### Post by wildmanne39 on 2011-07-19
> **unhopeful said:**
> Ok. them comands wokrd. but i wasnt able to use Ctrl+alt+t to bring up a terminal. that wouldnt work. so i tried other Ctrl+alt hotkeys and found that Ctrl+alt+F1 turns the hole screen into a Terminal. so was able to get back into linux .

But then i decided to try and set up my Duel screen with the Nvidia server settings and now the Main screen stays black while the second screen( witch is a 32" LCD TV ) only shows the top right corner of my desktop ZOOM'd way in. 

Is there by any chance a simaler comand as above to reset the Nvidia server settings ?

Thanx for the help, at least i was back on for a few minutes. 

Spot the Ubuntu noob : )Hi you can run these commands.
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
These commands should be ran by hitting ctrl+alt+f1 thru f6 and the black window not from the desktop.

You might want to post what the previous post ask for before resetting xorg.

---

