---
title: "Map Super Key to Win Key for Compiz?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by vf514 on 2006-09-14
I used to be able to do this through System > Preferences > Keyboard. Now, I don't see the menu to change the Win Key settings anymore. Have things changed recently?

My specific problem is that Super Key + Mouse Wheel will not zoom in/out if I do not have the Super Key mapped to the Win Key.

---

### Post by blakesmith on 2006-09-14
goto System > Preferences > Keyboard>Layout Options>Alt Win key behaviour> SUper mapped to winkeys (default)

---

### Post by angkor on 2006-09-14
It's still there I think in System -> Preferences -> Keyboard -> Layout Options -> Alt/Win key behaviour.

---

### Post by codejunkie on 2006-09-14
> **vf514 said:**
> I used to be able to do this through System > Preferences > Keyboard. Now, I don't see the menu to change the Win Key settings anymore. Have things changed recently?

if your using compiz you have to use **System/Preferences/Compiz Settings Manager** open the settings manager then on the left side click on **General Options** then click the tab on the right that says **Commands** enter the command you want to run say ***gnome-terminal*** to open a terminal in ```
Command line 0
```then to set a key to it click on Keyboard scroll down till you find **run command 0** and under **Key Name:**enter ```
Super_L
```for to use the left windows key or ```
Super_R
``` to use the right windows key hope this helps.

---

### Post by vf514 on 2006-09-14
> **angkor said:**
> It's still there I think in System -> Preferences -> Keyboard -> Layout Options -> Alt/Win key behaviour.

My Layout Options dialog is blank...

I will try codejunkie's idea.

---

### Post by vf514 on 2006-09-14
Codejunkie, I want to be able to zoom in and out by pressing the Win Key and moving the mouse wheel, not execute a specific command.

I apologize; I should have been clearer.

---

### Post by codejunkie on 2006-09-14
> **vf514 said:**
> Codejunkie, I want to be able to zoom in and out by pressing the Win Key and moving the mouse wheel, not execute a specific command.

I apologize; I should have been clearer.

This might fix it, on mine on a standard Ubuntu install with no Xgl/Compiz the keyboard is listed as a Generic 104-key PC keyboard in **System/Preferences/Keyboard** and all the special keys work properly.

when i install Xgl/Compiz it changes it to a Generic 101-key PC in **System/Preferences/Keyboard** for some reason and my windows and media keys no longer work, whether I'm using a standard X session or Xgl.

after i install xgl i always go into System/Preferences/Keyboard and change it back to a Generic 104-key PC keyboard and everything works fine in Xgl and a  standard X session. 

after you change the keyboard settings and switch from a Xgl to the standard X session you'll get a warning box saying that you've your keyboard settings have changed it will ask if you want to use the gnome settings or the xorg.conf/xserver settings, set it to use gnomes keyboard settings and all your keys should work like normal.

---

### Post by vf514 on 2006-09-15
I'm looking through System > Preferences > Keyboard and I'm not seeing Generic *-Key PC anywhere. -___- The field labled "Keyboard layout" under layout contains the string "Unknown" and when I try to add a model, I am offered no options. Strange!

---

### Post by vf514 on 2006-09-16
I was able to resolve the issue by reassigning the zoom shortcut to Alt + Shift + <mousewheel>. Hopefully, the keyboard issue will be resolved eventually.

---

