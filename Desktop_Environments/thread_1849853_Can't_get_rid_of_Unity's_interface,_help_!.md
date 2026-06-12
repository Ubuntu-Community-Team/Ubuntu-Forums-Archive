---
title: "Can't get rid of Unity's interface, help !"
date: 2011-09-25
forum: Desktop Environments
---

### Post by dielater on 2011-09-25
hello everyone !

It's been a while since i use ubuntu natty, but i dislike the new unity interface, so i want to go back to the old-fashionned gnome 2 graphical interface.

I tried several ways :
- disconnect my session to change the environnement at the login screen  :
        problem : i don't have anywhere the choice of the environnement ! only the time is displayed, and the "switch off" button
- power icon >> system settings >> login screen >> ubuntu classic >> then reboot
        problème : nothing changed after the reboot. i go back to settings and see that my choice have been saved to "ubuntu classic", although unity remains
- check if gnome-panel is installed, yes it is.

I don't know what to do, please help ! :)

Dielater

---

### Post by oldos2er on 2011-09-25
I believe you need to enter your user name first when logging in, then the Classic menu option should show up.

---

### Post by aschmidtm on 2011-09-25
Have you give Gnome 3 and shot?

---

### Post by dielater on 2011-09-25
> **aschmidtm said:**
> Have you give Gnome 3 and shot?

Gnome 2 is currently installed, not the 3. Do you think it comes from this ? Should i install gnome 3 ?

> **oldos2er said:**
> I believe you need to enter your user name  first when logging in, then the Classic menu option should show  up.

Already tried, no results..

---

### Post by MG&amp;TL on 2011-09-25
Installing gnome-shell makes no difference, AFAIK. Although it is good.

try this:[http://www.youtube.com/watch?v=YTtn4PPT1e8]("http://www.youtube.com/watch?v=YTtn4PPT1e8")

---

### Post by dielater on 2011-09-25
> **MG&TL said:**
> Installing gnome-shell makes no difference, AFAIK. Although it is good.

try this:[http://www.youtube.com/watch?v=YTtn4PPT1e8](http://www.youtube.com/watch?v=YTtn4PPT1e8)

Like i said in my first post, i already tried this, but it does'nt change anything.. That's weird..

---

### Post by MG&amp;TL on 2011-09-25
You sure you have gnome installed, and you haven't removed it by accident or something?

So there's definitely no switcher at the bottom when you press your username in GDM?

---

### Post by dielater on 2011-09-25
> **MG&TL said:**
> You sure you have gnome installed, and you haven't removed it by accident or something?

So there's definitely no switcher at the bottom when you press your username in GDM?

Yes i'm sure gnome is installed. when i try sudo apt-get install gnome-panel, it says the latest version is already installed.


Good i solved the problem ! 

For those who might need the solution :
1. Add gnome-panel to start up. power icon >> system settings >> preferences >> startup applications >> add (name : Gnome Panel, command : gnome-panel --replace )
2. Uninstall Unity : sudo apt-get autoremove unity
3. Reboot ! :)

---

### Post by Blasphemist on 2011-09-25
What session type options do you have at the bottom of the login screen? You do have to at least start to enter your password before the session type shows up. You should have classic and if you do, use it and take a screen shot (PrintScreen key) and post it here.

---

