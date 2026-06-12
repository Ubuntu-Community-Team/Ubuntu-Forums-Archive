---
title: "Customize a Gaming Mouse Extra Buttons"
date: 2012-12-21
forum: Gaming &amp; Leisure
---

### Post by Barsoianu Radu on 2012-12-21
I have a Cyborg R.A.T 7 MMO gaming mouse. This mouse has 19 buttons, and it would be nice if someone helps me to use them all. They work perfectly under Steam (for linux), however the problem i have is with World of Warcraft (via wine). WoW by default only recognizes 5 mouse buttons, to use the others (even in Windows) u have to install the mouse driver and software and assign the buttons to keyboard buttons. I have tried doing so in linux, trying 3 different programs, but not works. Here goes : 

1.BTNX - crashes all the time, it's no longer supported.
2.EasyStroke - It works, however u can only press 1 button at a time, so for MMO's where u have to always keep 1 button down for camera movement it's a bust. Also has 1-2 seccond delay.
3.IMWheel - same as easystroke, only 1 button at a time (and much harder to configure)

p.s Here is my mouse config from xorg.conf : 
```


Section "InputClass"  Identifier "M.M.O.7 Mouse"
MatchProduct "Mad Catz Mad Catz M.M.O.7 Mouse"
MatchDevicePath "/dev/input/event*"
Option "Buttons" "19"
Option "ButtonMapping" "1 2 3 4 5 6 7 8 9 10 11 12 0 0 0 16 17 18 19"      
Option "AutoReleaseButtons" "13 14 15"      
Option "ZAxisMapping" "4 5 6 7" 
EndSection


```

Any help would be apreciated, even if i have a RAT 7 MMO, a guide here would help anyone with the same issues. And from what i've searched(and i did) there are allot of people asking for a solution to this (mapping any mouse extra buttons to keyboard, but with no delay and in a way that you can press more than 1 button at a given time).

---

### Post by Barsoianu Radu on 2012-12-21
anyone ? did i post this in the wrong section ?

---

### Post by Barsoianu Radu on 2012-12-23
cmmon, someone has to know a bit more than me about mapping those lazy buttons.

---

### Post by holastickboy on 2012-12-23
I don't have the mouse that you have stated you own, so I am unable to do any fiddling to test out solutions.  I have found some links that might help, but I have no way of testing them.

Ubuntu multi button mice:
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

Cyborg Rat 7 MMO mouse where someone has had some success
[http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/](http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/)

Wish I could help more, but I don't have the hardware you do :(

---

### Post by Barsoianu Radu on 2012-12-23
this thread is not about customizing this mouse extra buttons but any mouse. The first thread i am familiar with, i started from there when i wanted to setup the mouse (that was pretty hard), and as you can see my xorg.conf is listed above. The seccond thread you linked is about imwheel which i did try and that dosn't solve the issue. As i sad at start making only 1 button work at a time and not all simultaneously it's really unplayable.

---

### Post by Barsoianu Radu on 2012-12-23
> **holastickboy said:**
> I don't have the mouse that you have stated you own, so I am unable to do any fiddling to test out solutions.  I have found some links that might help, but I have no way of testing them.

Ubuntu multi button mice:
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

Cyborg Rat 7 MMO mouse where someone has had some success
[http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/](http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/)

Wish I could help more, but I don't have the hardware you do :(


and last, you can try this at home with any mouse that has more than 5 buttons, and make the 6'th work in wow for example (althou i'm pretty sure that wow is not the only one recognizing only 5). Please read my inital post, and what problems i ran into trying out 3 different programs (BTNX, EasyStroke and IMWheel).

So to summarize what i need is :

a program/hack/whatever to map let's say any mouse button nr 6 to key "K" for example. In the game i assing an action to button "K" and i can call that action by pressing the linked mouse button. There should be no delay, and i shoud be able to press mouse button nr 6, while holding down mouse button nr 3 (for example).

---

### Post by Barsoianu Radu on 2013-01-02
hopefully 2013 will bring more ppl to this thread and will help solve the issue. currently moved back to windows :(. I like digging up on forums, trying to solve an issue and i have some paciente, but 1 month without beeing able to use a mouse is more than i can bare :)

---

### Post by Zirts on 2013-01-15
I know the feel :)   Have my Razer Diamondback 3g, has only 4 additional buttons but they are essential for me to play arenas effectively. 

Currently my mouse xorg.conf looks like this:

```

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "Name" "Razer Diamondback Optical Mouse"
	Option	    "Device" "/dev/input/mice"
	Option	    "CorePointer"
	Option	    "Resolution" "1600"
	Option	    "Buttons" "9"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "ButtonMapping" "1 2 3 6 7 8 9"
	Option	    "one page back" "4"
	Option	    "one page forward" "5"
EndSection

```
I don't really have any idea what it does but it makes the first 2 buttons work. One button does page forward and other page backwards. But now I am wondering if I could type something like numpad 4 into thoes quotes instead of one page forward. Or is it only certain keys or words you can use there?  

And then the keymapping and Zaxis mapping. What is the difference between them? And the keymapping, isnt it supposed to show all my mouse keys from 1 to 9. I have 9 keys if you count in the middle mouse button rolling forward and backward too. But why is it like 1 2 3 6 7 8 9, should it not be 1 2 3 4 5 6 7 8 9?  Seems very unlogical.

---

### Post by Barsoianu Radu on 2013-01-17
didn't know that you can map mouse buttons directly inside xorg.conf, first time i see this, maybe someone will show us how to map those buttons to keybinds and problem solved :). 
I have opened a troubleticket to madcatz as well, but got the same responce, no drivers/software in the forseeable future. I'll just switch to roccat (they support linux) as soon as they put out an mmo mouse.

---

### Post by Zirts on 2013-01-18
Yeah, it is pretty interesting. If we could find out more commands for it then maybe there would be no need for some official driver release. Open up xorg and edit it your self.

Edit:  
Some info in here [http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html#sect6]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html#sect6") but it shows a really small amount of commands that you are able to use in xorg.conf :S

Edit: Trying to understand this at the moment [http://ftp.x.org/pub/X11R7.0/doc/html/mouse5.html](http://ftp.x.org/pub/X11R7.0/doc/html/mouse5.html)  but I am not sure if I will be able to edit everything my self after reading it :D

Edit: Yeah so I got a bit smarter about the ZAxismapping but not much else in there...

---

### Post by Barsoianu Radu on 2013-01-19
I think that only page movement in Firefox is implemented but nothing else, otherwise i can't see the point of programs such as IMWheel, BTNX and EasyStroke. 

Like i sad at the start of the post, EasyStroke comes closest to solving the issue here, i mean everything works, just pressing 2 mouse buttons at the same time dosn't (and that's a must for gaming), and it has a bit of delay sometimes (i press 1 mouse button and the action happens after 1-2 secconds).

---

### Post by Barsoianu Radu on 2013-01-25
Still no xorg know-it-all people stumbled upton this post ? :(

---

### Post by Zirts on 2013-01-27
Yeah I tried easyStroke but it seems my mouse is from another league. On Zaxismapping my scrollwheel actions are under number 4 and 5. But the 2 extra buttons that dont work are under thoes number also. So I can only have one working, either wheel or buttons. No idea how windows drivers solve it...

---

