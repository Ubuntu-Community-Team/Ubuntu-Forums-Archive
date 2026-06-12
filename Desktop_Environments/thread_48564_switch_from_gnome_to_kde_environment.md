---
title: "switch from gnome to kde environment"
date: 2005-07-13
forum: Desktop Environments
---

### Post by lightchain on 2005-07-13
hi 
have apt-get installed kubuntu; how to switch from gnome to kde?
thanks
lightchain

---

### Post by frodon on 2005-07-13
In the login screen click on "session", if you've well installed kubuntu you should have KDE as choice.

---

### Post by Knome_fan on 2005-07-13
Also, if you really want to switch permanently, you probably want to change the display manager (that is essentially the login screen) from gdm to kdm.

To do that just change gdm to kdm in /etc/X11/default-display-manager

Have fun!  :grin:

---

### Post by arcanistherogue on 2005-07-13
I had this exact same question a couple days ago :D

I fixed it, and in case you have the same problem as me:

remember to select the session type on the login screen as KDE, not GNOME.

---

### Post by Raeth on 2005-07-13
And remember: You don't need to reboot. You can use "sudo /etc/init.d/gdm stop" then "sudo kdm" or "sudo /etc.init.d/kdm start" to change the desktop managers.

---

### Post by E-Buzz on 2005-07-14
Hi dudes. I also want to use kdm instead of gdm and follows the above steps with success until i get to the login screen (kdm). I type in my username, password and makes sure KDE is the chosen session. After that the screen turns black for a few seconds, as usual, but then, all of a sudden, i gets bounced back to the login screen instead of starting KDE. Any idea what i've missed here?

---

### Post by varunus on 2005-07-14
That's weird...

Can you log into KDE from GDM?  Or does it do the same thing there?

---

### Post by E-Buzz on 2005-07-14
[QUOTE=varunus]That's weird...

Can you log into KDE from GDM?  Or does it do the same thing there?[/QUOTE]

Good question, should have provided that info too  :grin: 

Yes, logging in from GDM works flawlessly.

---

### Post by CalleKubuntu on 2005-07-18
Knome_Fan wrote:
*********************
Also, if you really want to switch permanently, you probably want to change the display manager (that is essentially the login screen) from gdm to kdm.

To do that just change gdm to kdm in /etc/X11/default-display-manager
**********************

I tried to do that, but what I end up with is a text login, and then I have problems starting a graphical manager. That is after I reboot the machine. 

What exactly should I do to get that KDE display manager?
I searched for "kdm" on my system and found only folders.

Thanks
CalleKubuntu

---

### Post by Knome_fan on 2005-07-18
[QUOTE=CalleKubuntu]Knome_Fan wrote:
*********************
Also, if you really want to switch permanently, you probably want to change the display manager (that is essentially the login screen) from gdm to kdm.

To do that just change gdm to kdm in /etc/X11/default-display-manager
**********************

I tried to do that, but what I end up with is a text login, and then I have problems starting a graphical manager. That is after I reboot the machine. 

What exactly should I do to get that KDE display manager?
I searched for "kdm" on my system and found only folders.

Thanks
CalleKubuntu[/QUOTE]

Hi,
first off, make sure that kdm is installed.
After logging in do a sudo apt-get install kdm.

If it is indeed installed you should have a binary in /usr/bin, that is /usr/bin/kdm.
If this is the case you can try to start it with /etc/init.d/kdm start.

And of course make sure that etc/X11/default-display-manager is setup right, in case of kdm it should contain one line:
/usr/bin/kdm

Hope this helps!

---

