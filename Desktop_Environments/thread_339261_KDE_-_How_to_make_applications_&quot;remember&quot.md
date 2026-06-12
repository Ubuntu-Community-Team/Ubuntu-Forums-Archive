---
title: "KDE - How to make applications &quot;remember&quot; screen position"
date: 2007-01-15
forum: Desktop Environments
---

### Post by stormyuk on 2007-01-15
Hi,

In Kubuntu, does anyone know how I force applications to remember where they where closed or positioned on the screen? They seem to have a mind of their own and wander all over the place, usually top right or bottom right.

Is it by application or some other way as its pretty much all my applications doing it, amarok, firefox, konqueror etc etc..

Cheers,

Mike

---

### Post by stormyuk on 2007-01-16
Does a lack of response suggest something is wrong with my system and KDE should do this automatically or sth?

Its really beginning to bug me, everytime I open applications they open in the top left or bottom right of the screen and not where I had them positioned before.

:(

---

### Post by loell on 2007-01-16
i once tried kde before, and it does remember window position.
if its systemwide then there is something wrong with your kde window manager, i guess.

---

### Post by stormyuk on 2007-01-16
Hi,

Is there anyway to fix it or re-initialise the KDE window manager?

Thanks,

Mike

---

### Post by Extreme Coder on 2007-01-16
I have the same problem, so I can't help but confirm I have the exact same problem. Everytime I open a new app, it opens in one of the four corners. I will be watching this thread if a solution appears.

---

### Post by stormyuk on 2007-01-17
Hi,

A bit of an update, with the help of a guy from the kubuntuforums.net I managed to "understand" the behaviour but unfortunately there seems to be no fix or at least to my mind an easy work around.

The default settings try to place windows 'smartly' out of each other way which is why it puts them in the four corners, to my mind thats not exactly smart.  You can  edit the settings going to systemSettings>WindowBehaviour.

The general setting can be found in 'WindowBehaviour>Moving>Placement', and for individual application its possible to create a rule in 'Window-Specific Settings'.

It looks like for me that would be a bit time consuming and user intensive, its one negative I have found in my effort to move from Windows XP to a Kubuntu. Maybe one day it can be something implemented like Windows? Is there a way to request such features of the developers?

Cheers,

Mike

---

### Post by oobuntoo on 2007-01-17
> **stormyuk said:**
> Hi,

In Kubuntu, does anyone know how I force applications to remember where they where closed or positioned on the screen? They seem to have a mind of their own and wander all over the place, usually top right or bottom right.

Is it by application or some other way as its pretty much all my applications doing it, amarok, firefox, konqueror etc etc..

Cheers,

Mike

It's very easy to make window remember previous position in KDE.

For each application:

Right click on a window's title bar -->Advanced -->Special Application Settings...
Put a tick mark before "Position"
On the drop-menu, choose "Remember"
Click OK.


For system wide:

Open up "System Setting", select "Window Behavior", select "Moving" tab
On the drop-down menu next to "Placement", choose something else other than "Smart"
Strangely, KDE developers did not implement "Remember" option under this drop-down menu.

---

### Post by stormyuk on 2007-01-17
Ahh that sounds great, I will check it out later when I am home.  Will the "Special Application Settings" override that of the "smart" in "window behaviour"?

Thanks very much oobuntoo!

---

### Post by Extreme Coder on 2007-01-17
Passed by again to say thank you oobuntoo! Centered placement is much better, and if I need to place the window somewhere strange, I will play with the Special Application Settings.

---

### Post by oobuntoo on 2007-01-17
> **stormyuk said:**
> Ahh that sounds great, I will check it out later when I am home.  Will the "Special Application Settings" override that of the "smart" in "window behaviour"?

Thanks very much oobuntoo!

Your're welcome!
Yes, "Special Application Settings" overide everything.

---

### Post by maniaq on 2008-05-06
yeah that's great except - for me - I can't get any of those settings to stick!

the Advanced Settings on the title bar, I click on OK and the dialog box disappears - and then if I go BACK into the same Advanced Settings, my changes have gone - like they never happened...

same deal with the system-wide "Window Behaviour" - I create a new Window-Specific setting, give it a name and all, I close up System Settings, I open it back up again and my new setting has been "disappeared" - like it never happened...

---

### Post by acl123 on 2008-05-06
Can I do something like this in Gnome?

I've been using Compiz to set the size and positions of Windows, but I don't always have Compiz running.

---

