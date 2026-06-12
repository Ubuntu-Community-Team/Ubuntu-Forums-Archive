---
title: "Gnome splash screen background color"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by lhabjane on 2007-07-03
When my system is loading (after logging in) I get an orange background for one second, then I get gnome splash screen loading components, and then I get my regular background color. The problem is that everything in my system is blue except the background for that one or two seconds? Does anyone have an easy solution for this?

---

### Post by hysteresis on 2007-07-03
Its in system-administration-login window-local. right under gdm themes. at least I think thats it. I'm not near my linux machine.

---

### Post by lhabjane on 2007-07-03
How the heck I missed that! Thanks!

---

### Post by NoTownKasper on 2008-04-09
Ok...I've got the same issue, except the login-window setting, under System>Administration didn't change it at all...any suggestions? Ubuntu 7.10, good ol Gusty.

Ok, just tried again with a new color scheme/window theme/login-window configuration, none of them fixed the problem...and I'm trying to set up a demonstration with this here...showing Ubuntu off to some of my programmer frinds, ya know? :(

---

### Post by Lantesh on 2008-04-10
Ok here is what you need to do.  First there is the colored splash screen that comes up before the logon/password screen, and then there is another colored splash screen that comes up after the logon/password screen.  So you need to make two changes.  One is an easy GUI change.  The other requires using gedit in the terminal.  Here ya go:

How to Fix the color of the two Splash Screens


For the first splash screen that comes up before the login screen:


Go to Applications/System/Administration/Login Window. Click the “Local” tab and you will see a box where you can change the color. Make note of the color you choose.


For the second splash screen that comes up after the login screen:


Type in this command in the Terminal: sudo gedit /etc/gdm/PreSession/Default


Look for:


# Default value

if [ "x$BACKCOLOR" = "x" ]; then

BACKCOLOR="#dab082"

fi


Change “#dab082” to the same color you used for the first splash screen in the Login Window manager.

---

### Post by m4dm4n on 2008-04-10
This fix works fine, but it shows the colour over the top of my custom splash screen for gnome. I arrive at the login screen, enter my details and the splash screen is displayed until it gets to "loading nautilus" (around 2 seconds) and then the splash disappears leaving just the solid colour I set as my background. Its not a major problem but its a little annoying, is there a fix for this?

---

### Post by Lantesh on 2008-04-10
Sorry what I posted above is pretty much all the info I've got.  The only other thing I can think of, and I'd assume this setting is already active for you, is to try this:

In terminal enter command:  gconf-editor
Go to Apps -> gnome-session -> Options-> and see if "splash screen" is checked

---

### Post by m4dm4n on 2008-04-10
The splash is turned on since it displays for a second, but it disappears as soon as compiz has loaded (I can see it loading in the splash). I suspect its something to do with compiz as I've seen it mentioned before but I haven't been able to find any fixes for it. As I said, not a major problem, just a minor annoyance.

---

### Post by Lantesh on 2008-04-11
Well good luck with it, and post back in this thread if you figure it out.  I'm curious to know.

---

