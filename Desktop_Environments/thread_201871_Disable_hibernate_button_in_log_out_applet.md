---
title: "Disable hibernate button in log out applet"
date: 2006-06-22
forum: Desktop Environments
---

### Post by StickyStyle on 2006-06-22
I am setting up some locked down user stations and have susceded in removing the shutdown and reboot buttons from the log out button applet and changing the perms for /sbin/halt so normal users cannot execute the program.  Also I have made it so that the 'lock screen' button in the log out applet does nothing using various resoruces found with google.

But i cannot seem to disable the 'hibernate' button in the log out applet ](*,) 
I found in the gconf-editor apps-> gnome-power-manager->action_button_hibernate and set it to 'nothing' as the description mentions, but users can still hibernate the machine.  Does anyone know how to remove that button, or at least make it do nothing when clicked?  Idealy i would like the 'hibernate' and 'lock screen' gone leaving only 'log out' and 'switch user.

?

---

### Post by tonyr on 2006-06-22
A brute force method:

Edit /**etc/acpi/hibernate.sh** and add **exit** as the second line (first line
after the **bash** header).  On my machine, selecting the Hibernate button
then at first acts like it's going to work, but then drops to the lock screen window.
I don't know what the effect will be for you, since you have lock screen disabled, too.

There is another script, **/etc/acpi/hibernatebtn.sh**, that appears to map the
Hibernate button to something else, a key event maybe?  You could explore that, too.

---

### Post by StickyStyle on 2006-06-22
Thank you, that did work :-)

However I educated myself a little more on gconf and learned that i needed make the settings i was using to be 'manditory' settings, then the suspend button whent away :-D 

I will be leaving the exit statement in the shell script though just incase.

---

