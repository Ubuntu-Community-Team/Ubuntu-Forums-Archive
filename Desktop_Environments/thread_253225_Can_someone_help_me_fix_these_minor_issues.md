---
title: "Can someone help me fix these minor issues"
date: 2006-09-08
forum: Desktop Environments
---

### Post by NoTiG on 2006-09-08
THe first one is that my sound is divided. Im on a laptop... and I have usb logitech headphones plugged in.... and sometimes the sounds go out through the speakers, and sometimes through the headphones. Like the GDM session manager before gnome boots up.. the sound goes through the speakers... but once gnome starts loading... then it goes through headphones. how do i control this so it all goes through the headphones?

Another thing.... my mouse is only detected about half the time. its a plain usb mouse. windows detects it fine so i know its not a malfunctioning port. The way i fix it is by restarting. Is there a way to fix this, and if not is there a way to reset it without having to reboot all the way?

One more thing.. Some dvds i can play ... but this one i just got "Casanova" wont work.. the cdro just starts spinning and going crazy and totem loads but doesnt start playing it. Windows plays it fine. any ideas ?
when i insert the cd.. i can here the dvd speeding up and slowing down and speeding up and slowing down constantly. and it seems "busy" . and when i hit the eject button it keep sdoing it and ignores me... and i try to eject from the GUI by right clicking and it still ignores me. its annoying >< . totem loads.. and it says "now playing" and it displays the correct length of time the movie is...... but it never starts.  I have libdvdcss installed annd all that.

one more thing...... My wireless is set up to use ndiswrapper. However if i do ndiswrapper -e and write the configuration  to /etc/modprobe.d ... It hangs when it loads gnome. So i basically always have to type that command in before i can use the internet. argh. ANy ideas?

thats all for now hehe. if i can even get one of these problems fixed ill be happy.

Ps. oh yea.. i sthere a way to change the touchpad settings? its REALLY sensitive and i cant even navigate with it because its constantly clicking. way to sensitive. and sometimes i want to disable it so my wrists dont set it off while i type.

---

### Post by CatKiller on 2006-09-08
> **NoTiG said:**
> Another thing.... my mouse is only detected about half the time. its a plain usb mouse. windows detects it fine so i know its not a malfunctioning port. The way i fix it is by restarting. Is there a way to fix this, and if not is there a way to reset it without having to reboot all the way?I'd guess that it's a problem with your X configuration. I don't know enough about it to offer suggestions to fix it, but in the meantime you can Ctrl-Alt-Backspace to kill and restart the X server - it means that you don't need to restart the computer all the way. It might find the mouse again for you.

---

