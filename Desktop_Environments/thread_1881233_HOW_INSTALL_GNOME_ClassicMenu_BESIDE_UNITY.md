---
title: "HOW INSTALL GNOME ClassicMenu BESIDE UNITY"
date: 2011-11-15
forum: Desktop Environments
---

### Post by MMALLOW on 2011-11-15
Hi

i use ubuntu 11.10 with unity

i want to install gnome classic menu with unity or beside unity

i mean together 

from terminal and ubuntu software center

thanks

---

### Post by MMALLOW on 2011-11-15
I'm  sorry for duplicated its my mistake 

thanks to you

i waiting your reply

---

### Post by stinkeye on 2011-11-15
[**_[COLOR="DarkRed"]http://www.florian-diesch.de/software/classicmenu-indicator/[/COLOR]_**]("http://www.florian-diesch.de/software/classicmenu-indicator/")

---

### Post by BillyBoa on 2011-11-15
You can try installing the Gnome Classic from the terminal:


```
sudo apt-get install gnome-session-fallback
```

Then you have to logout and select "GNOME Classic" from the login screen

---

### Post by MMALLOW on 2011-11-15
THANKS FOR ALL 

I HEARD ABOUT  Classic Menu Indicator  BUT MY FRIEND TOLD ME 

DON'T TRY IT ITS MAKE PROBLEM AND TAKE TO MUCH FROM RAM

I DO KNOW IF ITS RIGHT OR NOT

AND HE CONVINCE ME TO INSTALL GNOME Classic Menu

THIS BRIGITTE OR NOT

---

### Post by stinkeye on 2011-11-15
At the moment it's using 13mb of ram.
It seems to run without problems although I don't use it.
Just installed to test.
Try it for yourself and if it gives you problems, uninstall it.

---

### Post by Frogs Hair on 2011-11-15
> **MMALLOW said:**
> THANKS FOR ALL 

I HEARD ABOUT  [SIZE=2][B]Classic Menu Indicator  BUT MY FRIEND TOLD ME 

DON'T TRY IT ITS MAKE PROBLEM AND TAKE TO MUCH FROM RAM

I DO KNOW IF ITS RIGHT OR NOT

AND HE CONVINCE ME TO INSTALL GNOME [/B][/SIZE][SIZE=2][B]Classic Menu

THIS BRIGITTE OR NOT
[/B][/SIZE] [B]
[/B]

Make sure that application has been updated for 11.10 . It was made for Gnome 2 and may work , but I would not use it unless updated .

---

### Post by stinkeye on 2011-11-15
> **Frogs Hair said:**
> Make sure that application has been updated for 11.10 . It was made for Gnome 2 and may work , but I would not use it unless updated .
Well there is a deb package for 11.10 so I guess it's compatible with gnome3.
It's not gonna make your computer blow up anyway.
> ClassicMenu Indicator is a notification area applet (application indicator) for the top panel of **Ubuntu’s Unity desktop** environment
ClassicMenu Indicator is available from the PPA (“Personal Package Archive”) ppa:diesch/testing for Ubuntu 11.04 “Natty Narwhal” and **11.10 “Oneiric Ocelot”**.


---

### Post by MMALLOW on 2011-11-16
thanks 4 all
its my mistake 

i mean  i want unity + clasic menu in one screan on the same time

---

### Post by stinkeye on 2011-11-16
Install gnome-panel.
Put gnome-panel in startup applications using
**bash -c "sleep 5 && gnome-panel"** as the startup command.
log out/in.
Hold  down alt and drag the panel to the bottom with left mouse.

If you want to customize the panel use alt+ right mouse on the panel.
Only seems to work in metacity though so 
you would have to alt+f2 run **metacity --replace**, customize the panel 
then open a terminal and  run **compiz --replace &**.

---

### Post by MMALLOW on 2011-11-17
> **stinkeye said:**
> install gnome-panel.
Put gnome-panel in startup applications using
**bash -c "sleep 5 && gnome-panel"** as the startup command.
Log out/in.
Hold  down alt and drag the panel to the bottom with left mouse.

If you want to customize the panel use alt+ right mouse on the panel.
Only seems to work in metacity though so 
you would have to alt+f2 run **metacity --replace**, customize the panel 
then open a terminal and  run **compiz --replace &**.

thanks to you

---

