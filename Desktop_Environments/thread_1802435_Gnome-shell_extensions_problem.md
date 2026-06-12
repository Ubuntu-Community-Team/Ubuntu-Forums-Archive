---
title: "Gnome-shell extensions problem"
date: 2011-07-11
forum: Desktop Environments
---

### Post by macozz on 2011-07-11
Hi all,
since a few days ago I experienced a change in Gnome-shell. Suddenly some of the extensions, like weather and Themes tab stop to load.
They are located at ~/.local/share/gnome-shell/extensions/ and it seems to my that gnome-shell is ignoring this folder.
Someone experienced something like that and, better, did fix it?

Cheers!

---

### Post by macozz on 2011-07-11
Also, the battery icon disappeared from the panel...


My system: Asus EeePC 1201N. 4Gb ram, 320Gb HD, Natty Narwall 64b, Gnome-shell 3.1.3

---

### Post by macozz on 2011-07-13
Another issue, the app icons in the bottom right show all the same icon, not the corresponding application icon. Some idea of what the reason???

Thank you!

---

### Post by cbowman57 on 2011-07-16
> **macozz said:**
> Another issue, the app icons in the bottom right show all the same icon, not the corresponding application icon. Some idea of what the reason???

Thank you!

Best guess, you're using Nvidia 275.09 drivers.  The shell doesn't seem to want to play nice with the latest driver. Better off to go back to 271.

---

### Post by cbowman57 on 2011-07-20
> **macozz said:**
> Hi all,
since a few days ago I experienced a change in Gnome-shell. Suddenly some of the extensions, like weather and Themes tab stop to load.
They are located at ~/.local/share/gnome-shell/extensions/ and it seems to my that gnome-shell is ignoring this folder.
Someone experienced something like that and, better, did fix it?

Cheers!

What's your current status?  When you look at errors in looking glass what does it show for your extensions?

---

### Post by macozz on 2011-07-20
> **cbowman57 said:**
> What's your current status?  When you look at errors in looking glass what does it show for your extensions?

Actually I did not look for errors (I guess I do not know how to use looking glass). 
Also, I did not found the 271 driver. 
Yesterday a new driver (275.19) was installed, but the problems remains the same.
Thaks a lot!

---

### Post by cbowman57 on 2011-07-20
> **macozz said:**
> Actually I did not look for errors (I guess I do not know how to use looking glass). 
Also, I did not found the 271 driver. 
Yesterday a new driver (275.19) was installed, but the problems remains the same.
Thaks a lot!

My mistake, should have been 270.41 driver. 275.19 & 280.04 have that same icon bug.

Looking Glass **Alt+f2** then enter **lg **click **Errors**. You can post a screenshot but you'll have to use the timer to get a shot of looking glass.

---

### Post by macozz on 2011-07-21
OK, the older driver restore the icons, but I still have no the theme extension and battery icon in the upper pannel.
Looking Glass list errors about incompatibilities of the related extension, however I get the last version of them and no .deb versions are available. Or are they?

Cheers

---

### Post by cbowman57 on 2011-07-21
Since I have no idea what shell version you're using, or how you got where you're at it's hard to advise you.  You are better off installing your extensions manually & avoiding the debs.

The lack of a battery icon in Ubuntu is a known bug right now.

---

### Post by macozz on 2011-07-21
Well, as it is said in the second post, I am on Gnome-Shell 3.1.3, it is from git20110718 right now.
I get the debs from the ricotz0 repository.
However, some of the extension were installed manualy after compilation from source. This mix used to work until a month or so, but now they seems to be incompatible, even if they are 3.3 too.
Thanks a lot.

---

### Post by threepwood960 on 2011-12-09
My battery icon is dissapeared from I installed gnome-shell. Please, do you know if a solution has already pusblished? Thanks.

---

