---
title: "Firefox won't reopen"
date: 2009-02-23
forum: General Help
---

### Post by philip720 on 2009-02-23
Firefox won't reopen after closing.I have to reboot to get it to reopen.I've tried complete re-installation but when I re-install it,it re-installs the same as it was!All my add-ons,tool bars,etc. are all there like before!Only problem in 4 years that I haven't been able to solve.Using Ubuntu 8.04.   Thanks

---

### Post by Anxious Nut on 2009-02-23
How about trying this if that happens again:
go to system-->administration-->system monitor, scroll down till you find "Fire Fox" press the right click on it and choose "End", if it had problems then choose "Kill"

Note: try to do that even if you closed firefox and it is not on your panel

or you can try this, using the terminal, write "top" search for "FireFox" and memorize the PID number (the one that is written in the first column). then write in your terminal "kill -9 TheNumber"

---

### Post by lykwydchykyn on 2009-02-23
The add-ons and toolbars and so forth are stored in your home directory under the ~/.mozilla directory.  The uninstall won't touch that.  You might try renaming that folder and starting with a fresh profile to see if that fixes things.

To rename the folder:
```

mv ~/.mozilla ~/.mozilla-old

```

Have you checked the process list to see if there are firefox processes stuck in memory preventing you from relaunching?  I've seen that happen before.

---

### Post by fooman on 2009-02-23
uninstalling/reinstalling will not delete your profiles information (as you have already found out).

to do that you will need to delete the firefox information in the hidden file: .mozilla which is in your home directory.

to delete it (i do not know if it will help with your problem btw),  you can run the following command in a terminal:

```
rm -rf ~/.mozilla/*
```*please be aware that the above command will delete all of your profile, including your add-ons. bookmarks, etc...

*at the very least you should back-up your favorites/bookmarks before running it! 

you could also try killing firefox with one or both of the following commands and see if that helps:

```
sudo killall firefox
``````
sudo killall firefox.bin
```then try to open it again.

hope that helps.

---

### Post by mb_webguy on 2009-02-23
As a general rule of thumb, if a GUI application is acting up, try running it from the terminal.  You'll get a lot more information about what's going on, which will make it easier to diagnose the problem.

---

### Post by philip720 on 2009-02-23
> **Anxious Nut said:**
> How about trying this if that happens again:
go to system-->administration-->system monitor, scroll down till you find "Fire Fox" press the right click on it and choose "End", if it had problems then choose "Kill"

Note: try to do that even if you closed firefox and it is not on your panel

or you can try this, using the terminal, write "top" search for "FireFox" and memorize the PID number (the one that is written in the first column). then write in your terminal "kill -9 TheNumber"

I used the END command and it seems to be working now.Thanks a lot!

---

### Post by kmichaelray on 2009-02-23
I am having a similar problem except Firefox won't open at all. I install 8.10 and it worked fine for about two weeks, and then after an update, I can't get on the internet.  When I click Firfox it just try's to load for about 15 seconds and then goes away. I know the outer and intenet are working cause I am running 8.04 on another computer and it is working fine. 

Can anyone help?

---

### Post by lykwydchykyn on 2009-02-23
try running it from a terminal and post the output.

---

