---
title: "How to change gksudo background"
date: 2011-01-20
forum: Desktop Environments
---

### Post by Kognit on 2011-01-20
Hi

I am wondering if i can change the background or theme when i do gksudo or when i have to type a password, let's say in synaptics. Thx for answers

---

### Post by Kalimol on 2011-01-20
The background of the splash screen that comes up is just the tileable application background. If you change that, it affects every application. With that said, you can make it look a *little* cooler if you set it to transparent through Compiz - I have a rule for type=popupmenu | menu | dropdownmenu | tooltip | splash that's set to 90% opacity, but I'm not certain which part of that covers the box that comes up for gksudo.

I'm curious about whether or not that weird skin for applications that are running with elevated privileges can be changed, as well - that chunky Win95 look. So very ugly!

---

### Post by Krytarik on 2011-01-21
The "weird skin" thing happens, if you install themes into your home folder (the default way) instead of system-wide, in /usr/share/themes, because no one else can access those then, also not root, apparently.

About the Compiz setting, it's "splash", just yet tested it.

---

### Post by Kalimol on 2011-01-21
Oh, hey, cool. So if I copy my themes and icons into /user/share, that should fix it?

Thanks for making up for my laziness on checking the splash bit, by the way. = )

---

### Post by thilina on 2011-01-21
@Kalimol: Fixing the theme of root is a very simple thing. All you have to do is install Ubuntu tweak. For more info, visit this link. Regards...! 

[http://alldtechstuff.blogspot.com/2011/01/change-theme-of-root-user-easily-in.html](http://alldtechstuff.blogspot.com/2011/01/change-theme-of-root-user-easily-in.html)

---

### Post by Krytarik on 2011-01-21
> **Kalimol said:**
> Oh, hey, cool. So if I copy my themes and icons into /user/share, that should fix it?

Yes, but I would "chown" the files/dirs to root, and check the permissions. For all files 644 is sufficient, dirs must of course have 755.
To change it in a wash-up, if they are in a mess, as often, this command comes in handy, I only just recently learned it, run it in the dir of the theme:
```
find . -type f -exec sudo chmod 644 {} \;
```

The same applies to icon themes, system-wide dir is here of course /usr/share/icons .

---

### Post by Kognit on 2011-01-21
Thx for replies.

Ubuntu tweak and copying files to /usr only adapts gksudo to your theme. But i am wondering if i could change gksudo appearance anyway i want, regardless of theme. I have in mind background, size of gksudo box,...

---

### Post by JOHNNYG713 on 2011-01-21
When in gksudo nautilus click "Edit" open backgrounds and Emblems there you can change  the color or pattern in the window, by dragging a color or pattern in to the window this can also be done in standard nautilus !

---

### Post by Kognit on 2011-01-21
johnny,
i am not talking of Nautilus but of the pop up window which is asking for password. Instances when you install packages for Synaptic, when you run Nautilus in root mode, etc.

---

### Post by JOHNNYG713 on 2011-01-21
Oh! so you want the root theme to look like your default user theme and your root theme has that tan and blue KDE look?
 In terminal
```
sudo ln -s /home/USERNAME/.themes /root/.themes
``````
sudo ln -s /home/USERNAME/.icons /root/.icons

```Hope this helps!

---

### Post by Krytarik on 2011-01-22
> **JOHNNYG713 said:**
> Oh! so you want the root theme to look like your default user theme and your root theme has that tan and blue KDE look?
 In terminal
```
sudo ln -s /home/USERNAME/.themes /root/.themes
``````
sudo ln -s /home/USERNAME/.icons /root/.icons

```Hope this helps!
I wouldn't do this, because of different ownerships!

If I got it right, Kognit wants to tweak the outlook of just the password entry dialog for granting root permission, but not just the theme. That box follows the currently running theme, regardless if root can access those also or not, I've just yet checked it. But I don't think that there is a way to adjust its size or whatsoever.

---

### Post by Kognit on 2011-01-22
johnny,
no, i  don't want this. :)

I wan't to change this [http://members.home.nl/jeroen-91/ubuntu/breezy-new/gksudo.png]("http://members.home.nl/jeroen-91/ubuntu/breezy-new/gksudo.png")

Sorry for taking me so long to attach some picture :)

---

