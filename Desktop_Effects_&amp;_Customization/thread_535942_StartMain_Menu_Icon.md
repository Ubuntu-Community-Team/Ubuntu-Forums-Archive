---
title: "Start/Main Menu Icon"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by Dark Star on 2007-08-27
Hi all
Can any 1 tell me how to change the start button icon ? :) I have some lying arund but unable to change ..
Thanks in advance :)

---

### Post by P4oL1n0 on 2007-08-27
There are a lot of ways..... this is what I make to change the icon:
I take the current icon package that it's installed on Ubuntu, i rename my icon in "dtributor-logo.png" and I move it in /namepackage/scalable/apps/

Then i create an archive (.tar.bz2) making clic with the right button.
Now I install the new archive in Sistem--->Preference--->Theme (apparance in gutsy)

I hope to have helped you :)
Bye

---

### Post by Dark Star on 2007-08-27
I mean how to change the Main Menu / Start Button.. Which we click to open Menu :D In the eft side of taskbar :D ..Why to make .tar.gz ?:?

---

### Post by xopher on 2007-08-27
That's a pretty smart way of doing it + applying it ;)

I always just put the distributor-logo.svg/png into ~/.icons/*mycurrenticontheme*/scalable/apps

Then you have to ```
pkill gnome-panel
``` to apply it though..

---

### Post by Dark Star on 2007-08-27
Okies thanks :) to both of ya :D So I just put the logo and whats the use of second meathod :?

---

### Post by crash0 on 2007-08-27
the second method is using the configuration editor
go to apps -- nautilus -- panel -- default_setup -- objects -- menu_bar
(not 100% sure)

tick "use_custom_icon" and edit the custom_icon field to whatever the location of the icon is.

---

