---
title: "cant change themes"
date: 2011-12-29
forum: Desktop Environments
---

### Post by aydinahmed on 2011-12-29
Ive tried everything. Trying to install Orta theme. Ive installed gnome tweak tool. It shows up in the windows theme options but not in gtk-theme option window. I've installed gtk-chtheme app and it shows up, I click apply and ok...nothing.I have gtk2.0. Installed libgtk2.0-dev. Tried creating a .theme folder in home folder and unzipping there. Nothing. Tried running nautilus, unzipping in /usr/share/themes. Nothing. Please help. I'm on the verge of throwing this laptop out of the window......

---

### Post by mcduck on 2011-12-29
Which version of Ubuntu are you using? If it's 11.10, you'll need a GTK3 theme, not a GTK2 theme.

(or actually you'll want a theme that includes both GTK3 and GTK2 themes, most of the stuff is already using GTK3 but having the same theme for any older application that's still using GTK2 is of course nice)

---

### Post by Frogs Hair on 2011-12-29
Orta is a Gnome 2 theme and won't work in 11.10 , which is Gnome 3 . There is only an Orta  Gnome Shell theme available .

---

### Post by aydinahmed on 2011-12-29
I ran a cmd line in terminal, cant remember what it was, Cause I wanted to see what gtk I had already, and I thought it said 2.0, I have 11.10 ocelot. When I tried to start orta theme it said I didnt have Gnome enabled?? How do I upgrade to 3.0? Also, I went to synptic package manager to get Gnome and installed it I think. LOL, 
Newbie, can you tell?

---

### Post by Frogs Hair on 2011-12-29
Orta will not work with 11.10 . The theme would have to be upgraded by the developer to work with your current operating system . 

You can find GTK 3 themes at the link . [http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=d4ad8a717bf5b68206eb16d6927d492a](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=d4ad8a717bf5b68206eb16d6927d492a)

---

### Post by mcduck on 2011-12-29
> **aydinahmed said:**
> I ran a cmd line in terminal, cant remember what it was, Cause I wanted to see what gtk I had already, and I thought it said 2.0, I have 11.10 ocelot. When I tried to start orta theme it said I didnt have Gnome enabled?? How do I upgrade to 3.0? Also, I went to synptic package manager to get Gnome and installed it I think. LOL, 
Newbie, can you tell?

You most likely have both GTK3 and GTK2 installed. But you still need a GTK3 theme for GTK3 applications and Gnome 3 itself, which is why Gnome-Tweak-Tool and any other up-to-date tool will only accept GTK3 themes.

..and if you are running 11.10, then there's nothing to upgrade, you are already using Gnome 3. Your theme is complaining because it's an old one and is made for Gnome 2.

(GTK3 and GTK2 aren't compatible, the theme format is completely different. So GTK3 applications will only use GTK3 theme, and GTK2 applications only use GTK2 theme. But if your theme includes both GTK3 and GTK2 themes, then simply setting the GTK3 theme should make any GTK2-based application to pick the related GTK2 theme automatically.)

---

### Post by aydinahmed on 2011-12-29
I hit ctl + h in my home folder to create .themes folder. I took the gtk 3.0 theme that I downloaded and extracted it in this folder. Closed folder. shouldn't the theme show up in tweaktool? It doesn't .That's where I'm getting frustrated. Following every tutorial. It's not hard,lolol.

---

### Post by Frogs Hair on 2011-12-29
Make sure you have GTK 3 theme and logout and in or restart if nothing shows up . I had to do this when I installed my first theme for some reason . If you write down what theme it is I can probably tell you if it works or not.

---

