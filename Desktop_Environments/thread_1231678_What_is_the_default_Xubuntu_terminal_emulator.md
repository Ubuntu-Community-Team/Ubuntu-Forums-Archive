---
title: "What is the default Xubuntu terminal emulator"
date: 2009-08-04
forum: Desktop Environments
---

### Post by jocampo on 2009-08-04
Hi

anyone know what's the name for the default XUbuntu Jaunty terminal emulator? it comes with 4 upper right buttons instead of the common 3 which are: close, minimize and maximize. bk is black with white text (default config of course) Planning to download or install that on my Ubuntu desktop

Thanks

---

### Post by aysiu on 2009-08-04
It's called ```
xfce4-terminal
```

---

### Post by wojox on 2009-08-04
xfce4-terminal - Xfce terminal emulator

---

### Post by jocampo on 2009-08-04
Thanks folks...but why I just google that and pictures show it with 3 buttons instead of 4 ... what I've seen so far is the one with: close, minimize and maximize. 

The one I'm talking about and would like to install has an extra button that make it look like a thin horizontal line on your screen ... is that the same one?

---

### Post by aysiu on 2009-08-04
> **jocampo said:**
> Thanks folks...but why I just google that and pictures show it with 3 buttons instead of 4 ... what I've seen so far is the one with: close, minimize and maximize. 

The one I'm talking about and would like to install has an extra button that make it look like a thin horizontal line on your screen ... is that the same one? I don't think that has anything to do with the terminal.

I think that's a window decoration. Don't know if that's possible to get with GTK and Metacity.

As you can see from the attached screenshots, that's how all application windows appear in Xubuntu's default theme. It has nothing to do with the terminal.

---

### Post by ugm6hr on 2009-08-04
> **aysiu said:**
> I think that's a window decoration. Don't know if that's possible to get with GTK and Metacity.

All Xfce 4 windows default with 4 buttons (1 for shrink into title bar) - unless you change themes.

Nothing to do with the terminal per se.

---

### Post by aysiu on 2009-08-04
Okay, here's the solution: ```
sudo apt-get update && sudo apt-get install xfwm4
``` Then ```
xfwm4 --replace &
``` If you want Metacity back: ```
metacity --replace &
```

---

### Post by jocampo on 2009-08-04
> **aysiu said:**
> Okay, here's the solution: ```
sudo apt-get update && sudo apt-get install xfwm4
``` Then ```
xfwm4 --replace &
``` If you want Metacity back: ```
metacity --replace &
```

It worked! You're the man! ;-) ... thanks...

Two questions ('cause I usually don't execute commands just for execute them) what 

```
xfwm4 --replace &
``` 

...does, replace my previous terminal emulator? 

and, I guess another forum member mentioned the 4 button layout has something to do with the theme, is that true as well?

Thanks again,

---

### Post by aysiu on 2009-08-04
No, it has nothing to do with the terminal. You should now have those four buttons on *every* window--the terminal window, the web browser window, the file manager window, etc.

It replaces your window manager (previously Metacity) with a new one (Xfwm4)--the window manager that Xubuntu uses by default.

---

### Post by jocampo on 2009-08-04
> **aysiu said:**
> No, it has nothing to do with the terminal. You should now have those four buttons on *every* window--the terminal window, the web browser window, the file manager window, etc.

It replaces your window manager (previously Metacity) with a new one (Xfwm4)--the window manager that Xubuntu uses by default.

Got it..

I thought everything was part of Gnome. Now I see Metacity is part of Gnome not Gnome itself.

---

