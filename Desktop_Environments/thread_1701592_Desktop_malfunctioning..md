---
title: "Desktop malfunctioning."
date: 2011-03-06
forum: Desktop Environments
---

### Post by quantumpositron on 2011-03-06
Hi,

I recently installed Ubuntu on a single-core AMD 64 with an ATI RADEON 9100.  My desktop is malfunctioning:

Specifically, when I close a program the program still shows in the task bar below.

I can only see two workspaces in the workspace view.

When I use Evolution Mail I cannot get the cursor to show in the textboxes, nor does it type.

I am using the Radeon drivers that Ubuntu selected for me upon installation.  

Aside from installing Chrome and the plug-ins Firefox said it needed to view YouTube, I have not done anything to my installation.

Please help!

Thank you.

-QP

---

### Post by Krytarik on 2011-03-06
Try using the Open Source Edge driver for your video card:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by quantumpositron on 2011-03-08
Thank you for the advice and terminal commands.  Everything went fine and so far no problems.  

The desktop is sort of unpredictable in its behaviour.  One day it works, the next day not.  Hopefully this is all 

what was needed.

Thank you again.

-QP

---

### Post by quantumpositron on 2011-03-09
I just had to reboot ubuntu because a cursor would not show up in Evolution Mail.  Guess it didn't work.  

What else can I try?

Thanks again,

-QP

---

### Post by Krytarik on 2011-03-09
Did it work once or do the issues exist from the start?

---

### Post by Krytarik on 2011-03-09
And what exactly do you mean by this?:
> **quantumpositron said:**
> I can only see two workspaces in the workspace view.


---

### Post by quantumpositron on 2011-03-09
> **Krytarik said:**
> Did it work once or do the issues exist from the start?

The Open Source Edge driver did not have an effect on the malfunctions.  Sometimes everything works fine, and sometimes things go wrong.

To give you an example, this morning I booted up and checked my email in Evolution.  I then opened a 

browser and went to a site.  I went back to Evolution to check some new mail.  Then it broke.  I could not 

get back to the browser.  The close, minimize, and maximize icons were no longer displayed in the upper 

left hand corner.  So I clicked on the browser in the task bar and nothing happened.  I was stuck in 

Evolution.

This does NOT happen EVERY time I open Evolution and switch back to a browser.  : /

---

### Post by quantumpositron on 2011-03-09
> **Krytarik said:**
> And what exactly do you mean by this?:

In the lower right hand side of my task bar, just next to the trash bin icon are four squares.  Each one 

represents a workspace.  I was trying to refer to that.  Whenever it breaks I cannot switch between 

workspaces.

Thank you for working with me to fix this.  I'm a Windows refugee and am still learning how to find my way 

around the OS.;)

---

### Post by Krytarik on 2011-03-09
"Refugee" :)

All the symptoms eventually point into one direction: the window manager.
Do you have "Visual Effects" enabled, thus Compiz running?
If so, check if the issues remain when you replace it with Metacity, or switch Visual Effects to "None".
```
metacity --replace
```

---

### Post by quantumpositron on 2011-03-10
I looked in System>>Preferences>>Windows and don't see anything like "visual effects" or "Compiz."

Where do I look for this? :?:

-QP

---

### Post by Krytarik on 2011-03-10
Check in "System -> Preferences -> Appearance -> Visual Effects (tab)".

---

### Post by quantumpositron on 2011-03-11
Visual effects were set to "none."

Should I still install metacity?

Thank you,

-QP

---

### Post by Krytarik on 2011-03-11
"None" means Metacity as window manager, any other means Compiz. Then just try it the other way around, set it to "Normal" or "Extra".

Btw., you don't have to thank me each post. ;-)

---

### Post by quantumpositron on 2011-03-12
> **Krytarik said:**
> "None" means Metacity as window manager, any other means Compiz. Then just try it the other way around, set it to "Normal" or "Extra".

Btw., you don't have to thank me each post. ;-)

Alright. :KS

I just checked my settings again and this time they were on normal.  Is it possible these settings could 

change without me?

---

### Post by Krytarik on 2011-03-12
> **quantumpositron said:**
> 
I just checked my settings again and this time they were on normal.  Is it possible these settings could change without me?
Generally not. Do you still have the issues then?

---

### Post by quantumpositron on 2011-03-12
The issues are sort of random.  It will be a day or two of usage before I really know.  I'm keeping my fingers 

crossed. :D

---

### Post by quantumpositron on 2011-03-14
So far, so good.

Except now Youtube is in black and white.  Any ideas?

:popcorn:

---

### Post by Krytarik on 2011-03-15
> **quantumpositron said:**
> 
Except now Youtube is in black and white.  Any ideas?

There seem to be a number of people having those or a similar issue currently.
Try these workarounds, I found it in another thread:
[http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)

---

