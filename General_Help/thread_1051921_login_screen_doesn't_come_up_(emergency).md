---
title: "login screen doesn't come up (emergency)"
date: 2009-01-27
forum: General Help
---

### Post by banana jama on 2009-01-27
Last night I downloaded a new theme from gnome-looks.com I wanted to change how the login screen look so I changed it. Now when I turn on my computer the login screen does come up just a brown screen with the pointer as a loading icon. How can I get my compouter to work without the ability to log in?  PLEASE HELP!!!!!!!!!

---

### Post by banana jama on 2009-01-27
Bump

---

### Post by tragicglee on 2009-01-27
I'm not positive this will solve your issue, but it's worth a shot until somebody else replies, and can be easily undone.


From the login screen, drop to a TTY (hit ALT + CTRL + F1 at the same time, if you don't know). Login, and issue the following commands.  

```

sudo /etc/init.d/gdm stop
cd /etc/gdm
sudo mv gdm.conf-custom oldgdm.conf-custom
sudo /etc.init.d/gdm start

```

I'm assuming the new GDM theme broke things, so we're stopping Gnome Dispay Manager, and moving your custom configuration so it isn't used, and then restarting the Display Manager. If login screen doesn't automatically come back after the last command, try hitting ALT + CTRL + F7.

If there's no improvement:

```
sudo /etc/init.d/gdm stop
cd /etc/gdm
sudo cp oldgdm.conf-custom gdm.conf-custom
ls /usr/share/gdm/themes
 [COLOR="Red"]pick a simple name from that list[/COLOR]
sudo nano gdm.conf-custom
 [COLOR="Red"] scroll down, find the line that reads GRAPHICAL THEME=some theme name.
  Remove that name, replace with the one you just picked
  (case sensitive, so type exactly as you Saw It) Hit CTRL + O
  to save, then exit nano[/COLOR] 
sudo /etc/init.d/gdm restart

```

Hopefully this helps

---

### Post by banana jama on 2009-01-27
it didn't work thanks for the suggestion. i had no choice but to install a second ubuntu so i could access all of my information. i just plan to make the second ubuntu my main distro and delete the other one when i get all my data off of it.

---

### Post by diablozx9 on 2009-02-07
Worked for me,,, THANKS,,
I got it fixed before the wife got home....

---

