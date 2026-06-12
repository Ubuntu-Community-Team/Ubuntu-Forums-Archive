---
title: "Transparent Terminal?"
date: 2005-11-15
forum: Desktop Environments
---

### Post by tagg3rx on 2005-11-15
How do you make your terminal transparent?

Thanks
:KS Tagg3rX :KS

---

### Post by NewWithoutClue on 2005-11-15
I would 'apt-get' tilda, if i were you.
you can hide it and pop it up when you want by pressing 'F1', of course you can change the key(s).
It is completely transparent...you can't move it with the mouse...you have to tell tilda where you want it

```
sudo apt-get install tilda
```
( right clicking on the tilda terminal will allow you to configure it )


w00t,
Paul.

---

### Post by souled on 2005-11-15
[QUOTE=tagg3rx]How do you make your terminal transparent?

Thanks
:KS Tagg3rX :KS[/QUOTE]

Right click in terminal window --> Edit current profile --> Effects. The transparency setting is in there.

---

### Post by tagg3rx on 2005-11-16
That did the trick

One oddity, I have the term open infront of another window and its transparent to the desktop.

Cool tho - just not how i expected transparency to look, figured i would see the window behind it.

Thanks!
:KS Tagg3rX :KS

---

### Post by tagg3rx on 2005-11-16
One more question : 

How do you make the text colors change I dont see that in the prefs.
But i know ive seen it in screen shots where like depending in the command and read out it displays diffrent colors.

Thanks 
:KS Tagg3rX :KS

---

### Post by souled on 2005-11-16
The transparency in the terminal is like a fake transparency. It just uses an image of your background to make it look transparent. To get real transparency you have to use some composite thing (not sure what it's called) Look in the howto section; there's a thread on it. 

To change the font color go to the Colors tab in the profile editing menu of gnome-terminal. Uncheck the 'Use colors from system theme' box and then edit colors to your hearts content :)

---

### Post by angkor on 2005-11-16
[QUOTE=souled]Tsome composite thing (not sure what it's called) Look in the howto section; there's a thread on it. 
[/QUOTE]


You're looking for 'xcompmgr' and 'transset'.

[http://ubuntuforums.org/search.php?searchid=2539890](http://ubuntuforums.org/search.php?searchid=2539890)

Try it out if you like, but be warned it is not quite stable and very resource hungry.

---

