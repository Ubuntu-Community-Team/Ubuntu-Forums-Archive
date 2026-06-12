---
title: "Automatic Software Updates Not Working."
date: 2005-11-26
forum: Desktop Environments
---

### Post by Georgie-o on 2005-11-26
The Ubuntu update icon states "29 updates available."  When I click to show me the updates, the screen comes up with a list of updates with "checked boxes."  I then press "install" and a task bar/progress window shows up briefly and then turns off after about 1 second.  The orginal update window is still up showing that the updates are waiting to be installed.  I try again, and get the same result.  Any thoughts or help?****

---

### Post by AndreiCiprian on 2005-11-26
I have installed some of the updates today including a new kernel version.
Everything went fine.

---

### Post by Georgie-o on 2005-11-26
I figured out what went wrong...well I corrected the problem but don't know enough to actually know why it wasn't working.  Yesterday I had a problem with the "add applications" showing that all programs not already installed were unavailable.  I posted for assistance and found advice on making changes tot he following file:

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list 

I then replaced this with the text provided at: [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")  

Which worked well and enabled all the programs I wanted, however, it appears to have done something to the automatic update ability (maybe on purpose?)  So I went back to the original language and now it updates fine.

---

### Post by stalefries on 2005-11-26
Try opening up a terminal (Applications>Accessories>Terminal) and typing 
```
sudo apt-get update && sudo apt-get upgrade
``` 

It will prompt you for your password. Type it in, but be warned that it willnot show little asterisks for each character of your password. Don't worry, this is normal. After a few seconds, it will give you a yes or no question. Type "y" and press enter. 

This is basically the same as installing the updates the way you were doing it, but without a fancy gui.

---

