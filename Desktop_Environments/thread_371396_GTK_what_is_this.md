---
title: "GTK? what is this?"
date: 2007-02-26
forum: Desktop Environments
---

### Post by grogger13 on 2007-02-26
Ok i just got beryl working and have been working to make it look good.  I found a theme that i thought looked sleek and professional.
[http://www.gnome-look.org/content/show.php?content=48621](http://www.gnome-look.org/content/show.php?content=48621)

It says he has a defualt theme installed on the lastest gtk-engine, so i think i need that, but i'm not even sure what gtk-engine i have, i need some help getting the things i need to make beryl look as good as possible.  I really want to get rid of anything that is dull and gray, like the panels are right now.

---

### Post by Kateikyoushi on 2007-02-26
He is using the - GTK2 Theme: Clearlooks Cairo Glider theme.

---

### Post by grogger13 on 2007-02-26
yeah i know it says it right on the website.  Im not sure where to find it, his post makes me believe it is in a package that comes with GTK-engine2.6 and higher.

---

### Post by Kateikyoushi on 2007-02-26
Isn't it it in your themes ? System > Preferences > Theme. Which version of ubuntu do you use ?

---

### Post by shareMenaPeace on 2007-02-26
> **grogger13 said:**
> I really want to get rid of anything that is dull and gray, like the panels are right now.

You can also put tranparency on the panels, with rightclick ->properties -> background 
And did you checked out the emerald theme manager, as it provides many great thems as well.

---

### Post by grogger13 on 2007-02-27
i have ubuntu Edgy, but i do see a simple "Glider" theme and also a "Clearlooks" theme but not a "Clearlooks Cairo Glider".

** optional **: to activate the profile (fading windows, etc), import "blueglass-emerald.profile" using the beryl settings manager.
     
How do i import a profile.  i was searching all over the beryl settings manager

---

### Post by satchelpig on 2007-03-05
> **grogger13 said:**
> 

** optional **: to activate the profile (fading windows, etc), import "blueglass-emerald.profile" using the beryl settings manager.
     
How do i import a profile.  i was searching all over the beryl settings manager

I have the same question.  I imported this file (I think) but I then don't see anywhere in the manager that suggests anything has happened and/or that I can modify the theme in any way.  Anyone?

---

### Post by mcduck on 2007-03-06
GTK engine is the program that defines how the buttons and such look like, and then GTK themes tell the engine which colors to use and so on. Most GTK engines are available from apt-get/Synaptic, just search for 'gtk2-engine'.

So, to use a 'clearlooks' GTK theme you need the theme, and then you also need gtk2-engines-clearlooks'-package.

---

### Post by satchelpig on 2007-03-06
> **mcduck said:**
> GTK engine is the program that defines how the buttons and such look like, and then GTK themes tell the engine which colors to use and so on. Most GTK engines are available from apt-get/Synaptic, just search for 'gtk2-engine'.

So, to use a 'clearlooks' GTK theme you need the theme, and then you also need gtk2-engines-clearlooks'-package.

Sorry if I'm just being thickheaded, but I'm still confused.

(1) I went and installed all that GTK stuff . . . now where do I find it/use it/modify it?

(2) Still not sure what it has to do with the emerald profile I was trying to import . . . 

Thanks for any help . . .

---

### Post by ComplexNumber on 2007-03-06
> **satchelpig said:**
> Sorry if I'm just being thickheaded, but I'm still confused.

(1) I went and installed all that GTK stuff . . . now where do I find it/use it/modify it?

(2) Still not sure what it has to do with the emerald profile I was trying to import . . . 

Thanks for any help . . .
see screenshot. the emerald settings are not changed in beryl settings manager. they're changed in the emerald manager. install it if you don't have it. after that, when you right click on the beryl icon in the notification area(ie system tray), you will see the emerald manager there.

---

