---
title: "Unity systray rsibreak icon disappeared"
date: 2015-05-21
forum: Desktop Environments
---

### Post by Megan_Adams on 2015-05-21
hi everyone. 
I am using 14.04 on a chromebook via crouton. 

This is my second install. On the first I had no problem.

This time around the systray icon for rsibreak does not appear. I need this or I can't use the machine. I can't set up breaks without the icon. 

Aside from the no icon issue, I also get errors for rsibreak. The errors I get are:
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Gtk-Message: Failed to load module "canberra-gtk-module"

I am not sure if my rsibreak problem is related to disappearing systray icons in 14.04 or these messages. 

I tried fixing the messages:
I tried fix the first with [http://askubuntu.com/questions/487083/is-removing-ibus-enough](http://askubuntu.com/questions/487083/is-removing-ibus-enough)
It worked but had no effect. 
Then I did this:
sudo apt-get install libcanberra-gtk-module:i386
That worked but also had no effect. 
I am not sure if my rsibreak problem is related to disappearing systray icons in 14.04 or these messages. 

I also tried various techniques for whitelisting the rsibreak for the systray icon. 
[http://ubuntuforums.org/showthread.php?t=1737589](http://ubuntuforums.org/showthread.php?t=1737589)
[http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html](http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html)

Your help much appreciated. This is a deal breaker for me. 
thanks.

---

### Post by Megan_Adams on 2015-05-21
I got workrave to work. 
megan

---

