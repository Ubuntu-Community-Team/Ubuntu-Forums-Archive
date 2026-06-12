---
title: "Missing window decoration"
date: 2009-01-24
forum: General Help
---

### Post by Sjellest on 2009-01-24
Hi there.
As the headline says, I'm missing the window decoration. Well i think its is come kind of error caused by myself. It seems that every time i launch a window it appears perfectly right for about 1/10 of a second then it gets maximized and looses the window decoration. I temporarily solved the problem yesterday when i pressed the "create a new layer" button 2 or 3 times rapidly in Gimp.

I'm sorry for my bad english, but i hope you understand it :p

---

### Post by Therion on 2009-01-24
I have a couple, possible, solutions...  Try this first (assuming you are running compiz):

Open CCSM: System/Preferences/Advanced Desktop Settings
Scroll down to the Utilities section and click on "Workarounds".
DE-select the box labeled **Legacy Fullscreen Support**.

See if that solves the problem...  If not, we'll need to use the Terminal to stop Emerald, most likely, from starting with compiz; which could also be causing this problem.

---

### Post by Sjellest on 2009-01-24
I didn't work. But then it's good that you have more solutions :)

---

### Post by Therion on 2009-01-24
Alright, time to pull out the big gun:

Open a Terminal and enter: ```

mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```
You may need to log out (Ctrl + Alt + Backspace) and log back in for this be made effective.

---

### Post by Yashiro on 2009-01-24
Boot up into your desktop.
Press Alt+F2.
Type *gnome-appearance-properties* press enter.
Go to Visual Effects and set it to None.
Reboot.

Use your desktop as you normally would. If the error does not return then it is Compiz desk effects related. Therefore you could try the methods suggested above if you want to fix compiz.

If the problem continues with Compiz disabled though, post back with results.

---

### Post by Sjellest on 2009-01-24
> **Yashiro said:**
> Boot up into your desktop.
Press Alt+F2.
Type *gnome-appearance-properties* press enter.
Go to Visual Effects and set it to None.
Reboot.

Use your desktop as you normally would. If the error does not return then it is Compiz desk effects related. Therefore you could try the methods suggested above if you want to fix compiz.

If the problem continues with Compiz disabled though, post back with results.

I tried this but the errors continued.

---

### Post by Sjellest on 2009-01-24
> **Therion said:**
> Alright, time to pull out the big gun:

Open a Terminal and enter: ```

mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```
You may need to log out (Ctrl + Alt + Backspace) and log back in for this be made effective.

Then i tried this but no improvements. Well actually some of the windows that before got maximized didn't anymore with compiz off... I'm confused bur i hope some of you can solve this... :)

---

### Post by Yashiro on 2009-01-24
Ok, so you've got these problems whether desktop effects are on or off. Yes?

What theme are you using on your Windows? If it's the default Human theme. Try Clearlooks.

---

### Post by Sjellest on 2009-01-24
1) Yes it true. It seems that the problems have nothing to do with the desktop effects... 

2) Im using the default Human theme right now, but i've just tried Clearlooks and some other and none worked. I also tried with emerald, but it did not work. 

But i cant figure out why it worked when i pressed the "new layer" button in Gimp...

---

