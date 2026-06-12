---
title: "Crazy ubuntu"
date: 2012-08-24
forum: Desktop Environments
---

### Post by blackmail on 2012-08-24
Ok, so the thing is that lately many applications just crash for the fun of it, and after restarting them they work, like docky, cairo dock newly, pidgin, thunderbird, and also if i leave my computer alone it locks itself, but lately, the screen remains either black and only the lock sign is displayed, and no password prompt, or the screen is white-ish, i can see the open windows but it all appears whitened as if i would have the backlight set to 400%, and it doesn't react, the cursor moves but it doesn't react to show a password prompt or something...
How could i start solving this problem...

also lately i cannot install updates, the only way it works is with the:
sudo apt-get dist-upgrade command, i have 12.04 installed...

---

### Post by grahammechanical on 2012-08-25
In System Settings>Brightness and lock you can set Turn Screen Off to Never and also set Screen Lock to Off.

Does this not work on your machine?

Regards.

---

### Post by blackmail on 2012-11-02
sorry for the really really late reply, the problem was not with the brightness, it was some service that i had to disable, so when resurrecting my omputer from suspend, i have to go ctrl+alt+F2 and just disable a servic and after doing this several times it just stopped, the screen was only white and nothing on it, it was not a brightness peoblem. To anyone who has the same problem and don't want to restart the computer a solution would be do stop lightdm and then start it back again, so ctrl+alt+F2, after that enter your user and password.

then go type:

sudo /etc/init.d/lightdm stop

and then again

sudo /etc/init.d/lightdm start

and the login window should appear if not just hit the ctrl+alt+F7 combination
Cheers

---

