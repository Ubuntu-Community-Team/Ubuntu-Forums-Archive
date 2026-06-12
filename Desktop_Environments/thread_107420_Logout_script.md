---
title: "Logout script?"
date: 2005-12-23
forum: Desktop Environments
---

### Post by quietglow on 2005-12-23
Can someone give me some info on the nature of the logout button in the System menu?

Does the button trigger a script? If so, where does the sucker live?

I'd like to have the power button on my laptop activate that command, and I was hoping to point the /etc/acpi/events/powerbtn to whereever that command lives.

Thanks!

---

### Post by quietglow on 2005-12-23
anyone? just need to know where the script is...I'm looking and can't seem to find it. I'm not sure how I can figure out what command that button gives.

---

### Post by briancurtin on 2005-12-23
i believe you want to look for the .bash_logout script in your home directory. im sorting through a few google results right now to see if anything worthwhile comes up

im really not sure if that even has anything to do with it, i just know that .bash_logout runs when you shut down. it could be associated with what you want to do.

---

### Post by cwaldbieser on 2005-12-23
[QUOTE=quietglow]Can someone give me some info on the nature of the logout button in the System menu?

Does the button trigger a script? If so, where does the sucker live?

I'd like to have the power button on my laptop activate that command, and I was hoping to point the /etc/acpi/events/powerbtn to whereever that command lives.

Thanks![/QUOTE]
You can just have it run a script that does
```

shutdown now

```
That will stop all processes and shut down the system.

---

### Post by briancurtin on 2005-12-23
you could have it call "init 0" - halting the system

(it might be init 6, one is halt one is reboot, i cant exactly remember which is which)

edit: damn i got beat

---

### Post by quietglow on 2005-12-23
Thanks all, but I don't want it to shutdown, I want it to give me the nice menu that comes up when you select "log out" when I press the button. Its actually set to just shut down now--that's controlled in the script here: /etc/acpi/events/powerbtn

---

### Post by cwaldbieser on 2005-12-23
[QUOTE=quietglow]Thanks all, but I don't want it to shutdown, I want it to give me the nice menu that comes up when you select "log out" when I press the button. Its actually set to just shut down now--that's controlled in the script here: /etc/acpi/events/powerbtn[/QUOTE]
OK, I get it.  That might be a little tricky, because the power button will trigger a system-wide event, but you really want it to pop up a screen for the currently logged on user(s).

I am not sure there is really a seperate script for this?  Is GNOME your only Desktop, or do you also use KDE, XFCE, etc?

---

### Post by quietglow on 2005-12-24
I'm gnome all the way...leave it to me to ask the difficult and not crucially important :-)

The background is that for some reason the lid button of this machine doesnt map very well to the sleep script. I've set up 4 or 5 other laptops to do this, but this one seems to ignore the command to link the lid button and the sleep script. It sleeps just fine if you select it from the menu, but it would be nice if that menu could be triggered from a hardware single button. I love gnome, but I've never been able to get myself to work from menus for everything--my desktop and launchbar are full of icons. 

I sure do appreciate your help!

---

