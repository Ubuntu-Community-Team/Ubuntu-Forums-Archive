---
title: "Compiz Needs to be Restarted Every Login"
date: 2009-05-20
forum: Desktop Environments
---

### Post by jpoRS on 2009-05-20
Hello,

Running a fresh install of Juanty on a System 76 Pangolin, and for some reason every time I log in I need to restart Compiz (from the Fusion Icon menu) in order to get it working.  I have also noticed that my Gnome-Do theme needs to be reset as well.

Sorry if this isn't enough information, I just don't know what you need to know.

Thanks,
jim

---

### Post by jpoRS on 2009-05-20
Anybody?

---

### Post by Wolfhere on 2009-05-20
Have you tried creating the compiz in your sessions? 
The command line should be compiz --replace

---

### Post by jpoRS on 2009-05-21
Wow.  Sometimes simple solutions are best. Why didn't I think of that?

Thanks!
jim

---

### Post by cyberscribe on 2009-05-22
The "solution" presented above works, of course, if you are willing to do this after every reboot or login, but it does not address - or fix - the basic underlying problem: having to restart Compiz (by selecting "Reload Window Manager" from the Compiz Fusion Icon option menu in the the notification area of the task bar) every time you reboot or log in.

I've had this same problem ever since Gutsy.  Every time I reboot or log in the Compiz Fusion Icon is present in my tray, but Compiz is not actually enabled.  I have to restart Compiz by selecting "Reload Window Manager" from the Compiz Fusion Icon option menu in the the task bar every time I reboot or log in -- if I don't, then I'm just running plain old GTK/Metacity with the default theme, etc.

Once I restart Compiz by selecting "Reload Window Manager" from the Compiz Fusion Icon option menu everything is fine again -- but I have to do this every time.

Is there no "fix" for this?

Thanks in advance for any help with this problem.

---

### Post by GOfree on 2009-05-22
I really like the Compiz Fusion Icon.

Most of the time, I don't need Compiz-Fusion and just run on Metacity. If I want to play with Compiz, then I turn it on.

It is only a matter of two or three mouse clicks if you have the icon permanently in the notification area of the gnome panel.

To have the icon start automatically, you may have to add it to the gnome sessions preferences.

- System > Preferences > Sessions
- Startup Programs > Add
- Name: Compiz Fusion Icon
- Command: fusion-icon --no-start

This will at least save you the trouble of starting the icon every time.

---

### Post by cyberscribe on 2009-05-22
Thanks for the very prompt reply GOfree, however...

There is no "Sessions" option under "System > Preferences" in Jaunty (9.04) -- menu items go from "Search and Indexing" to "Sound" -- there's no "Sessions" at all.

There is a "StartUp-Manager" under "System > Administration" but it offers no way to set the command you suggested.

Any other ideas?

- - - - - - - - - - - - - - - - - - - -

Update:  After snooping around a bit more I discovered that Jaunty has a "System > Preferences > Startup Applications" rather than the old "Sessions" - and both apparently do the same thing, I guess, since I can add switches (command line options) to "Compiz Fusion Icon" by using the "Edit" feature in "Startup Applications".

I discovered that "*Command: fusion-icon*" actually had "*Command: fusion-icon **-n***" in there for some reason (maybe as a result of my attempting to fix this problem a couple of Ubuntu generations ago?) and by deleting the "-n" switch and just leaving "fusion-icon" with nothing else following it, Compiz now starts up properly upon boot again!  Yay!

It looks like I probably caused my own problem quite some time ago, and the Compiz-Fusion Icon config somehow remained unchanged over at least two upgrades.

Thanks for getting me thinking about this persistent problem though; it's finally working the way it should once again!

---

### Post by GOfree on 2009-05-22
cyberscribe,

I don't want to steer you wrong, so I should let you know that I am not using Jaunty, but Debian 5.0.

Still, the gnome menus should be similar...

"Sessions" should be in the "Preferences" menu. If it isn't then it might be hidden.

Try this:

- System > Preferences > Main Menu
- In the left side bar, navigate to the Preferences menu
- When you select the preferences menu, you should get a list of all the possible menu items, shown in the main window
- If you find the listing for Sessions, make sure the box is checked

---

### Post by GOfree on 2009-05-22
BTW,

It should be possible to start compiz immediately with the sessions options, as someone noted earlier... but I haven't had any success yet :(

---

### Post by cyberscribe on 2009-05-22
@ GOfree:

I don't know if you noticed what I added by editing my previous comment; have a look above.

In Jaunty there's no longer any "Sessions" item, but the new "Startup Applications" seems to serve the same purpose.

