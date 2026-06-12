---
title: "Appearance Preferences keeps popping up at the login screen?"
date: 2011-04-09
forum: Desktop Environments
---

### Post by Dáire Fagan on 2011-04-09
Some time ago now under instruction I did something to make the *Appearance Preferences*  op up at the login screen so I could make some changes to it. This is the same *Appearance Preferences* usually accessed once logged in via *System* >> *Preferences* >> *Appearance* *Preferences*.

I cannot recall what I did exactly, can anyone tell me how to stop it popping up?

---

### Post by Frogs Hair on 2011-04-09
If this was a method to change the color of the greeter box and background there were different methods on the internet . The bottom line is you have find the correct instructions .

This is the command that came with the method I used and have no idea if it will work for you . ```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by Dáire Fagan on 2011-04-09
> **Frogs Hair said:**
> If this was a method to change the color of the greeter box and background there were different methods on the internet . The bottom line is you have find the correct instructions .

This is the command that came with the method I used and have no idea if it will work for you . ```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

Before I input that, is that the command to bring the settings up at login screen, or stop them coming up?

---

### Post by Frogs Hair on 2011-04-09
> **dusf said:**
> Before I input that, is that the command to bring the settings up at login screen, or stop them coming up?

It is the unlink command , and it was / is  used to remove the Appearance Preferences from the login window  after making changes according to the instruction I used.

---

### Post by Dáire Fagan on 2011-04-09
It did the trick, thank you friend :)

---

### Post by Frogs Hair on 2011-04-09
> **dusf said:**
> It did the trick, thank you friend :)

No problem , the last person that tried had no luck because the method they used was much different.

---

