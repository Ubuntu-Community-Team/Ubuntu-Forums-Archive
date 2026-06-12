---
title: "few questions"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Hairy_Palms on 2005-11-12
k ive got a few stupid questions that i knew the answers too before but now for the life of me i cant find

1. how do i stop nautilus looking crap when i run it with the sudo command?
is there any config file that i can copy from my other installation to make it look the same?

2. which program from synaptic provides the run dialog so that i can add it to the menu?

3. how do i make nautilus have an address bar instead of the annoying tabs thing?

---

### Post by Xian on 2005-11-12
[QUOTE=Hairy_Palms]k ive got a few stupid questions that i knew the answers too before but now for the life of me i cant find

1. how do i stop nautilus looking crap when i run it with the sudo command?
is there any config file that i can copy from my other installation to make it look the same?[/quote]

Run the theme manager as admin and set to preference.

```
$ sudo gnome-theme-manager
```

[QUOTE=Hairy_Palms]3. how do i make nautilus have an address bar instead of the annoying tabs thing?[/QUOTE]

From the main panel:

Applications > System Tools > Configuration Editor
A new window will appear. From there goto:

Apps > Nautilus > Preferences
Tick the box "Always Use Location Entry"

---

### Post by dcstar on 2005-11-12
[QUOTE=Hairy_Palms]k ive got a few stupid questions that i knew the answers too before but now for the life of me i cant find

1. how do i stop nautilus looking crap when i run it with the sudo command?
is there any config file that i can copy from my other installation to make it look the same?

2. which program from synaptic provides the run dialog so that i can add it to the menu?

3. how do i make nautilus have an address bar instead of the annoying tabs thing?[/QUOTE]
1/: gksudo "nautilus --browser %U"

2/: ? I assume you want to find out what binary to run when addping a package, look under "Installed files" for whatever is installed in the "bin" directory and try that filename.

3:/ Ctrl-L in Nautilus (Go-Location)

---

### Post by Hairy_Palms on 2005-11-12
question 1 didnt work, the theme
question 2 didnt work, i mean i want the run application dialog as it was in hoary in the menu
q3 worked both ways thx

---

### Post by Hairy_Palms on 2005-11-12
found the answer to question 2, the program is gmrun.

---

### Post by Trab on 2005-11-12
ummm if ur talking about the issues with ur theme being different when u use sudo vs when you use regular nautalius then what you need to do is change the theme for ur root.
the way to do this
```

sudo gnome-theme-manager

```
this will allow you to edit the theme that nautalius will use... so if u know how to set up ur theme then just do that.
or just copy the /home/$USER/.themes/ directory to /root/.themes/
latz
-Trab

---

### Post by Hairy_Palms on 2005-11-12
running sudo gnome-theme-manager doesnt affect the sudo nautilus.
and copying the themes over wont didnt do anything because i dont have any custom themes therefore the folder is empty.

---

### Post by Xian on 2005-11-12
[QUOTE=Hairy_Palms]running sudo gnome-theme-manager doesnt affect the sudo nautilus.[/quote]
It will when you apply a new theme.

[QUOTE=Hairy_Palms]and copying the themes over wont didnt do anything because i dont have any custom themes therefore the folder is empty.[/QUOTE]
The /usr/share/themes folder is empty?
If so just copy themes over from /home/~/.themes.

---

### Post by Hairy_Palms on 2005-11-12
it doesnt when i apply a new theme it does nothing
my /usr/share/themes are systemwide so copying them over wont do anything, and /usr/hairy/.themes is empty as i said before i did it before i reinstalled but that was a long time ago and i cant remember how.

---

### Post by Xian on 2005-11-12
[QUOTE=Hairy_Palms]it doesnt when i apply a new theme it does nothing[/QUOTE]
I would advise breaking it down. Instead of trying to apply an entire theme, click on the Theme Details button and change a combo of the Border and/or Controls. Perhaps that will alter the look of the application. That particular method works on my system.

---

### Post by Hairy_Palms on 2005-11-12
doesnt do anything, its so annoying because i know theres a way to do it because i did it before i reinstalled :(

---

### Post by Hairy_Palms on 2005-11-12
no matter what i change nautilus is exactly the same, heres the screenshot of normal nautilus and sudo nautilus
[http://i21.photobucket.com/albums/b264/Hairy_Palms/nautilus.jpg](http://i21.photobucket.com/albums/b264/Hairy_Palms/nautilus.jpg)

---

### Post by Hairy_Palms on 2005-11-12
FINALLY ive fixed it, thx for help guys, i went into the folder /root/.icons and replaced it with a symlink to /home/mike/.icons, and that did the trick.

---