Simply putting "*fusion-icon*" - *and nothing else* - in the "Command: " line of "Compiz Fusion Icon" under System > Preferences > Startup Applications DOES start Compiz when you reboot or log in.

Since I want Compiz up and running after each reboot/login, that fixed the problem for me.  Thanks a bunch for setting me back on the right track toward finding a solution!

---

### Post by cyberscribe on 2009-05-22
Let me just summarize what I've leaned, just in case I've inadvertently confused anybody that may be reading this:

- - - - - - - - - - - - - - - - - - - -

IF you want Compiz-Fusion to start automatically every time you reboot or login (on Jaunty) just search for and install "**fusion-icon**" using the Synaptic Package Manager.

After installing "fusion-icon" go to *System > Preferences > Startup Applications*

In "*Startup Applications*" just check the box next to "*Compiz Fusion Icon*" if it's present. If it's not present you can just "+ Add" it yourself, and fill in the fields as follows:

Name: Compiz Fusion Icon
Command: fusion-icon
Comment: Compiz Fusion Icon Autostart

Reboot, or log out and then log back in again and Compiz will automatically start up too.

For those that may be interested, there is also a "Compiz-Switch" that can toggle Compiz on and off, as you desire.  More on that here:

[http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/](http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/)

---

### Post by jpoRS on 2009-05-24
> **Wolfhere said:**
> compiz --replace

Cyberscribe: if you put this in startup applications, it automatically restarts Compiz and thus (for me anyway) fixes the problem.  Makes my processor work a little harder on boot but it will work.

Good luck!
jim

---

### Post by kristijandz on 2009-05-24
> **cyberscribe said:**
> Let me just summarize what I've leaned, just in case I've inadvertently confused anybody that may be reading this:

- - - - - - - - - - - - - - - - - - - -

IF you want Compiz-Fusion to start automatically every time you reboot or login (on Jaunty) just search for and install "**fusion-icon**" using the Synaptic Package Manager.

After installing "fusion-icon" go to *System > Preferences > Startup Applications*

In "*Startup Applications*" just check the box next to "*Compiz Fusion Icon*" if it's present. If it's not present you can just "+ Add" it yourself, and fill in the fields as follows:

Name: Compiz Fusion Icon
Command: fusion-icon
Comment: Compiz Fusion Icon Autostart

Reboot, or log out and then log back in again and Compiz will automatically start up too.

For those that may be interested, there is also a "Compiz-Switch" that can toggle Compiz on and off, as you desire.  More on that here:

[http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/](http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/)

Thank you, I need this. ;)

---

### Post by daddypawid on 2009-06-05
Ok.... I need some help on this... See I had compiz runnig no prob and on start up... Then  wanted to play around with emerald an to set some transparency... Did and well.. great..

But douring this I messed up something... I followed the advice of someone and went to system-->preference-->apperance... then I went and put on visual effects and from then on compiz doesn't run...

I did: compiz --replace   didn't work

I removed. restarted and reinstalled Compiz fusion... didn't work

Now I run the compiz fusion icon and it works but it is way slower than before....

---

### Post by mister_playboy on 2010-02-01
> **cyberscribe said:**
> Let me just summarize what I've leaned, just in case I've inadvertently confused anybody that may be reading this:

- - - - - - - - - - - - - - - - - - - -

IF you want Compiz-Fusion to start automatically every time you reboot or login (on Jaunty) just search for and install "**fusion-icon**" using the Synaptic Package Manager.

After installing "fusion-icon" go to *System > Preferences > Startup Applications*

In "*Startup Applications*" just check the box next to "*Compiz Fusion Icon*" if it's present. If it's not present you can just "+ Add" it yourself, and fill in the fields as follows:

Name: Compiz Fusion Icon
Command: fusion-icon
Comment: Compiz Fusion Icon Autostart

Reboot, or log out and then log back in again and Compiz will automatically start up too.

For those that may be interested, there is also a "Compiz-Switch" that can toggle Compiz on and off, as you desire.  More on that here:

[http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/](http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/)

I'm not sure why I just started having this problem... but this solved it!  Thanks.

---

### Post by ben2talk on 2012-09-10
To be honest, I can see several areas where people can become confused following instructions here.

Installing Gnome-Do, or Synapse (my current favourite) launchers makes life just soooo much easier.

Instead of playing around in silly menu systems, just type in 'start' and choose the most likely candidate that fits the bill. I have little idea of the content of my menu since I started using Gnome-Do. The same applies on my phone, the same applied with Vista (laughable that even that came with a 'hit key and start typing to find anything') etc...

I have both running simultaneously on my system, and noticed no issues as yet - I was going to remove one, but I'm a bit lazy...

Anyway, thanks for the tip - I had '--no-start' on my fusion icon startup.;)

---

