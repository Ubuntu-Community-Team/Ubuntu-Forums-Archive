---
title: "How do I fix my screen magnifier at login? Why can't I login with sticky keys?"
date: 2011-01-26
forum: Desktop Environments
---

### Post by chovynz on 2011-01-26
Solution for Ubuntu 10.10 GNOME desktop. Default installation.

This is more of a solution thread than a question. There are a number of other threads out there on how to fix your on screen magnifier and/or sticky keys. This is another way to fix it. We found this after getting desperate and trying things for a few hours.

[SIZE=5]The problem (or any number and combination of these) :[/SIZE]

[LIST]
[*]You're on the login screen
[*]The on screen magnifier wont go away.
[*]You can't see any universal access icon because the onscreen magnifier is blocking it (the icon is in the lower right of the login screen on GNOME desktop.)
[*]Universal access icon looks like this [IMG]http://img88.imageshack.us/img88/2126/64pxuniversalaccessicon.png[/IMG].
[*]Your sticky keys are on and you can't put your login password in properly
[*]The onscreen magnifer has a black background and won't display anything.
[*]the onscreen keyboard wont go away
[/LIST]
[SIZE=5]Solution 1.) Be able to Login and Fix Magnifier[/SIZE]

[LIST=1]
[*]**1.) (IF STICKY KEYS IS ON, AND MAGNIFIER, or onscreen KEYBOARD is visible)**
[/LIST]
[INDENT]
[LIST]
[*]First the trick is to log in. We did it by very slowly entering our login password.
[*]You should be able to see half of the screen, enough to click on your username and input your password.
[*]Remember : that if you have capitals in your password you will need to hold down shift for enough time for the key-press to be registered.
[*]It's easier if you can use the onscreen keyboard. Click the arrow-pointing-upwards shift button on the onscreen keyboard to switch to capitals. If onscreen keyboard is not visible then you will need to do this manually on your keyboard. press and hold shift for enough time for the key-press to be registered.
[*]type in your password and login.
[*]NOTE: You will not be able to click on "enter" with your mouse once you have input your password, because the onscreen magnifier is covering this part of the login window. **After typing your password into the password field, push and hold enter on your keyboard or click enter in the onscreen keyboard.** Hopefully it'll work as expected.
[*]**if just entering your password and pushing enter doesn't work,** you can use "tab" if need be to switch your focus field. From the password field it is, two "tabs". Now push enter. Cross fingers it works.
[/LIST]
[/INDENT]
[LIST=1]
[*]2.) SWITCH USER
[/LIST]
[INDENT]
[LIST]
[*]We don't know why this works, but we've found that it does. Once you are logged in, you need to switch user. It doesn't matter if you only have one user, once you get back to the login screen you will be able to see the universal access button.
[*]Switch user by clicking on the top-right power icon. It looks something like this: [IMG]http://img717.imageshack.us/img717/2903/powericon.png[/IMG]
[*]Choose switch user. You will be taken to the login screen with (hopefully) no onscreen magnifier interfering now.
[*]Right click this universal access button [IMG]http://img88.imageshack.us/img88/2126/64pxuniversalaccessicon.png[/IMG]
[*]Uncheck any options that are ticked.
[*]You will now be able to login as normal.
[/LIST]

[/INDENT][SIZE=4]Solution 2.)[/SIZE]
 [COLOR=Red]Edit: Unfortunatly this didn't work for us, but it might for you. Try it anyway.[/COLOR]
> **nomentero said:**
> Solution is very simple. Open  gnome-keyboard-properties, select tab Accessibility and deselect  "Accessibility features can be toggled with keyboard shortcuts".
[SIZE=4]
Solution 3.)[/SIZE]  
[COLOR=Red]Edit: Unfortunatly this didn't work for us, but it might for you. Try it anyway.[/COLOR]
> **Slats Grobnik said:**
> @duanedesign: Did you uncheck the "Virtual Assistance" checkbox under System -> Preferences -> Startup Applications? 
  Reboot.

[B][SIZE=5]Solution 4.) Uninstall the accessibilty preferences
[/SIZE][/B]
[LIST]
[*]Lets say you want to permantly stop the kids from playing with the onscreen magnifier. Here's how:
[/LIST]
> **themusicalduck said:**
> You can remove the magnifier program, I think, like this.

Boot Ubuntu in recovery mode from the grub menu. When it asks, pick to drop into root shell.

Run this command ```
apt-get remove gnome-mag
```Hopefully that'll  stop it magnifying on startup and you can go and take it out of the  startup applications if you want.
This has partially worked. I'll add more remov accessibilty preferences as I find them. I ran this command by opening a terminal and typing 
```
 sudo apt-get remove gnome-mag
```You can also do this by clicking System > Administration > Synaptic Package Manager. Search for gnome-mag. Mark it for Removal. Apply.

---

### Post by stinkeye on 2011-01-26
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```
Will turn the the magnifier off at the login screen.
Once you've done that, you can turn the rest off in the universal access menu.



You can also disable: (handy if you have kids)
screen_reader
screen_magnifier
screen_keyboard 

They will not be selectable in the universal access menu.
See--->[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10385617&postcount=13[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10385617&postcount=13")

---

