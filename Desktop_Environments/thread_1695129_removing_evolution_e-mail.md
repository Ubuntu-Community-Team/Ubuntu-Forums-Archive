---
title: "removing evolution e-mail"
date: 2011-02-25
forum: Desktop Environments
---

### Post by wilander on 2011-02-25
ive removed the program evolution e-mail from my system. But still there is an icon from it in the panel up-right. I tried to remove it, but then it also removed my sound button! Its wierd. And i dont know how i can get rid of the icon without removing other buttons. What is the easiest way to modify my panel buttons?

---

### Post by jimmyjones on 2011-02-25
I use Thunderbird, and removed Evolution.

the icon is for the Indicator Applet, not Evolution.

I installed Cloud Services Notifications, (I found the instructions on the forum) and mapped it to the icon so that it was doing something.

Works for me


[http://chuchiperriman.github.com/cloud-services-notifications/](http://chuchiperriman.github.com/cloud-services-notifications/)


[http://ubuntuforums.org/showthread.php?t=1439519&highlight=cloudsn](http://ubuntuforums.org/showthread.php?t=1439519&highlight=cloudsn)

---

### Post by wilander on 2011-02-25
ok.. i dont quite understand. how will this make me able to _remove_ the icon? Im not interested in evolution or the thunderbird. I dont want a e-mail program on my computer.

The icon is not indicator apple i think (dont know what that is..), because when i click it it tries to open evolution...

---

### Post by jimmyjones on 2011-02-25
Sorry, I misunderstood your intent.

The mail icon is part of the Indicator Applet, I believe it's all or nothing.

edit to add:

Found this link, haven't tried it.

Remove Evolution Mail Notifier from Indicator Applet in Ubuntu&#8217;s System Tray

[http://ubuntugenius.wordpress.com/2010/05/04/remove-evolution-mail-notifier-from-indicator-applet-in-ubuntus-system-tray/](http://ubuntugenius.wordpress.com/2010/05/04/remove-evolution-mail-notifier-from-indicator-applet-in-ubuntus-system-tray/)

---

### Post by jimmyjones on 2011-02-25
Ok, I tried it and it worked.

I'd already un-installed Evolution so I got a not installed error from the first command in the link.


All I did then was in the terminal:

sudo apt-get remove indicator-messages

answered 'y'

Then 

killall gnome-panel

after a few seconds the gnome panels returned sans the email icon !

All the other icons still function, wireless, blutooth, battery and volume.

Did it on 3 different systems same results, cool, I've been trying to get rid of it for awhile.

---

### Post by wilander on 2011-02-25
thanks so much for the site, now its solved! :-P

---

### Post by jimmyjones on 2011-02-25
Cool, glad I could finally help someone.



I've gotten enough help here, finally able to give something back.

---

