---
title: "Can't get back to Ubuntu Classic"
date: 2011-05-12
forum: Desktop Environments
---

### Post by kansas_plainsman on 2011-05-12
I've gotten tired of Unity and want to go back to Ubuntu Classic - but selecting it during the log-in process has no effect (except that there's an additional bar across the bottom)  The Unity app menu down the left side of the screen is still there.

Am I missing something?  Or is something broken?

---

### Post by Rasa1111 on 2011-05-12
Not sure..

but maybe try changing to classic from the login screen after your already logged into your desktop. 
Instead of before you login. 

So you would search (in Dash), "login screen"
When you see it, Open it, choose classic as default, then log out and back in. 

Hope it helps.
But Im unsure if it will.. lol

Good luck.

---

### Post by kansas_plainsman on 2011-05-12
Hum.  Tried selecting Ubuntu (no effects) and that got me the "standard" gnome environment - left a few icons in the bar blanked but otherwise working again.

Not sure what the difference is between the two options.

Thanks for the suggestion.

Oops.  The two blank icons were for OpenOffice - and it's not there anymore!

---

### Post by shashanksingh on 2011-05-12
First log-on to classic, open a terminal and run

sudo apt-get remove unity

this should remove unity,

then when you log in as ubuntu-classic, it should work fine.

again remove unity and check if you have the gnome-panel

sudo apt-get install gnome-panel

---

### Post by encefalocardia on 2011-05-12
Just purge Unity

---

### Post by mcduck on 2011-05-12
No need to remove or purge anything just because of that. :D

It's simple, actually: Selectign the "Classic Gnome"-session will load Gnome with Compiz as window manager (if your system is detected able to handle Compiz, just like in previous Ubuntu versions you get effects if your system can  do them). On the other hand Unity is a Compiz plugin, and enabled by default (since it needs to be that way for the Unity desktop to work).

So all you need to do to get rid of Unity in Classic Gnome (with Compiz) is open CompizConfig Settings Manager and disable the Unity plugin.

(selecting "Ubuntu (no effects)" will load classic Gnome with Metacity as window manager. No Compiz, so no Unity no matter it the plugin is enabled or disabled in Compiz settings)

---

